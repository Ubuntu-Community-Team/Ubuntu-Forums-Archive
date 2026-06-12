---
title: "mouse cursor stuck at drag symbol (hand) and not usable"
date: 2012-06-09
forum: General Help
---

### Post by scotty64 on 2012-06-09
On my Xubuntu installation the mouse cursor gets sometimes stuck in drag mode (hand symbol) and although the mouse cursor moves, both mouse and keyboard are unusable.
Does anybody has the same problem ? Is there a simple way out of it ?
I am wondering if this is a bug or some (for me) hidden screen lock feature.
The only way out of this hang is to switch to another tty and restart lightdm.
The problem mostly appears when having Firefox open and moving the cursor from the Firefox window to another. I may press a button accidentally while doing this, but I am not aware of this.

---

### Post by ddavidd on 2012-06-13
We are now getting the same problem with my computer and my daughter's laptop.

Both newly installed with 12.04
It seems to happen often when working in Firefox, typically when leafing through the bookmarks.
The mouse pointer changes to a hand, still moves but nothing else works except cold restarting or this workaround that I found in Google, but it still shuts all running applications:

Ctrl + Alt + F1
login
> sudo restart lightdm
GUI appears again and asks for logon


Does anyone have a solution to the problem?

---

### Post by crampi on 2012-06-13
Having the same problem with FF 13.0 Ubuntu 10.10.  Does seem to involve tabs and/or moving them off or back to FF.  
 
 I have been able to Alt-F then Q to quit FF and save the rest of my desktop from a restart.

---

### Post by ddavidd on 2012-06-14
I read in a forum somewhere else that this problem affects Ubuntu 12.04 because it still uses kernel 3.2, whereas some other distributions use 3.4. 

Changing to 3.4 sounds a bit beyond my capabilities, I depend on the automatic updates. The new one today is offering kernel 3.2.0-25

Can I ask for expert views of this?

---

### Post by ddavidd on 2012-06-15
Yesterday there was a kernel update.

I now have:
Version 12.04 (precise) (32-Bit)
Kernel Linux 3.2.0-25-generic-pae
GNOME 3.4.1

It just did it again!
As I was clicking through the favourites in Firefox, the mouse pointer turned into a hand and the pointer was gone.
Alt tab to bring windows into focus still worked but no menu shortcuts and the mouse still remained useless.
I had to use the workaround Strg-Alt-F1 again.
I had an instance of Word open in Virtual Box and very fortunately the automatic saving had worked.

So no improvement from the latest updates, please can anyone help?

---

### Post by ccrs8 on 2012-06-20
This has happened to me at least a half-dozen times since upgrading to Xubuntu 12.04.  Always when clicking on Firefox.  The cursor stays as the hyperlink hand no matter where it is moved and does not register clicks.  Using the keyboard still works fine, but I can not get the cursor unstuck.  I always had to just push the computer's power button to force a shutdown/reboot, but ddavidd's recommendation at least enables me to fix the issue without going to that extreme.

There has got to be a command that "restarts" the mouse, right?  That way, when it happens again we can keyboard shortcut to the terminal and then simply restart the mouse without having to log back in and out and restarting lightdm.

---

### Post by LewisTM on 2012-06-20
I have that sometimes on my latpop with a mouse attached but never though much of it since it was quickly fixed by touching the touchpad. Maybe disconnecting/reconnecting the mouse would help in you case? Or connecting a second pointing device?

By the way the shortcut to restart the X server is Alt-SysRq-K.
Maybe one could also map a keyboard shortcut to restart Xfwm4.
```
xfwm4 --replace
```
That would not force to quit any application.

---

### Post by xissburg on 2012-06-20
I am running Ubuntu 12.04 in a VirtualBox (host OSX Lion) and I also have exactly the same issue. It happens quite randomly, when I give focus to the Ubuntu window. Got a few updates to install right now, let's see what happens.

---

### Post by ddavidd on 2012-06-27
Ubuntu 12.04, Gnome classic desktop
It just happened again, once again while working in Firefox.
The mouse pointer turned into a hand and would not work.

This time the following workaround worked:
Ctrl Alt -->  to change screen and then Ctrl Alt --< to change back
Alt D (since it is a German installation) to open the left-hand Firefox menu
Then use the keyboard to run down the menu and close Firefox.
Then Open Office reacted properly again with cursor and no work was lost.

---

### Post by Seb71 on 2012-06-27
See [this bug]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1012257").

You can close Firefox with Alt+F4.

---

### Post by mage7 on 2012-07-08
The bug should fixed in the next update of firefox about 2 weeks from now. 
Although I wonder whether a program running under normal privileges being able to hijack a desktop is a sign of some bigger flaw in  the window manager or something.

---

### Post by scotty64 on 2012-07-09
I think there is more to this bug and it is not just Firefox to blame: I have experienced the same problem with FileZilla and the KeePass password safe running through Mono. In contrast to other reports both the mouse and the keyboard are stuck in my case (in the graphical window, the Alt Fx text consoles work fine). Sometimes only a reboot helped to get out of this. Switching to a text console and killing Firefox did not help and sometimes I was even unable to restart lightdm via console.

---

### Post by desertcreature on 2012-07-09
I have this problem too in Xubuntu 12.04.

Seems to affect many applications if not all.  Certainly not localised to Firefox anyway.  That's not very helpful I know but this is:

I have discovered that doing an Alt+Tab to switch windows frees the pointer.  Definitely no need to kill any processes!

For me this makes the problem an irritant rather than a show stopping, find-another-distro type affair.  But it's still annoying.

---

### Post by imbjr on 2012-07-22
I've seen odd mouse behaviour since upgrading to 12.04. It's infrequent, but I've just seen it occur 3 times in about 5 minutes. I was right-clicking script files to open them and leafpad opened each one successfully, but thunar then would think I was doing a drag-selection underneath the leafpad window.

---

### Post by danmbox on 2012-08-01
There is a way to reboot the mouse...

Switch to text console (ctrl+alt+f1)
Log in
sudo rmmod psmouse
sudo modprobe psmouse

Wait a little and then switch back to the X console.

I've just tried it and it worked for me.

---

### Post by Noccy on 2012-10-01
This happens every time I try to search in an MP3 with the slider in Audacious, but only on one of the comps. Utterly annoying :s

Any permanent fix to this?

---

