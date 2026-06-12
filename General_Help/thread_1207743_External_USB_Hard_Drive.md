---
title: "External USB Hard Drive"
date: 2009-07-08
forum: General Help
---

### Post by John Gray on 2009-07-08
Hello everyone, 

I'm a proud new Ubuntu user, converted from XP 3 weeks and ago my wife and i are learning Ubuntu.  I have a questions;  I have a external hard drive that connected via USB.  the problem is only the first person to log into Ubuntu get to see that drive.  How to i get it to "Mount" (i think that's what it owuld be called) for each of us as we switch between users?  Thanks everyone....


John Gray

---

### Post by 5nak3 on 2009-07-08
While I'm no expert, and a better answer will most likely come around sooner or later

If you log in and the hard drive is mounted you can use the files.

When you log out and your wife logs in I was under the impression the hard drive would also automatically mount.

If it doesn't however, if you open up your home directory e.g.

On the top taskbar of the screen click on -> Places -> home folder

The hard drive should still be visible on the left hand "places" pane. All your wife has to do is click the icon of the hard drive and it will automatically mount.

I hope that helps.

---

### Post by John Gray on 2009-07-08
Yeah for some reason even when we switch users that drive doesn't "mount".  no clue why....

---

### Post by 5nak3 on 2009-07-08
So you can't even see the drive in the "places" pane on the side of the nautilus file browser window?

If you can see the drive, all you'd have to do is click it to mount it and then you can use the drive.

If not, I'm not too sure how to proceed as I've never come across this myself. So the only thing I can say is I hope someone comes up with an answer for you soon.

Sorry couldn't be much more help.

---

### Post by Jebtrix on 2009-07-08
One thing to check that I've noticed is that when you create a user from the initial install, then add a user later within Ubuntu, they do not start with the same default rights. If you go into System > Administration > Users and Groups, click Unlock. The just compare the Privileges list between the two users. Not sure if this is the problem, but good place to start.

---

### Post by John Gray on 2009-07-08
yes i did check in the users and groups and we do both have the same "User Privileges", however i just tried once i switched users to my wifes and went and browsed to /media/back-up a dialog box comes up saying that i do not have permission to view the contents of back-up.

so is it possible that because i do not have permission once switching users that it doesn't automatically mount.  It also doesn't matter for either user, if she logs in first then i can't access it and visa versa.  


John Gray

---

### Post by Jebtrix on 2009-07-08
Once I get a chance I'll play more with this but it looks hairy. Here is a similar detailed discussion on another distro:

[https://www.linuxquestions.org/questions/slackware-14/automounted-usb-flash-drive-file-ownerships-652274/](https://www.linuxquestions.org/questions/slackware-14/automounted-usb-flash-drive-file-ownerships-652274/)

---

### Post by 5nak3 on 2009-07-08
Me again, I noticed you already looked at the user privlages I was wondering did you see if

"Access external storage devices automatically" - was actually checked. 

Maybe that could solve th issue...

---

### Post by Jebtrix on 2009-07-08
I dont have a external HD where Im at but try:

```
sudo groupadd usb
sudo useradd -G usb your1stusernamehere
sudo useradd -G usb your2ndusernamehere
```

gksudo gedit /lib/udev/rules.d/50-udev-default.rules

Look for:

```
# libusb device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", MODE="0664"
```

Change to:
```
# libusb device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", MODE="0664", GROUP="usb"
```

Restart Machine

---

