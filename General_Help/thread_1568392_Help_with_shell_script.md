---
title: "Help with shell script"
date: 2010-09-05
forum: General Help
---

### Post by inameiname on 2010-09-05
I have a few scripts that I would like to make work for non-specific file and non-specific folder input. Basically, so I can put it inside my nautilus-scripts folder and be able to right click a file or folder and have it automatically feed into the script. Here is one of the scripts:

```

#!/bin/bash
tty -s; if [ $? -ne 0 ]; then gnome-terminal -e "$0"; exit; fi

PROGRAM_FOLDER="/home/me/Temp"
FILE="customizations_1.0_all"

cd "$PROGRAM_FOLDER/$FILE"
rm -fv -R "$PROGRAM_FOLDER/$FILE.deb"
find . -type f ! -regex '.*\.hg.*' ! -regex '.*?debian-binary.*' ! -regex '.*?DEBIAN.*' -printf '%P ' | xargs md5sum > DEBIAN/md5sums
cd "$PROGRAM_FOLDER"
dpkg-deb -b "$FILE"
rm -rf "$PROGRAM_FOLDER/$FILE"

```In other words, I'd love to be able to replace 'PROGRAM_FOLDER' with whatever directory the source is that I click on, and replace 'FILE' with whatever file the filename is so it'd work no matter what the source is called and where it is.

I've tried tweaking this, which was used in a script for converting ogv to avi that allowed for just what I'd like to do with the script above, but to no avail. Not even sure if I'm in the right vein as I'm semi-new to script creation.:

```

N=$#;
echo "Converting $N files !"
for ((i=0; i<=(N-1); i++))
do
echo "converting" $1
filename=${1%.*}

```

---

### Post by inameiname on 2010-09-05
Bump

---

