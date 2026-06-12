---
title: "hide folders or files without adding period &quot;.&quot; to rename file or folder"
date: 2011-06-18
forum: General Help
---

### Post by ellaivarios on 2011-06-18
Hi everyone,

I am trying to hide some folders in Ubuntu Linux which are always hidden in Windows through File/Folder Attributes (attrib -h)

It is not an option for me to rename the folder from let's say "Ancient texts directory" to ".Ancient Texts Directory" because the programs associated with these files and shortcuts will not work in Windows. I would like to make the folder hidden by not renaming the folder. Is that so hard to ask?

Is there really no other way of making a folder or a file hidden in Linux just like in Windows by Applying Attributes? I Don't want to rename it by putting a dot in front of it. Moreover renaming a file by putting a dot in front of the name changes the position the folder appears in the list view. For some people this may be ridiculous, but for me with a few hundred files and folders and subfolders, this organisation is important, aside from the aforementioned reasons.

I need to maintain compatibility between the two operating systems' basic folder structure as i must use both Operating systems.

Any ideas?

thank you

---

### Post by PGScooter on 2011-06-18
> **ellaivarios said:**
> Hi everyone,

I am trying to hide some folders in Ubuntu Linux which are always hidden in Windows through File/Folder Attributes (attrib -h)

It is not an option for me to rename the folder from let's say "Ancient texts directory" to ".Ancient Texts Directory" because the programs associated with these files and shortcuts will not work in Windows. I would like to make the folder hidden by not renaming the folder. Is that so hard to ask?

Is there really no other way of making a folder or a file hidden in Linux just like in Windows by Applying Attributes? I Don't want to rename it by putting a dot in front of it. Moreover renaming a file by putting a dot in front of the name changes the position the folder appears in the list view. For some people this may be ridiculous, but for me with a few hundred files and folders and subfolders, this organisation is important, aside from the aforementioned reasons.

I need to maintain compatibility between the two operating systems' basic folder structure as i must use both Operating systems.

Any ideas?

thank you

Hi ellaivarios,

If I understand you correctly, you can do this:
create a file in the folder in which you want to hide a given file. Call that file .hidden. In .hidden just put the name of the file that you want to hide. When you view that folder with nautilus, it will not show the hidden files (you might have to refresh once you add the .hidden file).
Does that make sense? Is that what you want?

---

### Post by ellaivarios on 2011-06-19
> **PGScooter said:**
> Hi ellaivarios,

If I understand you correctly, you can do this:
create a file in the folder in which you want to hide a given file. Call that file .hidden. In .hidden just put the name of the file that you want to hide. When you view that folder with nautilus, it will not show the hidden files (you might have to refresh once you add the .hidden file).
Does that make sense? Is that what you want?

[B]Yes Thank you so much! This is fantastic! At long last it works and there is a solution, I was becoming so desperate! I will mark this as solved.

Basically, one need only make a file called:
 .hidden

Then open this file i.e. with Gedit and in there just list the name of the files or folders that you need to be hidden.

Switch view of hidden files and folders by pressing "<Ctrl>+H"
[/B]

So fantastic Thank you so infinitely.

You know Ubuntu should come with an extensive User manual with all possible commands, features and most forum-posted solutions and FAQ. It would solve numerous problems.

Thank you.

---

### Post by inameiname on 2011-06-20
Neat. I was not aware this was possible either. Thanks for the reply.

---

### Post by dFlyer on 2011-06-20
Please mark the thread SOLVED.

---

### Post by silex89 on 2011-06-20
I've been using Ubuntu since 2005 and I didn't know that! lool, thanks a lot for the information :P


Regards

---

### Post by inameiname on 2011-06-20
FYI, for those of us who've never done this before, it took me a few minutes to figure out its not paths it wants, but just the filenames. Just something to remember. 

Regardless, thanks again for the tip, [PGScooter]("http://ubuntuforums.org/member.php?u=253148").

---

### Post by mdurham on 2011-06-20
Thanks PGScooter, we live and learn.

---

### Post by ellaivarios on 2011-06-20
> **inameiname said:**
> FYI, for those of us who've never done this before, it took me a few minutes to figure out its not paths it wants, but just the filenames. Just something to remember. 

Regardless, thanks again for the tip, ellaivarios.


Yes this works by adding only the file name or folder name in a simple list inside the file we named .hidden

and the file .hidden must be in the same directory as the folders or files that we want to hide.
___________________________________

this raises the question, however, that some of you Linux Gurus must answer: This .hidden file is a function of linux and essentially works much like the Windows Attributes for files, whereby a folder or file can be assigned an attribute as hidden, read-only, system file, backup file, etc. I wonder where we can find the documentation on what other files we can create to do similar things to files and folders, i.e.:

instead of just having .hidden can we also have .readonly for instance? And if we want a file to be both read-only and hidden must we have both files called .hidden and the supposed .readonly file or is there a way to combine this?

Sorry I know I closed the thread, but I think this is an important and interesting feature to think about and explore, as it assigns attributes to files without renaming them. if you cannot post because the thread is <SOLVED>, please, please please take the time to send me a Personal Message on this matter. Thank you.

---

### Post by inameiname on 2011-06-20
> 
Yes this works by adding only the file name or folder name in a simple list inside the file we named .hidden

and the file .hidden must be in the same directory as the folders or files that we want to hide.
___________________________________

this raises the question, however, that some of you Linux Gurus must  answer: This .hidden file is a function of linux and essentially works  much like the Windows Attributes for files, whereby a folder or file can  be assigned an attribute as hidden, read-only, system file, backup  file, etc. I wonder where we can find the documentation on what other  files we can create to do similar things to files and folders, i.e.:

instead of just having .hidden can we also have .readonly for instance?  And if we want a file to be both read-only and hidden must we have both  files called .hidden and the supposed .readonly file or is there a way  to combine this?

Sorry I know I closed the thread, but I think this is an important and  interesting feature to think about and explore, as it assigns attributes  to files without renaming them. if you cannot post because the thread  is <SOLVED>, please, please please take the time to send me a  Personal Message on this matter. Thank you.     
Indeed. And I would be curious if such a thing is possible for 'read only' files and whatnot. 

Another question for me also comes to mind: if its possible to have only one '.hidden' file, and use full paths instead of just filenames. That way, on a single '.hidden' file, you can 'hide' as many files/folders as you want in as many folders as you want. IDK, just something I think would be cool compared to putting several '.hidden' folders around town if you have much to 'hide'. Best for a lazy person. :P

Regardless, thread closed or not closed, its yours, and feel free to inquire all you want. Nothing is ever completely solved for those of us who seek more knowledge about something, especially knowledge outside or supportive of a particular question.

---

### Post by PGScooter on 2011-06-20
> **ellaivarios said:**
> [B]Yes Thank you so much! This is fantastic! At long last it works and there is a solution, I was becoming so desperate! I will mark this as solved.

Basically, one need only make a file called:
 .hidden

Then open this file i.e. with Gedit and in there just list the name of the files or folders that you need to be hidden.

Switch view of hidden files and folders by pressing "<Ctrl>+H"
[/B]

So fantastic Thank you so infinitely.

You know Ubuntu should come with an extensive User manual with all possible commands, features and most forum-posted solutions and FAQ. It would solve numerous problems.

Thank you.

