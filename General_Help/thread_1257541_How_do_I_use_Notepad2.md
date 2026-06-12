---
title: "How do I use Notepad2?"
date: 2009-09-03
forum: General Help
---

### Post by lsutiger on 2009-09-03
There is a little known windows program named Notepad2. I used this to open simple text files in 8.04, but can not get it to work in 9.04.

Any ideas?

---

### Post by mike555 on 2009-09-03
Why not use gedit , it's in your accessories menu.

---

### Post by Barafu Albino Cheetah on 2009-09-03
Idea: you go read about a proper way to post questions to forums. This would help, sure. 
Nobody would answer this way.

---

### Post by lsutiger on 2009-09-03
I currently do, but it shows all of the printer control codes, which is aggravating. Is there a way to disable that feature?

---

### Post by lsutiger on 2009-09-03
> **Barafu Albino Cheetah said:**
> Idea: you go read about a proper way to post questions to forums. This would help, sure. 
Nobody would answer this way.

People like you make these forums worse. I asked a simple question for those who are familiar with my problem.I do not expect an answer, just input from others. Ideas are what makes this world go round. If you do not have an answer or a constructive alternative to the question, please, oh please, just be quiet.

---

### Post by mc4man on 2009-09-04
Should be pretty straightfoward, I use hardy but just happened to have a 9.04 live cd running and it ran no problem.
It was a 64 bit live cd but that shouldn't matter,wine is 32 bit anyway.