### Post by VCoolio on 2010-09-05
Try that with $NAUTILUS_SCRIPT_SELECTED_URIS  check [here](https://help.ubuntu.com/community/NautilusScriptsHowto?highlight=%28%28NautilusScriptsHowto%29%29).

---

### Post by lloyd_b on 2010-09-05
It looks like you're on the right track.  Just need to address some details...

When you select "Open With" in Nautilus, Nautilus performs the command with the full path of the file/folder appended as the first command line parameter.  For example, if you have a script called "dosomething", and you use "Open With" to execute it on a file in "/home/myuser/somefile.dat", it produces the exact same results as if you typed "dosomething /home/myuser/somefile.dat" in a terminal window.

It appears you are aware of the $1 shell variable, which represents the first command line parameter.  What you need to do is parse that file name and path into two separate elements.  The simplest way to do this is with the 'basename' and 'dirname' commands:```
DIRNAME=`dirname $1`
FILENAME=`basename $1`
```(note that those are 'backtics' around the dirname and basename commands, not single quotes)

This works, but it's more efficient to use bash's internal string manipulation routines to accomplish the same thing.  I only mention dirname and basename because they are easier to understand.  Here's the same, with the bash string handling rather than dirname and basename:```
DIRNAME=${1%/*}
FILENAME=${1##*/}
```(to remove some probable confusion - the "%" strips away the *shortest* possible match for the pattern "/*" from the *right* of the string, which removes the last / character and everything after it.  The ## removes the *longest* possible match for the pattern "*/" from the *left* of the string, which removes everything up to and including the last / character.  I told you dirname and basename are simpler :))

Note that the above assumes you're clicking on a file name.  But what if you want to select a folder, and process all of the files in it?  For that, you need to check whether the command line parameter is a file or directory first.  Here's some more example code:```
#!/bin/bash
if [ -d $1 ]; then
    #It's a directory - change to it
    cd $1
    # loop through all the files in the directory, processing them
    for FILENAME in *; do
        somecommand $FILENAME
    done
else
    # It's a file
    DIRNAME=${1%/*}
    FILENAME=${1##*/}
    cd $DIRNAME
    somecommand $FILENAME
fi
```

One comment - you're first example script has a problem.  Specifically,```
cd "$PROGRAM_FOLDER/$FILE"
``` should fail every time, as you can't 'cd' into a file...

Lloyd B.

---

### Post by inameiname on 2010-09-05
Thank you both for your suggestions. 

So here's my understanding:

FULL_PATH=$1        = "/home/me/Temp/smplayer_0.6.10+svn20100830-1~0guiodic0_i386.deb"    = $@
DIRNAME=${1%/*}        = "/home/me/Temp"                            = `dirname $1`    
FILENAME=${1##*/}    = "smplayer_0.6.10+svn20100830-1~0guiodic0_i386.deb"            = `basename $1` 

Is this right, which removed everything to the right of the last '.', which is the file extension?

name=${1%.*} = "/home/me/Temp/smplayer_0.6.10+svn20100830-1~0guiodic0_i386"

And is this correct?:

NAME=${1##*/.*} = "smplayer_0.6.10+svn20100830-1~0guiodic0_i386"

Oh and I understand why you would say this would fail:

cd "$PROGRAM_FOLDER/$FILE"

But since I just made the following in the above script:

PROGRAM_FOLDER="/home/me/Temp"
FILE="customizations_1.0_all"

it works, seeing as how here, I put the wrong word, FILE, instead of FOLDER, which it is.

Finally, as for that script on checking for if the selected is a file or folder, do I just add that at the top of all the scripts? Would that hurt anything?

---

### Post by inameiname on 2010-09-05
Okay, so I've tweaked a script and it works by doing this in the terminal:

$ /Path/To/Script.sh /Path/to/File.deb

which is basically,

$ /home/(my username)/.gnome2/nautilus-scripts/Script.sh /home/(my username)/Temp/File.deb

however, right clicking the very same 'File.deb' and selecting the nautilus-script 'Script.sh' won't work, only a quick terminal popup which seems to read no such directory for everything. 

What am I doing wrong? Once again, the script itself works, other this this:

```

#!/bin/bash


tty -s; if [ $? -ne 0 ]; then gnome-terminal -e "$0"; exit; fi

name=${1%.*}
FULL_PATH=$1
FILENAME=${1##*/}

mkdir "$name"
cp -fv -R "$FULL_PATH" "$name/$FILENAME"
cd "$name"
ar vx "$FILENAME"
rm -fv -R "$FILENAME"
for file in *.tar.gz; do tar xvpf $file; done
for file in *.tar.lzma; do tar xvpf $file; done
rm -fv -R "control.tar.gz"
rm -fv -R "data.tar.gz"
rm -fv -R "data.tar.lzma"
rm -fv -R "debian-binary"
mkdir "$name/DEBIAN"
cp -fv -R "changelog" "$name/DEBIAN/changelog"
cp -fv -R "config" "$name/DEBIAN/config"
cp -fv -R "conffiles" "$name/DEBIAN/conffiles"
cp -fv -R "control" "$name/DEBIAN/control"
cp -fv -R "copyright" "$name/DEBIAN/copyright"
cp -fv -R "postinst" "$name/DEBIAN/postinst"
cp -fv -R "preinst" "$name/DEBIAN/preinst"
cp -fv -R "prerm" "$name/DEBIAN/prerm"
cp -fv -R "postrm" "$name/DEBIAN/postrm"
cp -fv -R "rules" "$name/DEBIAN/rules"
cp -fv -R "shlibs" "$name/DEBIAN/shlibs"
cp -fv -R "templates" "$name/DEBIAN/templates"
cp -fv -R "triggers" "$name/DEBIAN/triggers"
cp -fv -R ".svn" "$name/DEBIAN/.svn"
rm -fv -R "changelog"
rm -fv -R "config"
rm -fv -R "conffiles"
rm -fv -R "control"
rm -fv -R "copyright"
rm -fv -R "md5sums"
rm -fv -R "postinst"
rm -fv -R "preinst"
rm -fv -R "prerm"
rm -fv -R "postrm"
rm -fv -R "rules"
rm -fv -R "shlibs"
rm -fv -R "templates"
rm -fv -R "triggers"
rm -rfv ".svn"

```

---

### Post by inameiname on 2010-09-05
Bump

---

### Post by lloyd_b on 2010-09-05
I was making a false assumption - I assumed you were running the script via the "Open With" option, not via the Nautilus scripts.  The Nautilus scripts are designed to potentially pass multiple files/folders (since you can have multiple selected when you invoke the script), and so apparently don't use the $1 parameter.

Instead, they use some environment variables, which can potentially contain a list of selected items.  The specific one you'll probably want to trap is "NAUTILUS_SCRIPT_SELECTED_FILE_PATHS", which contains the full path and file/folder name for each item that is selected when the script is run.

Since this can contain more than one item, you'll want to loop through it, processing all of the selected items (you may or may not plan on doing this, but it's the safest way).

I recommend you get into the habit of using all uppercase names for variables - it makes them stand out (for example "name" might be a variable named "name", or a command named "name", while "NAME" is almost never going to be a command).  I also recommend using more descriptive variable names - right now, you understand that "name" is going to be a new directory created by the script, but 6 months from now it may not be so obvious.  "NEWDIRNAME" is a little more explanatory as to what you'll be using the variable for.
 
```
#!/bin/bash

# Set IFS so that is won't consider spaces as entry separators.  Without this, spaces in file/folder names can make the loop go wacky.
IFS=$'\n'

# See if the Nautilus environment variable is empty
if [ -z NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ]; then
    # If it's blank, set it equal to $1
    NAUTILUS_SCRIPT_SELECTED_FILE_PATHS=$1
fi

# Loop through the list (from either Nautilus or the command line)
for ARCHIVE_FULLPATH in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS; do
    NEWDIRNAME=${ARCHIVE_FULLPATH%.*)
    FILENAME=${ARCHIVE_FULLPATH##*/}

    mkdir "$NEWDIRNAME"
    cp -fv -R "$ARCHIVE_FULLPATH" "$NEWDIRNAME"
    cd "$NEWDIRNAME"
    ar vx "$FILENAME"
    rm -fv -R "$FILENAME"
    for FILE in *.tar.gz; do tar xvpf $FILE; done
    for FILE in *.tar.lzma; do tar xvpf $FILE; done
    rm -fv -R "control.tar.gz"
    rm -fv -R "data.tar.gz"
    rm -fv -R "data.tar.lzma"
    rm -fv -R "debian-binary"

    mkdir "DEBIAN"
  
    mv -fv "changelog" "DEBIAN"
    mv -fv "config" "DEBIAN"
    mv -fv "conffiles" "DEBIAN"
    mv -fv "control" "DEBIAN"
    mv -fv "copyright" "DEBIAN"
    mv -fv "postinst" "DEBIAN"
    mv -fv "preinst" "DEBIAN"
    mv -fv "prerm" "DEBIAN"
    mv -fv "postrm" "DEBIAN"
    mv -fv "rules" "DEBIAN"
    mv -fv "shlibs" "DEBIAN"
    mv -fv "templates" "DEBIAN"
    mv -fv "triggers" "DEBIAN"
    mv -fv ".svn" "DEBIAN"
 
    rm -fv -R "md5sums"
done
```

Okay, some notes.  

First off, the line ```
tty -s; if [ $? -ne 0 ]; then gnome-terminal -e "$0"; exit; fi
``` is creating a new terminal window, and then executing the command in it.  But the environment variable containing the file names is *not* passed to that new terminal.  I simply removed it, which results in the command running silently.  I'm not sure how to get those environment variables into a new terminal window, as for all practical purposes that new window is effectively a new login.  Maybe with the command-line options to gnome-terminal (I use XFCE, so I don't have gnome-terminal installed on my machine to look).

Second, you had a lot of lines that were referring to "$name/DEBIAN/...", but they were executed after you had cd'ed into "$name".  It's cleaner to use a relative path from the current directory (that you just cd'ed into).

Third - instead of doing a "cp -R" on a file, and then a "rm" on it, I used a "mv" (move) command that effectively does both at once.

Fourth, I put a section in to test whether the environment variable from Nautilus is empty or not - if it is, process the command line parameter ($1), otherwise process the environment variable.  That way you can test this in a terminal window.

Finally, when copying a file into a directory, it is not necessary to actually provide the destination file name.  If you just specify the destination directory, it will automatically be copied there using its current file name.  For example, "cp thisfile /home/otheruser" will copy "thisfile" to "/home/otheruser/thisfile"

Be advised - I have *not* tested the code.  Be sure to have backups of your files before trying it :)

Lloyd B.

---

### Post by inameiname on 2010-09-05
Wow....boy I have a lot to learn. :P Thank you so much. I'll get back with you on whether or not your improvements helped. Thanks again!

Oh, and that open in terminal line is just something I've found and used in several scripts. It's worked on all basic scripts I've made so figured it'd work here as well.

---

### Post by inameiname on 2010-09-05
So far, the script works just fine. Well, I had to switch a ")" to "]", but that was all. Line 14 just had this:

    NEWDIRNAME=${ARCHIVE_FULLPATH%.*)
and I made it this:
    NEWDIRNAME=${ARCHIVE_FULLPATH%.*}
No biggie.

Oddly enough, it works through nautilus-scripts context menu, but not if I just type this in a terminal windows:

./Script.sh '/home/(my username)/Temp/smplayer_0.6.10+svn20100830-1~0guiodic0_i386.deb'

I'm guessing the reason is because the script uses  NAUTILUS_SCRIPT_SELECTED_FILE_PATHS and is meant for use through the  scripts and that's all. No biggie. 

Anyway, I'm gonna see if I can tweak these new things I've learned from  you into my few other accompanying scripts. If you hadn't figured out,  this is merely a hacked way of extracting a deb file, and convert it's  contents into a ready to be updated one, and then another script  automatically repackages it (after I add or remove various things when  need be), and a final script installs it.

Again, I appreciate the work. Usually I can just piece things together here and there and throw out a script, but this one was giving me trouble. Especially as a novice to true script making.

Also, for later note and potential use, or non-use, what do you mean by "the environment variable containing the file names is *not* passed  to that new terminal." Like I said, it's never given me trouble before; I just want to make sure if it does, not to include it. Or to learn why not.

---

### Post by inameiname on 2010-09-05
So I've found your rendition of the script works wonderfully. Now, on to the other two that I need to tweak, a 'remaker' one, which puts the deb back to together again, doesn't seem to work. Here it is. It's really only just a few lines, with the top being what you've written:

```

#!/bin/bash

# Set IFS so that is won't consider spaces as entry separators.  Without this, spaces in file/folder names can make the loop go wacky.
IFS=$'\n'

# See if the Nautilus environment variable is empty
if [ -z NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ]; then
    # If it's blank, set it equal to $1
    NAUTILUS_SCRIPT_SELECTED_FILE_PATHS=$1
fi

# Loop through the list (from either Nautilus or the command line)
for ARCHIVE_FULLPATH in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS; do
    NEWDIRNAME=${ARCHIVE_FULLPATH%.*}
    FILENAME=${ARCHIVE_FULLPATH##*/}
    NAME=${ARCHIVE_FULLPATH##*/.*}

    cd "$NEWDIRNAME"
    rm -fv -R "$ARCHIVE_FULLPATH"
    find . -type f ! -regex '.*\.hg.*' ! -regex '.*?debian-binary.*' ! -regex '.*?DEBIAN.*' -printf '%P ' | xargs md5sum > DEBIAN/md5sums
    cd ..
    dpkg-deb -b "$NAME"
    rm -rf "$NAME"
done

```...and the other is just one line, to install the deb(s):

```

#!/bin/bash

# Set IFS so that is won't consider spaces as entry separators.  Without this, spaces in file/folder names can make the loop go wacky.
IFS=$'\n'

# See if the Nautilus environment variable is empty
if [ -z NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ]; then
    # If it's blank, set it equal to $1
    NAUTILUS_SCRIPT_SELECTED_FILE_PATHS=$1
fi

# Loop through the list (from either Nautilus or the command line)
for ARCHIVE_FULLPATH in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS; do
    NEWDIRNAME=${ARCHIVE_FULLPATH%.*}
    FILENAME=${ARCHIVE_FULLPATH##*/}
    NAME=${ARCHIVE_FULLPATH##*/.*}

    sudo dpkg -i "$ARCHIVE_FULLPATH"
done

```...obviously, the problem with the latter is the 'sudo' command. As now it's not being run in the terminal, I'm not sure how to make it pop up a terminal to insert my password to install. Technicall though, I have a solution for this (works just fine):

sudo gedit /etc/sudoers

...and add the following to '/etc/sudoers':

# To automate an update script in the nautilus-scripts folder without need of sudo
%(my username) ALL = NOPASSWD: /home/(my username)/.gnome2/nautilus-scripts/Deb-Installer.sh

---

### Post by lloyd_b on 2010-09-06
> **inameiname said:**
> So far, the script works just fine. Well, I had to switch a ")" to "]", but that was all. Line 14 just had this:

    NEWDIRNAME=${ARCHIVE_FULLPATH%.*)
and I made it this:
    NEWDIRNAME=${ARCHIVE_FULLPATH%.*}
No biggie.

Oddly enough, it works through nautilus-scripts context menu, but not if I just type this in a terminal windows:

./Script.sh '/home/(my username)/Temp/smplayer_0.6.10+svn20100830-1~0guiodic0_i386.deb'

I'm guessing the reason is because the script uses  NAUTILUS_SCRIPT_SELECTED_FILE_PATHS and is meant for use through the  scripts and that's all. No biggie.

The first is a classic typo on my part.

For the second  - another typo - change the line ```
if [ -z NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ]; then
```to```
if [ -z $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ]; then
``` and it should work.

Lloyd B.

---

### Post by inameiname on 2010-09-06
Oh cool, thanks. 

I've fixed the Deb-Remaker.sh script. All that was needed was to change:

dpkg-deb -b "$NAME" 
to
dpkg-deb -b "$NEWDIRNAME"
and
rm -rf "$NEWDIRNAME"
to
rm -rf "$NEWDIRNAME"
and it works now. 

So here are the two working scripts (if anybody else might ever need them), for any number of files selected, for Deb-Extracting and Deb-Remaking. I added an end line that textually tells you the job is finished:

Deb-Extractor.sh:

```

#!/bin/bash

# Set IFS so that it won't consider spaces as entry separators.  Without this, spaces in file/folder names can make the loop go wacky.
IFS=$'\n'

# See if the Nautilus environment variable is empty
if [ -z $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ]; then
    # If it's blank, set it equal to $1
    NAUTILUS_SCRIPT_SELECTED_FILE_PATHS=$1
fi

# Loop through the list (from either Nautilus or the command line)
for ARCHIVE_FULLPATH in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS; do
    NEWDIRNAME=${ARCHIVE_FULLPATH%.*}
    FILENAME=${ARCHIVE_FULLPATH##*/}
    NAME=${ARCHIVE_FULLPATH##*/.*}

    mkdir "$NEWDIRNAME"
    cp -fv -R "$ARCHIVE_FULLPATH" "$NEWDIRNAME"
    cd "$NEWDIRNAME"
    ar vx "$FILENAME"
    rm -fv -R "$FILENAME"
    for FILE in *.tar.gz; do tar xvpf $FILE; done
    for FILE in *.tar.lzma; do tar xvpf $FILE; done
    rm -fv -R "control.tar.gz"
    rm -fv -R "data.tar.gz"
    rm -fv -R "data.tar.lzma"
    rm -fv -R "debian-binary"

    mkdir "DEBIAN"

    mv -fv "changelog" "DEBIAN"
    mv -fv "config" "DEBIAN"
    mv -fv "conffiles" "DEBIAN"
    mv -fv "control" "DEBIAN"
    mv -fv "copyright" "DEBIAN"
    mv -fv "postinst" "DEBIAN"
    mv -fv "preinst" "DEBIAN"
    mv -fv "prerm" "DEBIAN"
    mv -fv "postrm" "DEBIAN"
    mv -fv "rules" "DEBIAN"
    mv -fv "shlibs" "DEBIAN"
    mv -fv "templates" "DEBIAN"
    mv -fv "triggers" "DEBIAN"
    mv -fv ".svn" "DEBIAN"

    rm -fv -R "md5sums"
    notify-send -t 5000 -i /usr/share/icons/gnome/32x32/status/info.png "Job Finished"
done

```Deb-Remaker.sh:

```

#!/bin/bash

# Set IFS so that it won't consider spaces as entry separators.  Without this, spaces in file/folder names can make the loop go wacky.
IFS=$'\n'

# See if the Nautilus environment variable is empty
if [ -z $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ]; then
    # If it's blank, set it equal to $1
    NAUTILUS_SCRIPT_SELECTED_FILE_PATHS=$1
fi

# Loop through the list (from either Nautilus or the command line)
for ARCHIVE_FULLPATH in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS; do
    NEWDIRNAME=${ARCHIVE_FULLPATH%.*}
    FILENAME=${ARCHIVE_FULLPATH##*/}
    NAME=${ARCHIVE_FULLPATH##*/.*}

    cd "$NEWDIRNAME"
    rm -fv -R "$ARCHIVE_FULLPATH"
    find . -type f ! -regex '.*\.hg.*' ! -regex '.*?debian-binary.*' ! -regex '.*?DEBIAN.*' -printf '%P ' | xargs md5sum > DEBIAN/md5sums
    cd ..
    dpkg-deb -b "$NEWDIRNAME"
    rm -rf "$NEWDIRNAME"
    notify-send -t 5000 -i /usr/share/icons/gnome/32x32/status/info.png "Job Finished"
done

```And finally, for that Deb-Installer.sh script, it still requires Sudo input, so have to do the solution I posed above. 

I'll mark this as solved. Hopefully no problems will arise.

---

### Post by inameiname on 2010-09-06
Unfortunately, for the Deb-Installer.sh script, I've had no luck using the:

```

sudo gedit /etc/sudoers
 ...and add the following to '/etc/sudoers':
 # To automate an update script in the nautilus-scripts folder without need of sudo
 %(my username) ALL = NOPASSWD: /home/(my username)/.gnome2/nautilus-scripts/Deb-Installer.sh

```Which is extremely weird, as I have other scripts inside my nautilus-scripts folder linked EXACTLY as this one that will run without the need to input a Sudo command. So I just don't understand. 

Is there some special restriction to automatically run a deb file? A working script I have runs "sudo apt-get update && sudo apt-get upgrade" without the need for entering my password, but "sudo dpkg -i whatever.deb" doesn't? I thought the sudoers file would force it to run.

---

### Post by lloyd_b on 2010-09-06
Where you need the sudo, try the 'gksudo' command instead.  It's a gui version of sudo, and should pop up a window prompting you for your password, if required (sudo keeps you "authorized" for a period of time after you enter a password (the default is 15 minutes).  So the *2nd* time you run a command it may or may not require you to enter the password).  

That's a safer method than specifically authorizing a script in sudoers.  It may or may not be an issue on your personal machine, but could be a potential security risk on a multi-user machine if the permissions on that script aren't properly set (for instance, if somebody can overwrite that script with their own, they could trick you into running their malicious script).

Lloyd B.

---

### Post by inameiname on 2010-09-06
I didn't know that about 'gksudo'. Interesting. 

Anyway, I would rather have it prompt for a password, so I will try that.

UPDATE:

I changed the
sudo dpkg -i "$ARCHIVE_FULLPATH"
to
gksudo dpkg -i "$ARCHIVE_FULLPATH"
and it does pop up a gui to insert my password, but then nothing, as if it fails. I tried opening through the terminal, and while it also pops up the gui for the password, it fails. It's read out is merely:

dpkg: need an action option
Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

Guess it doesn't like 'gksudo' or something, idk.

---

### Post by inameiname on 2010-09-06
This seems to work for it. Looks like I finally found a code to add to a script so it will ask for a password. hehe

```

SUDO="/usr/bin/sudo"

if [ -t 1 ]; then
  "$SUDO" "$@";
else
  gksudo -- "$SUDO" "$@";
fi

```Thus, my seemingly working Deb-Installer.sh script is this:

```

#!/bin/bash

SUDO="/usr/bin/sudo"

if [ -t 1 ]; then
"$SUDO" "$@";
else
gksudo -- "$SUDO" "$@";
fi

# Set IFS so that it won't consider spaces as entry separators.  Without this, spaces in file/folder names can make the loop go wacky.
IFS=$'\n'

# See if the Nautilus environment variable is empty
if [ -z $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ]; then
    # If it's blank, set it equal to $1
    NAUTILUS_SCRIPT_SELECTED_FILE_PATHS=$1
fi

# Loop through the list (from either Nautilus or the command line)
for ARCHIVE_FULLPATH in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS; do
    NEWDIRNAME=${ARCHIVE_FULLPATH%.*}
    FILENAME=${ARCHIVE_FULLPATH##*/}
    NAME=${ARCHIVE_FULLPATH##*/.*}

    sudo dpkg -i "$ARCHIVE_FULLPATH"
    notify-send -t 5000 -i /usr/share/icons/gnome/32x32/status/info.png "Job Finished"
done

```

---