I agree that documentation needs to be improved. Perhaps there should be "simple" and comprehensive manuals. If you are looking to get involved, maybe here is a good place to start: [http://ubuntu-manual.org/](http://ubuntu-manual.org/)

> **inameiname said:**
> FYI, for those of us who've never done this before, it took me a few minutes to figure out its not paths it wants, but just the filenames. Just something to remember. 

Regardless, thanks again for the tip, [PGScooter]("http://ubuntuforums.org/member.php?u=253148").
Yes, sorry for not being explicit about this.

> **ellaivarios said:**
> Yes this works by adding only the file name or folder name in a simple list inside the file we named .hidden

and the file .hidden must be in the same directory as the folders or files that we want to hide.
___________________________________

this raises the question, however, that some of you Linux Gurus must answer: This .hidden file is a function of linux and essentially works much like the Windows Attributes for files, whereby a folder or file can be assigned an attribute as hidden, read-only, system file, backup file, etc. I wonder where we can find the documentation on what other files we can create to do similar things to files and folders, i.e.:

instead of just having .hidden can we also have .readonly for instance? And if we want a file to be both read-only and hidden must we have both files called .hidden and the supposed .readonly file or is there a way to combine this?

Sorry I know I closed the thread, but I think this is an important and interesting feature to think about and explore, as it assigns attributes to files without renaming them. if you cannot post because the thread is <SOLVED>, please, please please take the time to send me a Personal Message on this matter. Thank you.
I don't think that this is a function of linux but rather of nautilus. For example, if you use a terminal the file is not hidden. I imagine if you use another file browser (dolphin, thunar), unless that file browser supports this feature, it will not necessarily hide the files also. a .readonly would be possible but only for actions carried out through nautilus. My guess is that most linux gurus would not support this as being hard-coded into linux and I would agree with that.

> **inameiname said:**
> Indeed. And I would be curious if such a thing is possible for 'read only' files and whatnot. 

Another question for me also comes to mind: if its possible to have only one '.hidden' file, and use full paths instead of just filenames. That way, on a single '.hidden' file, you can 'hide' as many files/folders as you want in as many folders as you want. IDK, just something I think would be cool compared to putting several '.hidden' folders around town if you have much to 'hide'. Best for a lazy person. :P

Regardless, thread closed or not closed, its yours, and feel free to inquire all you want. Nothing is ever completely solved for those of us who seek more knowledge about something, especially knowledge outside or supportive of a particular question.
inameiname, this seems like something that could be achieved through a "nautilus script". I don't think it would be too complicated. I've never written a nautilus script so I can't give you much guidance, but I think it would work something like this:
whenever you open a folder in nautilus, nautilus first parses your main .hidden file to see which files in the directory you are about to open should be hidden, it then takes that list of files and creates a .hidden file in that folder you're about to open and it puts those filenames in there (it should also check to make sure you're not unknowingly overwriting a .hidden file that already exists).

---

### Post by inameiname on 2011-06-20
> **PGScooter said:**
> 
inameiname, this seems like something that could be achieved through a "nautilus script". I don't think it would be too complicated. I've never written a nautilus script so I can't give you much guidance, but I think it would work something like this:
whenever you open a folder in nautilus, nautilus first parses your main .hidden file to see which files in the directory you are about to open should be hidden, it then takes that list of files and creates a .hidden file in that folder you're about to open and it puts those filenames in there (it should also check to make sure you're not unknowingly overwriting a .hidden file that already exists).

Perhaps. I've made several of those, so I'm sure I could figure out how to make a "nautilus-script" for it if I want. I was just curious if it was something built-in. Anyway, thanks for the tips on how to create it.

---

### Post by ellaivarios on 2011-06-20
> **inameiname said:**
> Perhaps. I've made several of those, so I'm sure I could figure out how to make a "nautilus-script" for it if I want. I was just curious if it was something built-in. Anyway, thanks for the tips on how to create it.

Perhaps you wouldn't be to troubled to share your Guru Linux knowledge on that nautilus script discussed above, and creating other kind of "attribute" files with the same method... us the lowly users of the oblivious, derelect, now bygone "Windows" kingdom would humbly appreciate such knowledge Oh Thy knowledgeable One. (LOL) [i'm not being sarcastic or anything -- i'm just being funny and asking politely - I just have to clarify, just in case)

And I also really like the idea of having to make one .hidden file with all the paths instead of the filenames and foldernames. i wonder if this could be loaded automatically through adding it permanently through list of files added permanently to memory upon booting up... in windows there's something similar for dlls and drivers...

any ideas?

---

### Post by inameiname on 2011-06-20
> **ellaivarios said:**
> Perhaps you wouldn't be to troubled to share your Guru Linux knowledge on that nautilus script discussed above, and creating other kind of "attribute" files with the same method... us the lowly users of the oblivious, derelect, now bygone "Windows" kingdom would humbly appreciate such knowledge Oh Thy knowledgeable One. (LOL) [i'm not being sarcastic or anything -- i'm just being funny and asking politely - I just have to clarify, just in case)

And I also really like the idea of having to make one .hidden file with all the paths instead of the filenames and foldernames. i wonder if this could be loaded automatically through adding it permanently through list of files added permanently to memory upon booting up... in windows there's something similar for dlls and drivers...

any ideas?

Oh, well I appreciate the confidence, and the courtesies. However, I've been thinking about this and its proving a bit more complicated than I was thinking, far more than the usual basic nautilus scripts I've done to date. But I am curious myself, so I'll look more into it. At the very least, get an idea on the process. I'm good with that sort of thing.

In the meantime, check this out. I remember this article a little while back about really hiding folders in Ubuntu. Its for Maverick only, I'm afraid, but its another way to hide folders and such without adding a period to them. 

