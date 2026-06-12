---
title: "Trying to download CodeBlocks, and other problems"
date: 2010-08-16
forum: General Help
---

### Post by Tyler5794 on 2010-08-16
I'm going to attempt to learn C/C++, so I decided to install CodeBlocks from [http://www.codeblocks.org/downloads/26#linux64](http://www.codeblocks.org/downloads/26#linux64). Once it was downloaded, I got the message "tmp/codeblocks-10.05-1-debian-amd64.tar.bz2 could not be opened, because the associated helper application does not exist. Change the association in your preferences." Um, yeah, dunno what to do here. :/

I don't think I have all the necessary drivers/software installed because when I attempted to install them, I got an error message.

I've got Windows 7 dual booted with Xubuntu version 10.0.4 (the newest version I think) on my laptop, it's got 400-something GBs, and it's 64 bit.

Also, a few random scattered problems:

When I'm on Youtube watching a video, I can't click on the video to pause it, or click on any of the buttons (pause/play, volume, window size). This might have something to do with my drivers/software/whatever problem, since I don't have all of them installed, but I was able to install Flash Player.
**This appears to be working now,, I don't know if it was just a random problem that won't happen again or what, I thought originally it had something to do with the drivers. Dunno, but if anyone knows anything about that happening often, that'd be appreciated.**

Sometimes (often) when I'm typing, the mouse will randomly fly across the screen, I think this is because the mousepad on my laptop is too sensitive; however, I don't know how to change the sensitivity of my mousepad on here.
Sometimes when it does this, it'll post random information if I'm in a text area, for example, it'll post a name of a file I was attempting to download, or the URL of another tab or something. I have no idea why it does this. The mouse gestures from Opera come to mind, I was thinking maybe that coupled with the mousepad being too sensitive could do that? I dunno.

Help would be reeeeaalllyy appreciated.

---

### Post by john newbuntu on 2010-08-17
Running "sudo apt-get install codeblocks" in a terminal should install codeblocks in Ubuntu 10.4.

Prior to running this, I'd also suggest that you install the build-essential package, although I am not sure if it will be installed as a part of the codeblocks package. No harm though, it gives you the ability to do C/C++ builds that in turn could be used by codeblocks:
"sudo apt-get install build-essential"

The correction of the youtube video problem might be because of a flash plugin update.

---

### Post by Tyler5794 on 2010-08-17
Okay, I installed codeblocks well, but build-essential crashed when I installed it. I don't know why, it didn't give me anything other than telling me to send an error report. Also, I don't know where to find codeblocks, it's not on my desktop or anything, is there somewhere specific I should look for things I just downloaded with terminal?'

---

### Post by john newbuntu on 2010-08-17
Open a terminal and type "codeblocks" without the quotes and it should open up the GUI.  On the GNOME manager, I see it under Applications->Programming->Code::BlocksIDE.

I am not sure on why build-essential crashed.  Was any error displayed?

---

### Post by Tyler5794 on 2010-08-19
Okay, I got CodeBlocks running, thank you. Is there any way I can get a CodeBlocks icon on the desktop so I can run it from there? And I've got Xfce, not GNOME, because it's Xubuntu, that wouldn't make anything different, would it?

Also, here's an example of the mousepad screwing up; (I was going to say "If I don't")
> If I dref=logo#!/?skref=logo#!/?sk=messagesref=logo#!/?sk=messagesref=logo#!/?sk=messageson=messages
Would I need a driver for a laptop mousepad or something?

When I type "sudo apt-get install build-essential" it just moves on to the next line on the terminal for me to type on. :/

I don't seem to have permission to access "root" on the file manager, it said permission denied. This has happened with a few things, is there any reason why I wouldn't be able to view some of my files? I'm the only user.

---

### Post by john newbuntu on 2010-08-19
A really dumb question here.  You did not happen to type the quotes did you? Try without quotes
```
sudo apt-get install build-essential
```

Also are you able to highlight code::blocks, drag and drop it on to the desktop?  I have not tried this on xfce.

Sorry, I do not know the solution to your mousepad/touchpad problem.

---

### Post by Tyler5794 on 2010-08-21
No, I'm not typing it with the quotes.
I tried dragging it to the desktop, it didn't do anything. It's under Development, in the Applications bar.
Do you know why I wouldn't have the permisisons to do everything on here? For example, I can't delete the folder "live" from my desktop; it was for GParted.

---

### Post by john newbuntu on 2010-08-22
You seem to have some permission issues with xubuntu.   I must admit that I am not an xfce expert.  Log out and log back in using the xfce-default or some such option.  See if you are able to work normally.  Otherwise, see if xfce-settings-manager has an option called "users and groups" and see if you have the privilege to administer the system.

For shortcut, if you right click on the desktop, and get an option like "create launcher"  Fill that form up and you will hopefully get the shortcut to run codeblocks on your desktop.

---

