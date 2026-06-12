---
title: "Help needed with getting root access!"
date: 2011-06-18
forum: General Help
---

### Post by Jexable on 2011-06-18
I'm trying to readyboost(with my usb) on my linux ubuntu. I am trying to get into the root folders and any other folders I'll need to access to get this done.

when I do the code; sudo mkswap /dev/sda1 in the terminal it says the device or resource is busy. I assume it's because I don't have access to the root files and any others in the dev folders.

The folders come up with an X over the icon, and them folders, are the ones I can't access(which makes sense)

Can someone help me... I'm trying to follow this tutorial and it's not working: [http://ubuntuforums.org/showthread.php?t=395435](http://ubuntuforums.org/showthread.php?t=395435)

(I HAVE LAST YEARS UBUNTU 10.04 I think it is?)

---

### Post by mikewhatever on 2011-06-18
If you didn't 'have access' the message would read 'permission denied'. /dev/sda is most probably not the USB device (it really never is), but rather the hard drive, and /dev/sda1 may be your windows or Ubuntu partition. Do check the device namings with **sudo fdisk -l**.

---

### Post by oldos2er on 2011-06-18
Usually Ubuntu mounts USB devices as /dev/usb0, /dev/usb1, etc. With your USB drive plugged in, use the **mount** command to find exactly where it's mounted.

---

### Post by Dave_L on 2011-06-18
> **Jexable said:**
> Can someone help me... I'm trying to follow this tutorial and it's not working: [http://ubuntuforums.org/showthread.php?t=395435](http://ubuntuforums.org/showthread.php?t=395435)

Did you read the whole thread? The posts at the end suggest that following that tutorial may be a bad idea.

---

### Post by mikewhatever on 2011-06-18
> **Dave_L said:**
> Did you read the whole thread? The posts at the end suggest that following that tutorial may be a bad idea.

+1
Ubuntu is not Vista, which is what inspired the author. It doesn't need 3GB of swap, let alone additional 3GB.

---

