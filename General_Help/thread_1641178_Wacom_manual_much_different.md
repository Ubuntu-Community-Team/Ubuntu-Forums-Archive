---
title: "Wacom manual much different"
date: 2010-12-08
forum: General Help
---

### Post by WBojangles on 2010-12-08
Hello,
I was setting up my Wacom tablet a few days ago, following [this tutorial]("https://help.ubuntu.com/community/Wacom"), and it using "man wacom" worked fine to get parameters in the tablet configuration text.
I realized that I needed to change something, so to look up the name of the parameter, I went to the terminal again and used "man wacom" just like last time, but the manual was only 24 or so lines. I don't know how this happened because I didn't change anything but that text document to set up the tablet. If you need I can post the contents of it. Is there anywhere I can find it or fix this?

---

### Post by Favux on 2010-12-08
Hi WBojangles,

Sure I'd like to see your 'man wacom'.

Looking at the Wacom wiki I'm not sure what you did for 10.4.

Which Wacom tablet do you have?  How are you configuring it?

---

### Post by WBojangles on 2010-12-08
Here is that new manual:

```
wacom(8)                      Wacom kernel module                     wacom(8)

NAME
       Wacom -   Tablet Input Kernel Driver

DESCRIPTION
       wacom-dkms  Uses  DKMS  to  automatically build the Wacom Module.  This
       allows newer hardware to be used with the current Linux Kernel.

       More information
              wacom-dkms        maintainer:         Taylor         LeMasurier-
              Wren<ripps818@gmail.com>

AUTHORS
       Taylor LeMasurier-Wren <ripps818@gmail.com>

wacom-dkms                       June 10, 2010                        wacom(8)
```

This looks like it belongs somewhere related to the wacom driver info, but why all of a sudden on "man wacom?"

The tablet I have is the Bamboo Fun (CTH-661), and I configured it exactly as the community documentation shows with method 1; I used "sudo apt-get install xserver-xorg-input-wacom wacom-tools," then "gksudo gedit /usr/lib/X11/xorg.conf.d/10-wacom.conf" to add in parameters like "Option 'KeepShape' 'on'" among a few others like type. I was looking to change the type option from "touch" to something that used the pen (nothing responded to the pen), and I wanted to be sure before guessing it was "pen" and maybe breaking something.

---

### Post by Favux on 2010-12-08
Did you do method 3 and install the ppa bluez package?

---

### Post by WBojangles on 2010-12-08
That method sort of implied that I would follow it if I used a bluetooth tablet, never even knew there was one. I tried it anyway and it worked fine until the last step:

Entering "sudo dpkg-reconfigure linux-image-'uname -r'"
```
Package `linux-image-uname' is not installed and no info is available.
Package `-r' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: linux-image-uname -r is not installed

```

I don't really know what this means or what I should do.

---

### Post by Favux on 2010-12-08
Good, you don't need bluetooth so we don't want that installed.

Somewhere you installed linuxwacom as a dkms (dynamic kernel module support) package.  Does that ring any bells?  That's OK, but you want to know which version (date) of the drivers you have.  I haven't seen one that is up to date.

I'd suggest something along the lines of the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

But first you would have to uninstall the wacom dkms package.  That's what's changed the manual.

---

### Post by WBojangles on 2010-12-08
Wonderful, the manual is back to the way it was and I will get to following that how-to soon, I need some sleep first. Thanks for all the help!

---