Open winecfg and make sure the windows version is set to xp. (that's all I did and it ran.
Are you using the standard notepad2 or one of the mods?

If you get it going there is something simple you can do to make it easier to run, ect.

for the standard Notepad2.exe
This will make Notepad2 open with the simple command of notepad2, this way you can easily make a desktop launcher to open it with (or drag launcher to top or bottom panel ) plus have multiple ones if you want the modded versions

 ```
sudo cp /usr/bin/notepad /usr/local/bin/notepad2
```

Now take your [COLOR="Red"]N[/COLOR]otepad2.exe, rename it [COLOR="Red"]n[/COLOR]otepad2.exe and place in inside your windows folder in wine's drive_c (with all the other .exe's like regedit, notepad, ect.

To test open a terminal and run ```
notepad2
```

For a launcher command again just use notepad2

If you want other Notepad2 mods just do the same thing but up the number
notepad3.exe (command of notepad3), ect.

Note that I'm making the .exe lowercase so as to match the wrapper script
(notepad2.exe - notepad2

---

### Post by lsutiger on 2009-09-04
Thanx mc4man! That got it to open from CLI. What I am trying to do is have the file open by double clicking. I have tried setting the 'Open With' property to notepad2 and notepad2 %, but both of those only open a blank notepad.

Any ideas?

---

### Post by mc4man on 2009-09-04
I think you'll find it very hard or impossible to use a d. left click or r. click to get a file to open in notepad2.

Maybe search out some photoshop threads, I remember something similar, clicking on a image and having it open in photoshop (vs. just photoshop opening.

Any l. or r. click option would use a userapp.desktop which sets up with a EXEC=<command> %f

That works with linux apps but wine will path it wrong, at best here can produce an error popup generally like H:\ /home/doug/test.txt can't be found
The H could also be a Z depending on drive detection in winecfg.

From the command line to open a file in  notepad2 it would look like this (My Documents = home folder
```

 notepad2 C:\\windows\\profiles\\doug\\My Documents\\test.txt
```
So you can see the pathing issue
( but if you fool around who knows

If you set it up like previous post then drop the Notepad2.ini in the windows folder also, will save settings changes

---

### Post by Whiffle on 2009-09-04
Here is a script you might be able to use.  I use this all the time to open stuff in word.  With a little editing (The PROGRAM variable, really) it should work for you.  Then you can save it as an executable, and stick it somewhere (I use ~/.bin, and then add ~/.bin to my PATH variable, but I suppose you could put it in /usr/local/bin ).  Then you can call it from the command line.


```

#!/bin/sh
# Launch Microsoft Word either by itself or with the provided file name to open.
# Fully qualifies pathname of the Windows Application to launch
PROGRAM="C:\\Program Files\\Microsoft Office\\OFFICE11\\WINWORD.EXE"

# If launched with no parameters, just run the application and exit.
if [ $# = 0 ]; then
    wine "$PROGRAM"
    exit 0
fi

# Get the file to open and the directory where it resides.
FILE_NAME=`basename "$1"`
DIR_NAME=`dirname "$1"`

# Convert directory from relative to fully qualified path.
if [ `echo $DIR_NAME | cut -c 1` != "/" ]; then
    DIR_NAME=`pwd`/$DIR_NAME
fi

# Change to the directory, run winepath to see if the directory maps to a fake
# windows drive.  WINEPATH_ERRS is 1 if not and 0 if yes.
cd "$DIR_NAME"
winepath "$DIR_NAME" > /tmp/winepath.chk 2>&1
WINEPATH_ERRS=`cat /tmp/winepath.chk | grep "Warning" | wc -l`

# If we cannot edit the file, show error box and terminate.
if [ $WINEPATH_ERRS -gt 0 ]; then
    kdialog --title "WINE/Microsoft Office Error!" --error \
  "ERROR:
  Attempting to open a file using a Windows Application where the file is not in a location accessible by your current WINE configuration.  To open this file you must either:
  - Move the file ($1) to a valid location.
  - Ensure that ($DIR_NAME) is accessible to WINE.
  Fake Windows drives are configured as softlinks (ln -s) in the directory (~/.wine/dosdevices).  The current configuration of this directory is:
    $(ls -l ~/.wine/dosdevices | tr -s " " | cut -d " " -f 9-) "
    exit 1
fi

# Finally run the application.
wine "$PROGRAM" "$FILE_NAME"

```

---

### Post by SushiR on 2009-09-04
> **lsutiger said:**
> There is a little known windows program named Notepad2. I used this to open simple text files in 8.04, but can not get it to work in 9.04.

Any ideas?

Sorry if I may sound a bit harsh but... why the heck do you use a windows program to open text files? If you want some simple editor you may try leafpad...

---

### Post by lsutiger on 2009-09-04
Thanx for all of the replies!
To SushiR - I am looking for a program that keeps track of both line numbers and column positions.

Leafpad does not have an option in the menu. Is there an option on the command line or a config file to make that happen?

Thanx again!

---

### Post by mc4man on 2009-09-04
@ Whiffle

The script works great, just changed the line to reflect where the .exe is (left it in C:\\Windows\\

Then it's simple to  create a userapp.desktop where the EXEC= is the script by using a r. click 'open with'- 'Open with other application' - 'use a custom command' - browse to your script

Or go right click - properties - open with - use a custom command, ect.

The custom command is just the path to the script/scriptname. 

( I also use ~/bin

---

### Post by Vaphell on 2009-09-04
maybe you post your wishlist of features
i find it very unlikely that there is no good text editor in linux - after all linux people love to edit config files and stuff :)

---

### Post by rscricket on 2012-06-01
Thanks - I followed the instructions in this post. One thing I had to figure out was the .wine directory is hidden in my Home directory. I renamed Notepad2.exe to notepad2.exe in the Home/.wine/drive_c/windows directory.

But when I started notepad2, nothing happened. So I went to the terminal window and typed: wine notepad2. 
I got the error that - err:module:import_dll Library MSVCP60.dll
So I downloaded this dll and put it in the Home/.wine/drive_c/windows/system directory.

Then I created a terminal window shortcut and changed the command line to notepad2. notepad2 started fine but when I tried to save this file, it crashed. I got this error (again via terminal cmd: wine notepad2) - 
> fixme:commdlg:GetFileName95 Flags 0x02000000 not yet implemented

To fix, I found this link: [http://bugs.winehq.org/show_bug.cgi?id=28939](http://bugs.winehq.org/show_bug.cgi?id=28939).
This told me that Notepad2 version 4.0.23 worked without issues. So I downloaded it, changed name to notepad2.exe, moved to Home/.wine/drive_c/windows directory.

Now notepad2 works fine.

Just thought this may help others trying this or any other .exe apps.

- rsc

---

