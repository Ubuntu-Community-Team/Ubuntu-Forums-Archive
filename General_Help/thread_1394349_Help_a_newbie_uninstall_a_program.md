---
title: "Help a newbie uninstall a program"
date: 2010-01-30
forum: General Help
---

### Post by Exp HP on 2010-01-30
Hey, I recently installed Ubuntu 9.10 on my Windows 7 laptop, and I'm having some difficulty with a program.

Following sort of a tradition, after installing my first program (a hex editor that I had to configure, compile (make) and install), the very first *game* I installed was an old favorite of mine called _DROD: Architect's Edition_ (the newer DRODs are available for Linux, but I wanted to start small this time).  This one came in the form of a .run file.  IIRC, I installed it using the command[B]
sudo sh ./DRODAESetup-1.6.7.run[/B]
and I selected the "Separate data for each user" option in the GUI installer window that came up. I'm now regretting that option, and I want to reinstall it using universal data because I'm having trouble running the program in its current state.  By the way, I also kept the default install (usr/local/games/drod-ae) and symbolic link (usr/local/bin) paths.

My trouble is twofold; for starters, every time I run it from the console, the console outputs the line
** Warning: Couldn't get memory information, assuming it's ok.**
before continuing to the program. Despite this warning, data is retained between successive runs of the program, *but all user-specific data (settings and progress) is indeed lost if I restart the computer.*
The other problem is that it will only work if I run it as root (via **sudo drod-ae**); if I don't run it as root, it outputs the above memory information warning and then returns without running the program.  For this reason, the item in the Applications menu doesn't do anything.


So I want to uninstall and do a clean reinstall of the program.  But I'm having trouble uninstalling it.
[SIZE=3] [SIZE=2]Can you help guide me through the process?[/SIZE][/SIZE]

Here's a dir listing of the install folder /usr/local/games/drod-ae,
```
mike@mike-lt-ub:/usr/local/games/drod-ae$** dir**
Caravel\ DROD\ Licensing\ Overview.txt    drod-ae      drodae.xpm  uninstall
Data                                      drod-ae.bin  Libs
```That one file named "uninstall" particularly caught my eye.  But I don't know how to use it!  Here's various things I tried:
```
mike@mike-lt-ub:/usr/local/games/drod-ae$** sudo make uninstall**
[sudo] password for mike: 
make: Nothing to be done for `uninstall'.
 mike@mike-lt-ub:/usr/local/games/drod-ae$** sudo sh uninstall**
Could not find a usable uninstall program. Aborting.
 mike@mike-lt-ub:/usr/local/games/drod-ae$** sudo sh ./uninstall**
Could not find a usable uninstall program. Aborting.
 mike@mike-lt-ub:/usr/local/games/drod-ae$** sudo make ./uninstall**
make: Nothing to be done for `uninstall'.
 mike@mike-lt-ub:/usr/local/games/drod-ae$** uninstall**
uninstall: command not found
 mike@mike-lt-ub:/usr/local/games/drod-ae$** ./uninstall**
Could not find a usable uninstall program. Aborting.
 mike@mike-lt-ub:/usr/local/games/drod-ae$** sudo ./uninstall**
Could not find a usable uninstall program. Aborting.
```I also, of course, tried double-clicking on the "uninstall" file in Nautilus and telling it to Run.

Help?

(I doubt this is necessary, but if you want to examine the program yourself, it is available on the [Caravel Games Download Page]("http://forum.caravelgames.com/downloads.php").)

---

### Post by Exp HP on 2010-01-30
I hate to be impatient, but...

BUMP

---

### Post by Barriehie on 2010-01-30
To uninstall it you're going to need a list of all the files/folders and symlinks that it created.  When you installed it did it echo anything to the terminal in regards to what it was doing???  Did it create an install.log anywhere???

Barrie

---

### Post by Exp HP on 2010-01-30
My first post does have a list of items in /usr/local/games/drod-ae that was generated from the **dir** command, so look at that.
It also created these files, *as far as I can tell*.

**/home/mike//home/mike/.caravel/drod-1_6/DataPath.txt**
Contents:
```
/usr/local/games/drod-ae/Data;/usr/local/games/drod-ae/Data;
```**/usr/local/bin/drod-ae**
This is an executable text file.
Contents:
```
#!/bin/sh

DRODAE_HOME="/usr/local/games/drod-ae"

if test "x$LD_LIBRARY_PATH" = "x"; then
    LD_LIBRARY_PATH="$DRODAE_HOME/Libs"
else
    LD_LIBRARY_PATH="$DRODAE_HOME/Libs:$LD_LIBRARY_PATH"
fi

DROD_1_6_RES_PATH="$DRODAE_HOME/Data"
DROD_1_6_DAT_PATH="$DRODAE_HOME/Data"

export LD_LIBRARY_PATH DROD_1_6_RES_PATH DROD_1_6_DAT_PATH

"$DRODAE_HOME/drod-ae.bin" "$@"
```And it added an item to the Main Menu in group "Other" with the following command:
```
/usr/local/games/drod-ae/drod-ae
```I have some pretty good ideas on what I should do, but I'm afraid to do it because I don't want to mess things up.

I'm not sure if I can access a log of all the files it created.  There is no install.log file. I've long since restarted the computer several times, so I don't know what was output to the console, and I don't want to run the installer a second time in fear of screwing things up or making it more difficult to remove.

There is a file named **uninstall** in the program's directory, and I assume that by using it I won't have to resort to manually deleting everything... but I can't for the life of me figure out how to use the file.

---

