---
title: "How to change utc read only file in ubuntu 12.04"
date: 2012-06-18
forum: General Help
---

### Post by SUPERFITTER on 2012-06-18
[SIZE=2]How do I edit a [/SIZE][SIZE=2]read only file in[/SIZE][SIZE=2] ubuntu 12.04. [/SIZE][SIZE=2] 

I'm in file system, etc/default/rcS/# assume that the BIOS clock is set to UTC time (recommended) UTC=yes. 

I want to change it to UTC=no.  Because it changes time in Bios to UTC time and I want to keep it in local time, for windows XP.

[/SIZE]  [SIZE=2]Thank You[/SIZE]

---

### Post by MG&amp;TL on 2012-06-18
If you're the administrator on that machine, use gksu if you want to use a graphical app to edit it, or sudo if it's a CLI app. Like this:

```

gksu gedit /etc/default/rcS
sudo nano /etc/default/rcS
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by SUPERFITTER on 2012-06-18
Thank you for answering MG&TL.

I tried both but nothing worked, what am I doing incorrectly?

---

### Post by Mark Phelps on 2012-06-18
> **SUPERFITTER said:**
> Thank you for answering MG&TL.

I tried both but nothing worked, what am I doing incorrectly?

I can confirm, from first-hand experience, that what MG&TL told you is EXACTLY how to make that change.  It has worked for me every time.

Need to tell us more about what "nothing worked" means.

---

### Post by SUPERFITTER on 2012-06-18
[SIZE=4][COLOR=Blue]I got this:[/COLOR][/SIZE]
  GNU nano 2.2.6                                          File: /etc/default/rcS                                                                                  Modified  

#
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.

# delete files in /tmp during boot older than x days.
# '0' means always, -1 or 'infinite' disables the feature
TMPTIME=0

# spawn sulogin during boot, continue normal boot if not used in 30 seconds
SULOGIN=no

# do not allow users to log in until the boot has completed
DELAYLOGIN=no

# assume that the BIOS clock is set to UTC time (recommended
[SIZE=4][COLOR=Blue]UTC=yes[/COLOR][/SIZE][SIZE=4][COLOR=Blue]   [COLOR=Red]**** [/COLOR] I want to change this to UTC= no.[/COLOR][/SIZE][SIZE=4][COLOR=Blue][COLOR=Red]**** [/COLOR][/COLOR][/SIZE]

# be more verbose during the boot process
VERBOSE=no

# automatically repair filesystems with inconsistencies during boot
FSCKFIX=no

---

### Post by MG&amp;TL on 2012-06-18
> **SUPERFITTER said:**
> [SIZE=4][COLOR=Blue]I got this:[/COLOR][/SIZE]
  GNU nano 2.2.6                                          File: /etc/default/rcS                                                                                  Modified  

#
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.

# delete files in /tmp during boot older than x days.
# '0' means always, -1 or 'infinite' disables the feature
TMPTIME=0

# spawn sulogin during boot, continue normal boot if not used in 30 seconds
SULOGIN=no

# do not allow users to log in until the boot has completed
DELAYLOGIN=no

# assume that the BIOS clock is set to UTC time (recommended
[SIZE=4][COLOR=Blue]UTC=yes[/COLOR][/SIZE][SIZE=4][COLOR=Blue]   [COLOR=Red]**** [/COLOR] I want to change this to UTC= no.[/COLOR][/SIZE][SIZE=4][COLOR=Blue][COLOR=Red]**** [/COLOR][/COLOR][/SIZE]

# be more verbose during the boot process
VERBOSE=no

# automatically repair filesystems with inconsistencies during boot
FSCKFIX=no

Nano (CLI) and Gedit (GUI) are both simple editors, similiar to notepad. Just...edit it to say no.

---

### Post by SUPERFITTER on 2012-06-18
[SIZE=4]Nano (CLI) and Gedit (GUI) are both simple editors, similiar to notepad. Just...edit it to say no.

I cannot get it to edit out _yes_, so I can put in _no_. 

What am I doing wrong?[/SIZE]

---

### Post by MG&amp;TL on 2012-06-18
Use the default font size, if you wouldn't mind.

Okay, going with gedit, the GUI one:

1. Run:

```
gksu gedit /etc/default/rcS
```2. Enter your password

3. In the text editor that appears, position the cursor by clicking, or by the arrow keys, on end of the line UTC=yes

4. Press the Backspace key three times.

5. Type 'no'.

6. Press the Save button.

Sorry to be patronising, but I'm not really sure what the problem is. You ARE administrator on the machine, right? You can check in the Users and Groups program.

---

### Post by SUPERFITTER on 2012-06-18
Okay, going with gedit, the GUI one:

1. Run:

     Code:
     gksu gedit /etc/default/rcS 
2. Enter your password

3. In the text editor that appears, position the cursor by clicking, or by the arrow keys, on end of the line UTC=yes

4. Press the Backspace key three times.

5. Type 'no'.

6. Press the Save button.


I cannot find a save button, I got the yes deleted and no in it's place, but cannot save?  

Sorry for all the problems.

---

### Post by MG&amp;TL on 2012-06-18
Not a problem.

It's in the top toolbar, next to Open. It's got a picture of a hard disk on it, with an arros going down. If not, File->Save.

Hope that helps. :)

---

### Post by SUPERFITTER on 2012-06-18
When I save it and then go back to:

 [SIZE=2]file system, etc/default/rcS/# assume that the BIOS clock is set to UTC time (recommended) UTC=yes.

It still says yes, it looks like I'm doing something wrong, but I don't know what?
[/SIZE]

---

### Post by SUPERFITTER on 2012-06-18
I seem to have collected a bunch of these:
/etc/default/rcS.save.1
/etc/default/rcS.save.2
/etc/default/rcS.save.3
/etc/default/rcS.save.4
/etc/default/rcS.save.5
/etc/default/rcS.save.6
/etc/default/rcS.save.7
/etc/default/rcS.save.8
/etc/default/rcS.save.9

How do I delete these?:confused:

---

### Post by MG&amp;TL on 2012-06-19
Okay, since you're having trouble with an editor, I'll do a one-command solution, but normally you'd use an editor.

First, remove the save files:

```
cd /etc/default
sudo rm -i rcS.save.?
```make sure you type the rm command correctly, as that can be very destructive.

Let's edit the file:

```
cd /etc/default
sudo sed -i 's/UTC=yes/UTC=no/g' rcS
```

---

### Post by SUPERFITTER on 2012-06-19
Thank You very much for your patience MG&TL. I have it working now, and its great.:D

---

### Post by MG&amp;TL on 2012-06-19
> **SUPERFITTER said:**
> Thank You very much for your patience MG&TL. I have it working now, and its great.:D

Awesome! Glad you got it working, make sure you have fun with Ubuntu. :)

You might want to spend some time getting used to a text-editor of choice, as that is how most configuration files are done. Just a thought.

---

