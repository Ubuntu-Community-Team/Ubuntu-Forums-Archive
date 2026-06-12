---
title: "Can't open file folders"
date: 2010-07-15
forum: General Help
---

### Post by guywithbadusername on 2010-07-15
This is my first time posting, and I'm hoping this is in the right forum.  I can't get any of my file folders to open.  Nothing is showing on my desktop, my folders won't open, my trash won't open, and nothing happens when I right click on my desktop screen.  Also, nautilus doesn't open, and while that may be related, I don't know what to do about it.

Everything was fine yesterday morning, and it had for some reason stopped working by the time I got home last night.

Thanks for any help!

---

### Post by Zorgoth on 2010-07-15
The problem is definitely that nautilus doesn't open; those are all actions performed by nautilus.  How are you trying to open nautilus?  Have you tried running it from a terminal, and if so, what errors did it give?

---

### Post by javierrivera on 2010-07-15
Try to log into the guest account (using the menu that appears when you click on the power button icon).

If nautilus works in the guest account, it's a problem with your profile, we can work on it afterwards.

If it doesn't it's some other kind of problem.

---

### Post by Zorgoth on 2010-07-15
If you don't have a guest account, you can create a new account or enable the guest account using "Users and Groups" in System > Administration from the top panel.

---

### Post by The Cog on 2010-07-15
If the GUI has completely frozen, you can try switching to a console and restarting the X server from there:
Press **Ctrl-Alt-F1** to get a tty console. Log in and then use the command:
**sudo restart gdm**

---

### Post by guywithbadusername on 2010-07-15
I have tried opening nautilus by typing it in after hitting Alt+F2, which didn't do anything except stall my computer for a few seconds (really old computer), and I tried the following in terminal:

desktop:~$ nautilus

(nautilus:3157): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:3157): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:3157): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:3157): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Segmentation fault

I tried signing in to a guest account, but that doesn't seem to be any better.  :(

What is a GUI, and what does "restart gdm" do?

---

### Post by The Cog on 2010-07-15
A GUI is a Graphical User Interface - it's the bit that gives you windows instead of a white-on-black text screen.

Segmentation fault is bad. It's a crash that shouldn't happen.At this stage, I would suggest Ctrl-Alt-F1 followed by Ctrl-Alt-Delete to reboot the machine.

---

### Post by guywithbadusername on 2010-07-15
Tried rebooting; still have the same problem.  Also tried reinstalling nautilus, but that didn't seem to do anything either.

---

### Post by AlphaLexman on 2010-07-15
Post the output of:
```
nautilus --check
```
from a terminal.

---

### Post by guywithbadusername on 2010-07-15
desktop:~$ nautilus --check

(nautilus:1638): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory
running nautilus_self_check_file
running nautilus_self_check_icon_container
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory
running nautilus_self_check_file
running nautilus_self_check_icon_container

---

### Post by guywithbadusername on 2010-07-15
Oops!  Didn't know 8 ) made a smiley face.  Is there a good way to turn those off?

---

### Post by AlphaLexman on 2010-07-15
> **guywithbadusername said:**
> Oops!  Didn't know 8 ) made a smiley face.  Is there a good way to turn those off?
The above should be a new thread.

My system gives the same first line failure also. (But my nautilus works). Sorry, dead end.

---

### Post by psycho5 on 2010-07-15
Do you remember what was the last thing you did before this started happening? Maybe a file copy or something was abruptly ended, or you say your computer is quite old, maybe something to do with your partition or disk? Bad sectors?

---

### Post by guywithbadusername on 2010-07-16
It could possibly have something to do with my computer, but I don't know.  How would I check this?  I installed 9.10 a few months ago, and it's worked fine until now.  Nobody did anything significant with the computer the day it started doing this, as far as I know.

I can still access my files from individual applications (for example, I can open a LaTeX file using gedit), but my desktop and other file folders have disappeared and won' open.

Is there something I can do other than reinstalling nautilus using the Synaptic Package Manager (which I've already tried)?

Thanks for all your suggestions, guys; I do appreciate it.

---

### Post by javierrivera on 2010-07-19
> Is there something I can do other than reinstalling nautilus using the Synaptic Package Manager (which I've already tried)?

Have you installed some nautilus extensions?. If you did, can you uninstall them?

---

### Post by etdsbastar on 2010-07-19
Post the output of 

$ sudo nautilus --check

or 

$ sudo nautilus -c

and then try to open nautilus by typing -

$ sudo nautilus

---