### Post by Barriehie on 2010-01-30
I think you can safely delete **/usr/local/games/drod-ae folder** and **/usr/local/bin/drod-ae file**.  If you don't plan on reinstalling it then you can also delete the **.file** in your home dir.  Removing the menu item is easy enough; System > Preferences > Main Menu

Barrie

Edit: If the installer was echoing out what it was doing, uncommon for windows based packages, you could reinstall it but redirect the output to a file and create an uninstall script from that.

Edit, Edit:  Post the uninstall file if you could please.

---

### Post by Exp HP on 2010-01-30
I cannot attach a file with no extension, so I'll copy and paste the contents of **/usr/local/games/drod-ae/uninstall**

```
#! /bin/sh
#### UNINSTALL SCRIPT - Generated by SetupDB 1.6 #####
DetectARCH()
{
        status=1
        case `uname -m` in
           amd64 | x86_64)  echo "amd64"
                  status=0;;
           i?86 | i86*)  echo "x86"
                  status=0;;
           90*/*)
           echo "hppa"
           status=0;;
        *)
        case `uname -s` in
            IRIX*)
            echo "mips"
            status=0;;
           AIX*)
           echo "ppc"
           status=0;;
            *)
            arch=`uname -p 2>/dev/null || uname -m`
                       if test "$arch" = powerpc; then
                          echo "ppc"
                       else
                          echo $arch
                       fi
            status=0;;
        esac
        esac
        return $status
}

DetectOS()
{
  os=`uname -s`
  if test "$os" = OpenUNIX; then
     echo SCO_SV
  else
     echo $os
  fi
  return 0
}

if which caravel-uninstall 2> /dev/null > /dev/null || type -p caravel-uninstall 2> /dev/null > /dev/null; then
    UNINSTALL=caravel-uninstall
else
    UNINSTALL="$HOME/.caravel/installed/bin/`DetectOS`/`DetectARCH`/uninstall"
    if test ! -x "$UNINSTALL" ; then
        echo Could not find a usable uninstall program. Aborting.
        exit 1
    fi
fi
"$UNINSTALL" -L drod-ae "/usr/local/games/drod-ae/.manifest/drod-ae.xml" "$1"
```It appears the "Could not find a usable uninstall program" message is from this file, so I guess the problem isn't that I can't get the file to run, but rather that I don't have a program that it needs to call!

---

### Post by Barriehie on 2010-01-30
Cool, there is a manifest file.  Now we need:
[color="red"]*/usr/local/games/drod-ae/.manifest/drod-ae.xml*[/color]
This should list everything that was installed where.  Since it's an XML file I'll probably have to gawk it to get the usable <sp> info from it, assuming it's in a format I'm expecting! :)

Barrie

---

### Post by Exp HP on 2010-01-30
Wow, that wasn't even in the dir list.  Huh, I didn't notice that before... krazzzy.:p

This one's large.  I'll just attach the whole .manifest folder in a tar archive (to my surprise, xml isn't allowed for attachments either).

The .manifest folder has two files in it: the **drod-ae.xml** file you wanted, as well as **scripts/p****reun.sh**.

---

### Post by Barriehie on 2010-01-30
> **Exp HP said:**
> Wow, that wasn't even in the dir list.  Huh, I didn't notice that before... krazzzy.:p

dot files are hidden unless using the -a option with ls. :)

---

### Post by Barriehie on 2010-01-30
K, everything listed in the .xml file is in the **/usr/local/games/drod-ae** folder.  There are 2 references to /root/.gnome2 folder and I would leave those alone.  I would say it's reasonably safe to remove the drod-ae folder in /usr/local/games .  There are 2 symlinks created that can be removed.  Remove the parts in red.
```

<symlink dest="/usr/local/games/drod-ae/drod-ae" mode="0777">[color="red"]/usr/local/bin/drod-ae[/color]</symlink>
<symlink dest="/usr/local/games/drod-ae/drod-ae" mode="0777">[color="red"]/bin/drod-ae[/color]</symlink>

```

Barrie

---

### Post by Exp HP on 2010-01-30
Thanks for the help!

The symbolic link link in /bin/ is something I would've missed if I went ahead and just deleted what I saw.  I'll look into how I can send console output to file so that I'll be more prepared next time I install something.;)

---

### Post by Barriehie on 2010-01-30
> **Exp HP said:**
> Thanks for the help!

The symbolic link link in /bin/ is something I would've missed if I went ahead and just deleted what I saw.  I'll look into how I can send console output to file so that I'll be more prepared next time I install something.;)

EASY!  You can redirect STDOUT and STDERR with pipes, is one way.

*script to run* 1>*SomePath/SomeFileName* 2>*SomePath/SomeFileName*

1 is STDOUT and 2 is STDERR

From the Advanced Bash Scripting Guide:
```

1>filename
# Redirect stdout to file "filename."
1>>filename
# Redirect and append stdout to file "filename."
2>filename
# Redirect stderr to file "filename."
2>>filename
# Redirect and append stderr to file "filename."
&>filename
# Redirect both stdout and stderr to file "filename."
#
#  Note that   &>>filename
#+ -- attempting to redirect and *append*
#+ stdout and stderr to file "filename" --
#+ fails with the error message,
#+ syntax error near unexpected token `>'.

```

and

```

2>&1
# Redirects stderr to stdout.
# Error messages get sent to same place as standard output.
#
i>&j
# Redirects file descriptor i to j.
# All output of file pointed to by i gets sent to file pointed to by j.
#
>&j
# Redirects, by default, file descriptor 1 (stdout) to j.
# All stdout gets sent to file pointed to by j.

```


HTH,
Barrie

---