[http://www.webupd8.org/2011/01/how-to-really-hide-folders-in-ubuntu.html](http://www.webupd8.org/2011/01/how-to-really-hide-folders-in-ubuntu.html)

---

### Post by inameiname on 2011-06-21
I think the only way to use a single ".hidden" file and have it do what desired would be to put that ability within Nautilus itself. Too much work there. Therefore, I made this. Just read the script to see what it does. It will make things much easier, I think.

```

#!/bin/bash

# Hide-Unhide-In-Nautilus.sh
# Creator: Inameiname
# Date: 21 June 2011
# Version: 1.0
#
#
# This is a simple nautilus script to automatically add file(s)/folder(s)
# to a ".hidden" file so Nautilus will hide them, just like ".*" files
# Instructions:
# - decide what file(s)/folder(s) you want to hide inside a particular folder,
# - highlight them, and right click and select the script
# - it will automatically add the filenames to a created ".hidden" file inside the directory
# - if ".hidden" isn't there, it will add it
# - if you decide to unhide things, simply highlight and select the script again,
# - and it will automatically remove the filenames from the ".hidden" file
# - if ".hidden" contains no filenames, it will remove it
#
#
# Optionals:
# - Add the option to change the owner and group for whatever is selected to hide/unhide
# - Add the option to add the permissions for whatever is selected to hide/unhide
# - Add the option to make executable whatever is selected to hide/unhide
#
#
# Remember this only works inside the current directory/opened folder and files/folders inside that folder.
# Just comment out or uncomment whatever desired.
# Currently, only the ability to hide/unhide stuff is uncommented,
# but you can always just comment it out, and uncomment one of the "Make Executable" commands,
# and/or one of the "Change the owner and/or group of each file" commands,
# and/or one of the "Add permissions" commands, or mix and match whatever you want.
#
#
# For the changes to take effect to the file(s)/folder(s) you hid/unhid, you may have to refresh the folder, or even Nautilus



# Set IFS so that it won't consider spaces as entry separators.
# Without this, spaces in file/folder names can make the loop go wacky.
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

    # Hide/Unhide file(s)/folder(s) using ".hidden" file within the current folder
      # Copies all selected files/folders filenames to ".hidden"
        echo $FILENAME >> .hidden
      # Sorts and Checks ".hidden" for any duplicates
        sort .hidden | uniq -u > .hidden_temp
        rm .hidden
        mv .hidden_temp .hidden
      # Checks ".hidden" to see if there is anything there; if not, it removes it
        for file in .hidden
        do
          if [ `wc -l < $file` -eq 0 ]; then
             # file is empty
             rm $file
          fi
        done
    # Change the owner and/or group of each FILE to OWNER and/or GROUP, if desired
      # chown -R $USER:$USER $ARCHIVE_FULLPATH # set owner:group to current user
      # gnome-terminal -x sudo chown -R root:root $ARCHIVE_FULLPATH # set owner:group to root
      # gnome-terminal -x sudo chown -R $USER:$USER $ARCHIVE_FULLPATH # set owner:group to current user
    # Add permissions, if desired
      # chmod 444 $ARCHIVE_FULLPATH # read-only permissions for all
      # chmod 600 $ARCHIVE_FULLPATH # read/write for you, no permissions for rest
      # chmod 644 $ARCHIVE_FULLPATH # read/write for you, read-only permissions for rest (default)
      # sudo chmod 444 $ARCHIVE_FULLPATH # read-only permissions for all
      # sudo chmod 600 $ARCHIVE_FULLPATH # read/write for you, no permissions for rest
      # sudo chmod 644 $ARCHIVE_FULLPATH # read/write for you, read-only permissions for rest (default)
    # Make executable, if desired
      # chmod +x $ARCHIVE_FULLPATH
      # gnome-terminal -x sudo chmod +x $ARCHIVE_FULLPATH

done

# Add a notification when finished, if desired
    notify-send -t 2000 -i /usr/share/icons/gnome/32x32/status/info.png "Job Finished"

```

---

### Post by ellaivarios on 2011-06-21
WOW!. This looks amazing. It seems to work, but yesterday night Nautilus got Whacky on me and kept crashing.

Hmmm. maybe I've got something conflicting?

I'll check and get back to you.

That link is quite interesting by the way.
You've really opened my eyes on this! Thank you!

---

### Post by ellaivarios on 2011-06-21
That Gobohide look very interesting. I was not looking for stealth in terms of hiding folders or files. 

I find it extremely convenient to be able to hide and unhide files using <Ctrl>+H. But other people might need the stealth for certain files, and I'm sure myself just as everyone may have use for it at some point.

Ideally here's what the next Nautilus version needs to include:
a. An option in preferences/settings to be able to choose between hiding folders with one or the other method, or both (**with a dot** in front of the file name, and/or with a **.hidden** file *containing* the folder and *file paths* instead of the file or folder names that the user wishes to hide, and do so globally with one file for the entire system, OR automatically by placing the .hidden file in each respective folder each time a user chooses from a menu (i.e. right click "make hidden")
b. include the script **_inameiname_** wrote
c. include an option for Gobohide so that users are aware of this

[COLOR="DimGray"]Also it might be best to load Nautilus into a ramdisk by default when Linux starts. I find it's quite slow especially if i have large path depths and many files, contrary to Windows. And no I'm not willing to chance from Nautilus to something else, unless it is extremely superior.[/COLOR]

---

### Post by inameiname on 2011-06-21
> **ellaivarios said:**
> That Gobohide look very interesting. I was not looking for stealth in terms of hiding folders or files. 

I find it extremely convenient to be able to hide and unhide files using <Ctrl>+H. But other people might need the stealth for certain files, and I'm sure myself just as everyone may have use for it at some point.

Ideally here's what the next Nautilus version needs to include:
a. An option in preferences/settings to be able to choose between hiding folders with one or the other method, or both (**with a dot** in front of the file name, and/or with a **.hidden** file *containing* the folder and *file paths* instead of the file or folder names that the user wishes to hide, and do so globally with one file for the entire system, OR automatically by placing the .hidden file in each respective folder each time a user chooses from a menu (i.e. right click "make hidden")
b. include the script **_inameiname_** wrote
c. include an option for Gobohide so that users are aware of this

[COLOR=DimGray]Also it might be best to load Nautilus into a ramdisk by default when Linux starts. I find it's quite slow especially if i have large path depths and many files, contrary to Windows. And no I'm not willing to chance from Nautilus to something else, unless it is extremely superior.[/COLOR]

Thanks, glad it seems to work for ya. 

Your suggestions sound like some good ones. I wasn't aware <Ctrl>+H did anything. Or was that just something you want? If so, its possible my script could be linked to a shortcut key, such as that one, and voila, it'll do what you want. Easy peasy.

That Gobohide idea would be interesting, but from the little I know about it from what I read, it seems overly difficult to recreate over and over due to it being a kernel thing and has to be added permanently for it to keep working after every release. 

And I can see the advantage of having it run on ramdisk, but I guess it'd all depend on how much ram is on a system. And since Ubuntu is able to run on fairly old machines, I doubt that'll come around any time soon. No matter. I'm like you, and will stick with Nautilus. Although, Nautilus-Elementary's new creation, Marlin, is looking to have potential, and might be the next stage in file browser evolution.

Speaking of one ".hidden" file where full paths can be added, I have figured out a simple potential that could work. Unfortunately, it doesn't automatically add full file paths, but once you add whatever ones you want, it does the rest, including making all ".hidden" files in the appropriate folders, and throws the filenames that you want hid in the appropriate ones. Again, nothing special, as I'm not a highly skilled script-maker, but it works, so....

Personally, though, I prefer the first script, as you can simply right click and hide/unhide things. Super simple. What this new one does is it runs at startup if you set it that way and it auto-adds all you need where you need it.

```

#!/bin/bash

# Hide-Unhide-In-Nautilus-On-Startup.sh
# Creator: Inameiname
# Date: 21 June 2011
# Version: 1.0
#
#
# This is a simple nautilus script to automatically add file(s)/folder(s)
# to a ".hidden" file from a single preset ".hidden" file so Nautilus will hide them, just like ".*" files
# Instructions:
# - Put this in whatever folder you wish
# - Set it to run at startup by going to Main Menu -> System -> Preferences -> Startup Applications
# - Add a new startup program, like this: Name: Hide-Stuff-In-Nautilus; Command: /path/to/file/Hide-Unhide-In-Nautilus-On-Startup.sh
# - Input whatever user you want who can use this script
# - Input whatever file(s)/folder(s) you want below, between the parentheses
#
#
# This only works if you input the proper filenames and foldernames into this beforehand
# Once done, and linked as a startup program, it will run at startup, first deleting the older
# ".hidden" files on your system, and making ".hidden" files as per requsted on this script



# Add the correct user you want who can use this script
    USER_TO_HIDE_FILES=""

# Add the file(s)/folder(s) you want to hide here
    # ARCHIVE_FULLPATH1=""
    # ARCHIVE_FULLPATH2=""
    # ARCHIVE_FULLPATH3=""
    # ARCHIVE_FULLPATH4=""
    # ARCHIVE_FULLPATH5=""
    # ARCHIVE_FULLPATH6=""
    # ARCHIVE_FULLPATH7=""
    # ARCHIVE_FULLPATH8=""
    # ARCHIVE_FULLPATH9=""
    # ARCHIVE_FULLPATH10=""
    # ARCHIVE_FULLPATH11=""
    # ARCHIVE_FULLPATH12=""
    # ARCHIVE_FULLPATH13=""
    # ARCHIVE_FULLPATH14=""
    # ARCHIVE_FULLPATH15=""
    # ARCHIVE_FULLPATH16=""
    # ARCHIVE_FULLPATH17=""
    # ARCHIVE_FULLPATH18=""
    # ARCHIVE_FULLPATH19=""
    # ARCHIVE_FULLPATH20=""
    # ARCHIVE_FULLPATH21=""
    # ARCHIVE_FULLPATH22=""
    # ARCHIVE_FULLPATH23=""
    # ARCHIVE_FULLPATH24=""
    # ARCHIVE_FULLPATH25=""

# Various substitutions that are based on what is put above
# Unless you are hiding more than 25 files/folders, leave this section alone (other than uncommenting # of lines required)
    # DIRNAME1=`dirname "$ARCHIVE_FULLPATH1"`
    # DIRNAME2=`dirname "$ARCHIVE_FULLPATH2"`
    # DIRNAME3=`dirname "$ARCHIVE_FULLPATH3"`
    # DIRNAME4=`dirname "$ARCHIVE_FULLPATH4"`
    # DIRNAME5=`dirname "$ARCHIVE_FULLPATH5"`
    # DIRNAME6=`dirname "$ARCHIVE_FULLPATH6"`
    # DIRNAME7=`dirname "$ARCHIVE_FULLPATH7"`
    # DIRNAME8=`dirname "$ARCHIVE_FULLPATH8"`
    # DIRNAME9=`dirname "$ARCHIVE_FULLPATH9"`
    # DIRNAME10=`dirname "$ARCHIVE_FULLPATH10"`
    # DIRNAME11=`dirname "$ARCHIVE_FULLPATH11"`
    # DIRNAME12=`dirname "$ARCHIVE_FULLPATH12"`
    # DIRNAME13=`dirname "$ARCHIVE_FULLPATH13"`
    # DIRNAME14=`dirname "$ARCHIVE_FULLPATH14"`
    # DIRNAME15=`dirname "$ARCHIVE_FULLPATH15"`
    # DIRNAME16=`dirname "$ARCHIVE_FULLPATH16"`
    # DIRNAME17=`dirname "$ARCHIVE_FULLPATH17"`
    # DIRNAME18=`dirname "$ARCHIVE_FULLPATH18"`
    # DIRNAME19=`dirname "$ARCHIVE_FULLPATH19"`
    # DIRNAME20=`dirname "$ARCHIVE_FULLPATH20"`
    # DIRNAME21=`dirname "$ARCHIVE_FULLPATH21"`
    # DIRNAME22=`dirname "$ARCHIVE_FULLPATH22"`
    # DIRNAME23=`dirname "$ARCHIVE_FULLPATH23"`
    # DIRNAME24=`dirname "$ARCHIVE_FULLPATH24"`
    # DIRNAME25=`dirname "$ARCHIVE_FULLPATH25"`

    # FILENAME1=${ARCHIVE_FULLPATH1##*/}
    # FILENAME2=${ARCHIVE_FULLPATH2##*/}
    # FILENAME3=${ARCHIVE_FULLPATH3##*/}
    # FILENAME4=${ARCHIVE_FULLPATH4##*/}
    # FILENAME5=${ARCHIVE_FULLPATH5##*/}
    # FILENAME6=${ARCHIVE_FULLPATH6##*/}
    # FILENAME7=${ARCHIVE_FULLPATH7##*/}
    # FILENAME8=${ARCHIVE_FULLPATH8##*/}
    # FILENAME9=${ARCHIVE_FULLPATH9##*/}
    # FILENAME10=${ARCHIVE_FULLPATH10##*/}
    # FILENAME11=${ARCHIVE_FULLPATH11##*/}
    # FILENAME12=${ARCHIVE_FULLPATH12##*/}
    # FILENAME13=${ARCHIVE_FULLPATH13##*/}
    # FILENAME14=${ARCHIVE_FULLPATH14##*/}
    # FILENAME15=${ARCHIVE_FULLPATH15##*/}
    # FILENAME16=${ARCHIVE_FULLPATH16##*/}
    # FILENAME17=${ARCHIVE_FULLPATH17##*/}
    # FILENAME18=${ARCHIVE_FULLPATH18##*/}
    # FILENAME19=${ARCHIVE_FULLPATH19##*/}
    # FILENAME20=${ARCHIVE_FULLPATH20##*/}
    # FILENAME21=${ARCHIVE_FULLPATH21##*/}
    # FILENAME22=${ARCHIVE_FULLPATH22##*/}
    # FILENAME23=${ARCHIVE_FULLPATH23##*/}
    # FILENAME24=${ARCHIVE_FULLPATH24##*/}
    # FILENAME25=${ARCHIVE_FULLPATH25##*/}

# Upon startup, remove all ".hidden" files (that way you can start fresh after each restart, in case you've changed things on this script)
    cd $HOME
    find . -type f -name ".hidden" -exec rm -f {} \;

# Determine the correct user that has to be logged in for this script to run and hide files
if [ $USER = $USER_TO_HIDE_FILES ] ; then
    # Hide/Unhide file(s)/folder(s) using ".hidden" file within the current folder
    # Copies all selected files/folders filenames to ".hidden"
    # Unless you are hiding more than 25 files/folders,
    # leave this section alone (other than uncommenting lines)
      # echo $FILENAME1 >> "$DIRNAME1/.hidden"
      # echo $FILENAME2 >> "$DIRNAME2/.hidden"
      # echo $FILENAME3 >> "$DIRNAME3/.hidden"
      # echo $FILENAME4 >> "$DIRNAME4/.hidden"
      # echo $FILENAME5 >> "$DIRNAME5/.hidden"
      # echo $FILENAME6 >> "$DIRNAME6/.hidden"
      # echo $FILENAME7 >> "$DIRNAME7/.hidden"
      # echo $FILENAME8 >> "$DIRNAME8/.hidden"
      # echo $FILENAME9 >> "$DIRNAME9/.hidden"
      # echo $FILENAME10 >> "$DIRNAME10/.hidden"
      # echo $FILENAME11 >> "$DIRNAME11/.hidden"
      # echo $FILENAME12 >> "$DIRNAME12/.hidden"
      # echo $FILENAME13 >> "$DIRNAME13/.hidden"
      # echo $FILENAME14 >> "$DIRNAME14/.hidden"
      # echo $FILENAME15 >> "$DIRNAME15/.hidden"
      # echo $FILENAME16 >> "$DIRNAME16/.hidden"
      # echo $FILENAME17 >> "$DIRNAME17/.hidden"
      # echo $FILENAME18 >> "$DIRNAME18/.hidden"
      # echo $FILENAME19 >> "$DIRNAME19/.hidden"
      # echo $FILENAME20 >> "$DIRNAME20/.hidden"
      # echo $FILENAME21 >> "$DIRNAME21/.hidden"
      # echo $FILENAME22 >> "$DIRNAME22/.hidden"
      # echo $FILENAME23 >> "$DIRNAME23/.hidden"
      # echo $FILENAME24 >> "$DIRNAME24/.hidden"
      # echo $FILENAME25 >> "$DIRNAME25/.hidden"
fi

```

---

### Post by ellaivarios on 2011-06-21
In Reply to my original post,
so as to maintain compatibility of hidden files between Linux and Windows I have also found this,

[http://www.fs-driver.org/](http://www.fs-driver.org/)

 which some people may really appreciate; it is a Freeware driver that allows the EXT2 & Ext3 file system to be read by windows and of course to treat files with a dot prefix as hidden, among numerous other goodies:


[COLOR="Blue"]What features are supported?

Complete reading and writing access to files and directories of volumes with the Ext2 or Ext3 file system.
Supports features which are specific to the I/O-system of Windows: Byte Range Locks, Directory Notfication (so the Explorer updates the view of a directory on changes within that directory), Oplocks (so SMB clients are able to cache the content of files).
Allows Windows to run with paging files on Ext2 volumes.
UTF-8 encoded file names are supported.
**The driver treats files with file names that start with a dot "." character as hidden.**
Supports GPT disks if the Windows version used also does.
Supports use of the Windows mountvol utility to create or delete drive letters for Ext2 volumes (except on Windows NT 4.0). See also section "Can drive letters also be configured from scripts?".[/COLOR]

In effect, this thread has managed to solve the problem of having to rename with a dot prefix hidden files also used in Windows, which would make things a mess, with the solution of the .hidden file including the name AND the very convenient script by **inameiname**. And we've also found a way for windows to maintain linux hidden files as hidden, by using the above-mentioned freeware file system driver, and once again no deed to rename the files or alter their attributes.

This way both operating systems can maintain hidden files in their own turf, and the user has the option of maintaining or not these hidden files as hidden files when running the other operating system.

This got so much better than I expected!!! WOW.

---

### Post by ellaivarios on 2011-06-21
Yeah this second script looks interesting.

I might have something wrong with the field separator. nautilus crashes and it will not mount any of my disks anymore unless I restart.

I tried it on another machine running ubuntu and it works fine though, so I am not sure what the problem is on mine. Weird eh?

I'm not sure which of the two scripts I like more. I think I might have to let them grow on me first before I choose. But the whole idea is so convenient! no need to rename files with a dot prefix geez!! so much better. I mean haven't they thought of interchangeability between OSs? when they designed this dot thing for hidden files?

---

### Post by inameiname on 2011-06-21
Its what this community does; it often gives me more than I ever asked for or even wanted. 

I actually never had any urge to hide any files or folders, but after checking this thread out, I found the whole idea of the ".hidden" file fascinating enough to investigate further, and eventually attempt to better hone my scripting skills. Hehe

---

### Post by ellaivarios on 2011-06-21
I can create a link to a keyboard shortcut no problem for the script.

I mentioned <Ctrl>+H because in Nautiulus it can be used to show/hide hidden files from view and it works for both files that have the dot prefix appeneded and files that are hidden using our beloved method with the **.hidden** file. It's a nice little shortcut.

Hmm, I seem to have hit a little stumble with the script: when my disks are not mounted nautilus hangs or crashes/grays out, I think because the script calls for paths that are not present yet (??) If they are mounted beforehand it seems ok. hmmm

---

### Post by inameiname on 2011-06-21
> **ellaivarios said:**
> Yeah this second script looks interesting.

I might have something wrong with the field separator. nautilus crashes and it will not mount any of my disks anymore unless I restart.

I tried it on another machine running ubuntu and it works fine though, so I am not sure what the problem is on mine. Weird eh?

I'm not sure which of the two scripts I like more. I think I might have to let them grow on me first before I choose. But the whole idea is so convenient! no need to rename files with a dot prefix geez!! so much better. I mean haven't they thought of interchangeability between OSs? when they designed this dot thing for hidden files?

Hmmm, I don't know what your issue might be. Often, it turns out its a single little typing error added to the script that screws everything up. It took me a while to get the "" right because of errors and such. At least it works on one machines, so it might not be a script issue. That's something you can probably narrow down.

Well, have fun with both. I tend to hoard scripts from around town that I enjoy, and pick and match my favorite. Actually, the chown, executable, and chmod parts were actually combinations of several I already have as nautilus-actions for the same reason as you wanted, to be able to have a simple way to change files and folders.

On another note, I looked at that link you posted, and its a bit outdated. Why don't you check out this one:

[http://www.omgubuntu.co.uk/2011/06/access-ubuntu-from-windows-7/](http://www.omgubuntu.co.uk/2011/06/access-ubuntu-from-windows-7/)

It allows Windows users to peruse Ext4s too.

Also, if you are a true script lover, and find all of these little shortcuts handy, you should check out my Ultimate Bashrc file. It's sort of the culmination of all of my script work, and includes tons of scripts that I've made and found over the past few years, all inside a large '~.bashrc' file.

[http://gnome-look.org/content/show.php/Ultimate+Bashrc+File?content=129746](http://gnome-look.org/content/show.php/Ultimate+Bashrc+File?content=129746)

---

### Post by inameiname on 2011-06-21
> **ellaivarios said:**
> I can create a link to a keyboard shortcut no problem for the script.

I mentioned <Ctrl>+H because in Nautiulus it can be used to show/hide hidden files from view and it works for both files that have the dot prefix appeneded and files that are hidden using our beloved method with the **.hidden** file. It's a nice little shortcut.

Hmm, I seem to have hit a little stumble with the script: when my disks are not mounted nautilus hangs or crashes/grays out, I think because the script calls for paths that are not present yet (??) If they are mounted beforehand it seems ok. hmmm


Oh right! I forgot that. I have the habit of showing/hiding hidden files through the main menu instead of that shortcut; hence why I forgot it. 

Regarding the script, which one are you having trouble with? If its the latter, don't forget you have to add the full file paths to whatever files/folders you want to hide, as well as the $USER of your machine. I put that there for a reason, for those with several users on a machine would be the only ones who have access to hiding/showing certain files.

Also, if Nautilus is crashing, you can always refresh it by "nautilus -q".

---

### Post by ellaivarios on 2011-06-21
I'm also worried I might mess up my Kernel by trying to Add Gobohide. I found out it's dependent on GoboLinux... How do I go about this without messing up system? I love it the way it is right now...

---

### Post by inameiname on 2011-06-21
Oh don't mess with it. I only put the link up on this thread to show its another interesting idea that could be possible. However, the last time it seems it was updated with for the Maverick kernel, so if you tried to install it's precompiled kernel on Natty, it'll mess a lot of things up, I'm sure. I think what it is is it took the idea from the Gobolinux folks and what they adapted on their kernel, and recompiled it so it worked on Ubuntu. But only if you use that particular kernel.

So again, I wouldn't do it. Not worth all the trouble figuring out how to add that ability to hide folders on a later kernel.

---

### Post by ellaivarios on 2011-06-21
hmmm I'm also wondering if we could make use of adding an environment variable like the path for a main .hidden file that starts as soon as the machine stars i.e. 

sudo gedit /etc/environment

and adding the file/folder in there.

or in .profile maybe so that it is available for the entire session?
----------------------
Wow, I checked out your scripts and the such. GEEZ!
I feel impotent and in awe in front of your guru skills man. LOL Seriously. My puny Linux knowledge has lost its mojo.

---

### Post by ellaivarios on 2011-06-21
hmm, uhm what happens when the files or folders whose names had been inserted into the .hidden file are deleted by the user? The .hidden file ends up containing junk in its lists... Perhaps it might be wise to have the script also contain a search for confirmation of the files or folders in its list, and if they do not exist, to delete their respective entries from inside the .hidden file. The problem is WHEN will it search for this? as the script is initiated only by the user when the user wants to make the files or folder hidden, but then the user may delete these files or folders and not bother looking into the .hidden file. Once Again, I believe Microsoft has the upper hand here, just by assigning attributes to a file or folder, which is not quite the same as "permissions" in linux, but includes some of the permissions as attributes (such as readonly, etc)

The downside to this, even if you could get it to work, would be if you have someone with about 20,000 files in one single folder and they happen to want some of them deleted, the script would check all of them against the .hidden file's list, and it might slow down performance a little bit. (here's the use of the ramdisk for nautilus again LOL). Maybe allowing the script to tap into the system index would help?

---

### Post by ellaivarios on 2011-06-21
Oh, By the way this is for total Noobs: The script must be placed inside gnome2>nautiluscripts or something, and then also right click on it to make it executable by ticking in the relevant box. After that when you right click it will appear there and you can choose it.

I also like to remove the extension .sh from my scripts to make them look like a real menu option. No it does not matter. You can add the extension .grandother and it would still work this aint windows, and thank god for that.



@inameianame, I still can't get the second script to work on my laptop but works fine on the other machine. I'll look into it. I think I am go for the first script though. I love it.
You should make an mount/unmount script too LOL (for ISOs and the like), and maybe even load it into .desktop so it is part of the session and not just in Nautilus.

---

### Post by inameiname on 2011-06-21
> **ellaivarios said:**
> hmmm I'm also wondering if we could make use of adding an environment variable like the path for a main .hidden file that starts as soon as the machine stars i.e. 

sudo gedit /etc/environment

and adding the file/folder in there.

or in .profile maybe so that it is available for the entire session?
----------------------
Wow, I checked out your scripts and the such. GEEZ!
I feel impotent and in awe in front of your guru skills man. LOL Seriously. My puny Linux knowledge has lost its mojo.


I don't quite understand the added benefit of that versus just adding it to the startup applications as I mentioned. The "Hide-Unhide-In-Nautilus-On-Startup.sh" script is technically a main ".hidden" file. I just had to change the name so it wouldn't delete itself, as per what I wrote inside the script.

I'm also curious what you mean by it being available in the entire session. You mean if you decide to add/remove a file to hide within it, you would want it to work automatically instead of only on startup? 

It could theoretically be added to "bash.profile", or ".bashrc", which would allow it to run every time you use bash. 

Just remember you can only use the first or second script, not both at the same time, as the second one would end up deleting all the first one did at every startup its enabled.

If its the second one that is most desired, why not simply add files/folders to hide, and run it, and let it be? If want to add/remove stuff, simply tweak it, run it, and voila. One file to copy the necessary ".hidden" files where desired, as well as removing ones not listed in it. Simple. But again, I would prefer the ease of the first one.

---

### Post by inameiname on 2011-06-21
> **ellaivarios said:**
> hmm, uhm what happens when the files or folders whose names had been inserted into the .hidden file are deleted by the user? The .hidden file ends up containing junk in its lists... Perhaps it might be wise to have the script also contain a search for confirmation of the files or folders in its list, and if they do not exist, to delete their respective entries from inside the .hidden file. The problem is WHEN will it search for this? as the script is initiated only by the user when the user wants to make the files or folder hidden, but then the user may delete these files or folders and not bother looking into the .hidden file. Once Again, I believe Microsoft has the upper hand here, just by assigning attributes to a file or folder, which is not quite the same as "permissions" in linux, but includes some of the permissions as attributes (such as readonly, etc)

The downside to this, even if you could get it to work, would be if you have someone with about 20,000 files in one single folder and they happen to want some of them deleted, the script would check all of them against the .hidden file's list, and it might slow down performance a little bit. (here's the use of the ramdisk for nautilus again LOL). Maybe allowing the script to tap into the system index would help?


The first script automatically removes ".hidden" files if you run it with the same file again. It also sorts and such so there isn't any ".hidden" files that contain junk in them.

Now, as far as the second script, if somebody accidentally deletes ".hidden" files, all thats required is to run it again and all that is preset inside it will be thrown back into the appropriate ".hidden" files again.

I'm not sure what you are saying about a confirmation. As I said, with the first one it does that already. It checks to see if the filename is already inside a particular ".hidden" file, and if it isn't, it will add it; otherwise, it will accept that second one to mean you dont' want to hide it anymore, and will simply remove that filename altogether. 

Now, as far as the second script with this issue, again, it does remove all previous ".hidden" files, and will recreate only those on the most current list of the ones you've presetted in it. Therefore, it does essentially delete the respective entries to those hidden files you don't want hidden anymore.



UPDATE:

I think I get what you are saying now. You mean if the file/folder itself is removed, but the link to it inside either the particular ".hidden" file in the first script, or the link to it in the second script remains, that could become an issue. I don't know how to go about having it check it, at least for the first script. Now, it could be possible with the second script, as you can simply add a "if ...then... fi" statement for all presets listed. It'd no doubt make the script fairly long, though.

Regardless, this is definitely something Linux needs to work on; one thing Windows still has Linux beat.

And true, the more file/folders you have listed, like 20,000, the more it would have to search.

---

### Post by inameiname on 2011-06-21
> **ellaivarios said:**
> Oh, By the way this is for total Noobs: The script must be placed inside gnome2>nautiluscripts or something, and then also right click on it to make it executable by ticking in the relevant box. After that when you right click it will appear there and you can choose it.

I also like to remove the extension .sh from my scripts to make them look like a real menu option. No it does not matter. You can add the extension .grandother and it would still work this aint windows, and thank god for that.



@inameianame, I still can't get the second script to work on my laptop but works fine on the other machine. I'll look into it. I think I am go for the first script though. I love it.
You should make an mount/unmount script too LOL (for ISOs and the like), and maybe even load it into .desktop so it is part of the session and not just in Nautilus.


Indeed. Thanks for clarifying that for the Noobs out there.

Personally I prefer having the extensions (.sh, .pl, .py, .rb, etc.), and just make sure to add them. Helps when I have files of the same name, but different extensions. 

.............

That is strange. I'd have to be familiar with your laptop to figure out why the second script doesn't work on it. Good that first one works though. Like I said, its the best. I just threw the second together to more closely make one like that which we thought up in the beginning.

And I actually have a mount/unmount script made. Getting help from a couple people on here a year back, I was able to create a simple one that works well for me. It was mainly desired because Lucid (maybe it was Maverick), decided to remove the unmount option on the context menu in Nautilus, which used to be right next to Safely Remove. It also unmounts anything, not just discs, but flash drives, usb drives, whatever. Anyway, here is a link to the unmount.sh one I made:

[http://gnome-look.org/content/show.php/Unmount.sh?content=132354](http://gnome-look.org/content/show.php/Unmount.sh?content=132354)

Typically thats all I needed that was removed, but sometimes I use these, which I did not make:

---

### Post by inameiname on 2011-06-23
I fixed a couple quick things on that second script, so I'll put it here. The deleting all the ".hidden" files when started was off. Now it should work. Also added another script that will let you easily remove all the extra ".hidden" files wherever they may be. Nothing special, and mainly was created out of boredom, but here:

Hide-Unhide-In-Nautilus.sh
```

#!/bin/bash

# Hide-Unhide-In-Nautilus.sh
# Creator: Inameiname
# Date: 21 June 2011
# Version: 1.0
#
#
# This is a simple nautilus script to automatically add file(s)/folder(s)
# to a ".hidden" file so Nautilus will hide them, just like ".*" files
# Instructions:
# - decide what file(s)/folder(s) you want to hide inside a particular folder,
# - highlight them, and right click and select the script
# - it will automatically add the filenames to a created ".hidden" file inside the directory
# - if ".hidden" isn't there, it will add it
# - if you decide to unhide things, simply highlight and select the script again,
# - and it will automatically remove the filenames from the ".hidden" file
# - if ".hidden" contains no filenames, it will remove it
#
#
# Optionals:
# - Add the option to change the owner and group for whatever is selected to hide/unhide
# - Add the option to add the permissions for whatever is selected to hide/unhide
# - Add the option to make executable whatever is selected to hide/unhide
#
#
# Remember this only works inside the current directory/opened folder and files/folders inside that folder.
# Just comment out or uncomment whatever desired.
# Currently, only the ability to hide/unhide stuff is uncommented,
# but you can always just comment it out, and uncomment one of the "Make Executable" commands,
# and/or one of the "Change the owner and/or group of each file" commands,
# and/or one of the "Add permissions" commands, or mix and match whatever you want.
#
#
# For the changes to take effect to the file(s)/folder(s) you hid/unhid, you may have to refresh the folder, or even Nautilus



# Set IFS so that it won't consider spaces as entry separators.
# Without this, spaces in file/folder names can make the loop go wacky.
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

    # Hide/Unhide file(s)/folder(s) using ".hidden" file within the current folder
      # Copies all selected files/folders filenames to ".hidden"
        echo $FILENAME >> .hidden
      # Sorts and Checks ".hidden" for any duplicates
        sort .hidden | uniq -u > .hidden_temp
        rm .hidden
        mv .hidden_temp .hidden
      # Checks ".hidden" to see if there is anything there; if not, it removes it
        for file in .hidden
        do
          if [ `wc -l < $file` -eq 0 ]; then
             # file is empty
             rm $file
          fi
        done
    # Change the owner and/or group of each FILE to OWNER and/or GROUP, if desired
      # chown -R $USER:$USER $ARCHIVE_FULLPATH # set owner:group to current user
      # gnome-terminal -x sudo chown -R root:root $ARCHIVE_FULLPATH # set owner:group to root
      # gnome-terminal -x sudo chown -R $USER:$USER $ARCHIVE_FULLPATH # set owner:group to current user
    # Add permissions, if desired
      # chmod 444 $ARCHIVE_FULLPATH # read-only permissions for all
      # chmod 600 $ARCHIVE_FULLPATH # read/write for you, no permissions for rest
      # chmod 644 $ARCHIVE_FULLPATH # read/write for you, read-only permissions for rest (default)
      # sudo chmod 444 $ARCHIVE_FULLPATH # read-only permissions for all
      # sudo chmod 600 $ARCHIVE_FULLPATH # read/write for you, no permissions for rest
      # sudo chmod 644 $ARCHIVE_FULLPATH # read/write for you, read-only permissions for rest (default)
    # Make executable, if desired
      # chmod +x $ARCHIVE_FULLPATH
      # gnome-terminal -x sudo chmod +x $ARCHIVE_FULLPATH

done

# Add a notification when finished, if desired
    notify-send -t 2000 -i /usr/share/icons/gnome/32x32/status/info.png "Job Finished"

```Remove-All-.hidden-Files.sh
```

#!/bin/bash



# Remove-All-.hidden-Files.sh
# Creator: Inameiname
# Date: 22 June 2011
# Version: 1.0
#
#
# This is a simple nautilus script to automatically remove all ".hidden" files
# in your home directory, including those ".hidden" files created using
# "Hide-Unhide-In-Nautilus.sh"



if zenity --question --text "Are you sure you want to remove all of the ".hidden" files in your home directory?" ; then
    # If answer is "yes", then do this:
    # Upon startup, remove all ".hidden" files (that way you can start fresh after each restart, in case you've changed things on this script)
      cd $HOME
      find . -type f -name ".hidden" -exec rm -f {} \;

    # Add a notification when finished, if desired
      notify-send -t 4000 -i /usr/share/icons/gnome/32x32/status/info.png "All ".hidden" files have been removed"
else
    # If answer is "no", then do this:
    # Add a notification when finished, if desired
      notify-send -t 4000 -i /usr/share/icons/gnome/32x32/status/info.png "All ".hidden" files have NOT been removed"
fi

```.hide-unhide-in-nautilus-on-startup.sh
```

#!/bin/bash

# Hide-Unhide-In-Nautilus-On-Startup.sh
# Creator: Inameiname
# Date: 21 June 2011
# Version: 1.0
#
#
# This is a simple nautilus script to automatically add file(s)/folder(s)
# to a ".hidden" file from a single preset ".hidden" file so Nautilus will hide them, just like ".*" files
# Instructions:
# - Put this in whatever folder you wish
# - Set it to run at startup by going to Main Menu -> System -> Preferences -> Startup Applications
# - Add a new startup program, like this: Name: Hide-Stuff-In-Nautilus; Command: /path/to/file/Hide-Unhide-In-Nautilus-On-Startup.sh
# - Input whatever user you want who can use this script
# - Input whatever file(s)/folder(s) you want below, between the parentheses
#
#
# This only works if you input the proper filenames and foldernames into this beforehand
# Once done, and linked as a startup program, it will run at startup, first deleting the older
# ".hidden" files on your system, and making ".hidden" files as per requsted on this script



# Add the correct user you want who can use this script
    USER_TO_HIDE_FILES=""

# Add the file(s)/folder(s) you want to hide here
    # ARCHIVE_FULLPATH1=""
    # ARCHIVE_FULLPATH2=""
    # ARCHIVE_FULLPATH3=""
    # ARCHIVE_FULLPATH4=""
    # ARCHIVE_FULLPATH5=""
    # ARCHIVE_FULLPATH6=""
    # ARCHIVE_FULLPATH7=""
    # ARCHIVE_FULLPATH8=""
    # ARCHIVE_FULLPATH9=""
    # ARCHIVE_FULLPATH10=""
    # ARCHIVE_FULLPATH11=""
    # ARCHIVE_FULLPATH12=""
    # ARCHIVE_FULLPATH13=""
    # ARCHIVE_FULLPATH14=""
    # ARCHIVE_FULLPATH15=""
    # ARCHIVE_FULLPATH16=""
    # ARCHIVE_FULLPATH17=""
    # ARCHIVE_FULLPATH18=""
    # ARCHIVE_FULLPATH19=""
    # ARCHIVE_FULLPATH20=""
    # ARCHIVE_FULLPATH21=""
    # ARCHIVE_FULLPATH22=""
    # ARCHIVE_FULLPATH23=""
    # ARCHIVE_FULLPATH24=""
    # ARCHIVE_FULLPATH25=""

# Various substitutions that are based on what is put above
# Unless you are hiding more than 25 files/folders, leave this section alone (other than uncommenting # of lines required)
    # DIRNAME1=`dirname "$ARCHIVE_FULLPATH1"`
    # DIRNAME2=`dirname "$ARCHIVE_FULLPATH2"`
    # DIRNAME3=`dirname "$ARCHIVE_FULLPATH3"`
    # DIRNAME4=`dirname "$ARCHIVE_FULLPATH4"`
    # DIRNAME5=`dirname "$ARCHIVE_FULLPATH5"`
    # DIRNAME6=`dirname "$ARCHIVE_FULLPATH6"`
    # DIRNAME7=`dirname "$ARCHIVE_FULLPATH7"`
    # DIRNAME8=`dirname "$ARCHIVE_FULLPATH8"`
    # DIRNAME9=`dirname "$ARCHIVE_FULLPATH9"`
    # DIRNAME10=`dirname "$ARCHIVE_FULLPATH10"`
    # DIRNAME11=`dirname "$ARCHIVE_FULLPATH11"`
    # DIRNAME12=`dirname "$ARCHIVE_FULLPATH12"`
    # DIRNAME13=`dirname "$ARCHIVE_FULLPATH13"`
    # DIRNAME14=`dirname "$ARCHIVE_FULLPATH14"`
    # DIRNAME15=`dirname "$ARCHIVE_FULLPATH15"`
    # DIRNAME16=`dirname "$ARCHIVE_FULLPATH16"`
    # DIRNAME17=`dirname "$ARCHIVE_FULLPATH17"`
    # DIRNAME18=`dirname "$ARCHIVE_FULLPATH18"`
    # DIRNAME19=`dirname "$ARCHIVE_FULLPATH19"`
    # DIRNAME20=`dirname "$ARCHIVE_FULLPATH20"`
    # DIRNAME21=`dirname "$ARCHIVE_FULLPATH21"`
    # DIRNAME22=`dirname "$ARCHIVE_FULLPATH22"`
    # DIRNAME23=`dirname "$ARCHIVE_FULLPATH23"`
    # DIRNAME24=`dirname "$ARCHIVE_FULLPATH24"`
    # DIRNAME25=`dirname "$ARCHIVE_FULLPATH25"`

    # FILENAME1=${ARCHIVE_FULLPATH1##*/}
    # FILENAME2=${ARCHIVE_FULLPATH2##*/}
    # FILENAME3=${ARCHIVE_FULLPATH3##*/}
    # FILENAME4=${ARCHIVE_FULLPATH4##*/}
    # FILENAME5=${ARCHIVE_FULLPATH5##*/}
    # FILENAME6=${ARCHIVE_FULLPATH6##*/}
    # FILENAME7=${ARCHIVE_FULLPATH7##*/}
    # FILENAME8=${ARCHIVE_FULLPATH8##*/}
    # FILENAME9=${ARCHIVE_FULLPATH9##*/}
    # FILENAME10=${ARCHIVE_FULLPATH10##*/}
    # FILENAME11=${ARCHIVE_FULLPATH11##*/}
    # FILENAME12=${ARCHIVE_FULLPATH12##*/}
    # FILENAME13=${ARCHIVE_FULLPATH13##*/}
    # FILENAME14=${ARCHIVE_FULLPATH14##*/}
    # FILENAME15=${ARCHIVE_FULLPATH15##*/}
    # FILENAME16=${ARCHIVE_FULLPATH16##*/}
    # FILENAME17=${ARCHIVE_FULLPATH17##*/}
    # FILENAME18=${ARCHIVE_FULLPATH18##*/}
    # FILENAME19=${ARCHIVE_FULLPATH19##*/}
    # FILENAME20=${ARCHIVE_FULLPATH20##*/}
    # FILENAME21=${ARCHIVE_FULLPATH21##*/}
    # FILENAME22=${ARCHIVE_FULLPATH22##*/}
    # FILENAME23=${ARCHIVE_FULLPATH23##*/}
    # FILENAME24=${ARCHIVE_FULLPATH24##*/}
    # FILENAME25=${ARCHIVE_FULLPATH25##*/}

# Upon startup, remove all ".hidden" files (that way you can start fresh after each restart, in case you've changed things on this script)
    cd $HOME
    find . -type f -name ".hidden" -exec rm -f {} \;

# Determine the correct user that has to be logged in for this script to run and hide files
if [ $USER = $USER_TO_HIDE_FILES ] ; then
    # Hide/Unhide file(s)/folder(s) using ".hidden" file within the current folder
    # Copies all selected files/folders filenames to ".hidden"
    # Unless you are hiding more than 25 files/folders,
    # leave this section alone (other than uncommenting lines)
      # echo $FILENAME1 >> "$DIRNAME1/.hidden"
      # echo $FILENAME2 >> "$DIRNAME2/.hidden"
      # echo $FILENAME3 >> "$DIRNAME3/.hidden"
      # echo $FILENAME4 >> "$DIRNAME4/.hidden"
      # echo $FILENAME5 >> "$DIRNAME5/.hidden"
      # echo $FILENAME6 >> "$DIRNAME6/.hidden"
      # echo $FILENAME7 >> "$DIRNAME7/.hidden"
      # echo $FILENAME8 >> "$DIRNAME8/.hidden"
      # echo $FILENAME9 >> "$DIRNAME9/.hidden"
      # echo $FILENAME10 >> "$DIRNAME10/.hidden"
      # echo $FILENAME11 >> "$DIRNAME11/.hidden"
      # echo $FILENAME12 >> "$DIRNAME12/.hidden"
      # echo $FILENAME13 >> "$DIRNAME13/.hidden"
      # echo $FILENAME14 >> "$DIRNAME14/.hidden"
      # echo $FILENAME15 >> "$DIRNAME15/.hidden"
      # echo $FILENAME16 >> "$DIRNAME16/.hidden"
      # echo $FILENAME17 >> "$DIRNAME17/.hidden"
      # echo $FILENAME18 >> "$DIRNAME18/.hidden"
      # echo $FILENAME19 >> "$DIRNAME19/.hidden"
      # echo $FILENAME20 >> "$DIRNAME20/.hidden"
      # echo $FILENAME21 >> "$DIRNAME21/.hidden"
      # echo $FILENAME22 >> "$DIRNAME22/.hidden"
      # echo $FILENAME23 >> "$DIRNAME23/.hidden"
      # echo $FILENAME24 >> "$DIRNAME24/.hidden"
      # echo $FILENAME25 >> "$DIRNAME25/.hidden"
fi

```

---

### Post by mourt on 2011-06-30
> **ellaivarios said:**
> .... when they designed this dot thing for hidden files?

That feature has been present in UNIX shells long before Windows (or MSDOS for that matter) was invented.

---

### Post by ellaivarios on 2011-07-01
> **mourt said:**
> That feature has been present in UNIX shells long before Windows (or MSDOS for that matter) was invented.

Putting a dot to in front of files to rename them in order to hide them is the most retarded way of hiding files ever invented. Come on, we glorify Unix and Linux, but they have their idiotic shortcomings as well. Give it up, not everything is absolutely perfect about Linux, although it has numerous advantages compared to all OSs available at present. And who cares if the most idiotic way of hiding files and folders was invented before Windows came along? LOL The Windows attributes system for files and folders beats the Linux system hands down any time of the day man. Period.

---

### Post by WonderWoofy on 2012-04-06
Wow, with this revelation, I was forced to finally register.

That is so incredibly easy, yet also unbelievably not obvious.  Although now that I know it is not something easily forgotten either.  Thank you so much!!! :p

---

