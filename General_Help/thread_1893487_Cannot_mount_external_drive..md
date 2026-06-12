---
title: "Cannot mount external drive."
date: 2011-12-10
forum: General Help
---

### Post by CallsignBaron on 2011-12-10
Hope someone can help.

Just installed Kubuntu 11.10 and I cannot mount an external hard drive formatted HFS+ on a Mac. Strangely, Ubuntu was able to read the drive and download files from it, but, Kubuntu has been unsuccessful. Can anyone tell me what Ubuntu/Unity has installed that will allow it to access the drive where Kubuntu/KDE cannot?

On a related note, Ubuntu was able to access my Time Capsule's internal drive as well (read and write access) and Kubuntu cannot even see it. If I can't fix this I may have to go back to Ubuntu but I am really digging KDE.

Any help? Thanks in advance.

---

### Post by dabl on 2011-12-10
First question, is the drive actually seen by the OS:

```
sudo fdisk -l
```

I would suppose you will see it, but need to verify.

Second question, have you tried hot-plugging the running drive into the running Kubuntu system, rather than booting with it connected?  There's a KDE device notifier that should pop up and offer to open the device in Dolphin, or play media, etc.

---

### Post by CallsignBaron on 2011-12-10
Yes and Yes

Kubuntu sees the external drive and gives me options (Open Dolphin or Open Gwenview) But when I try I get theis error:

The requested operation has failed.: Requested filesystem type is neither well-known nor in /proc/filesystems nor in /etc/filesystems

---

### Post by dabl on 2011-12-10
OK, I have no experience using hfs+, but it looks like there are some special procedures needed:

[https://help.ubuntu.com/community/hfsplus](https://help.ubuntu.com/community/hfsplus)

The recognition (or not) of a filesystem type is not, AFAIK, a function of the desktop environment -- I don't see why KDE would not be able to use it if Gnome can use it.  But, is the underlying Linux OS the same, or did you reinstall Kubuntu?  If the latter, then possibly there is a driver or kernel module missing in the Kubuntu installation that you had in the Ubuntu system.   :confused:

---

### Post by dabl on 2011-12-10
Looks like you need the hfsutils package installed.  Then with that, here is a non-automatic way to get it mounted:  [http://mintppc.org/forums/viewtopic.php?f=15&p=4372](http://mintppc.org/forums/viewtopic.php?f=15&p=4372)

---

### Post by CallsignBaron on 2011-12-10
> **dabl said:**
> Looks like you need the hfsutils package installed.  Then with that, here is a non-automatic way to get it mounted:  [http://mintppc.org/forums/viewtopic.php?f=15&p=4372](http://mintppc.org/forums/viewtopic.php?f=15&p=4372)

That did it dabl, thanks so much! :KS

Also, can see my Time Capsule now (router and printer - in fact I got the printer set up so I can use it!). Any ideas how I might see and access the internal drive? Again, this was something Ubuntu could do out of the box so I'm sure Kubuntu could do it if I can set it up like Ubuntu.

---

### Post by dabl on 2011-12-10
> **CallsignBaron said:**
> 

 Any ideas how I might see and access the internal drive? 

Again, first we go back to basics -- can you see it with fdisk -l?  If so, what it the filesystem type?

---

### Post by CallsignBaron on 2011-12-10
Can't see it. 

Can see the Time Capsule router and the attached printer (can get wireless Internet and print)  in Dolphin under Network, but cannot see the internal hard drive.

---

### Post by dabl on 2011-12-10
OK, that says Linux is not even aware of the drive.  So it doesn't matter about the desktop environment.

What kind of drive (IDE or SATA), and how is it set in BIOS?  Whatever the "channel" or "mode" setting is in BIOS, try changing it, and then see if fdisk -l will pick it up.  Until the Linux system sees the drive, you're not gonna mount it or use it.

---

### Post by CallsignBaron on 2011-12-10
This is not a connected drive, it is a network drive that lives inside the Time Capsule router.

[http://store.apple.com/us/product/MD032LL/A/Time-Capsule-2TB?fnode=MTY1NDA0Mg](http://store.apple.com/us/product/MD032LL/A/Time-Capsule-2TB?fnode=MTY1NDA0Mg)

BTW, the USB external HFS+ drive is working great now, with read AND write access. Thanks again for that!

---

### Post by dabl on 2011-12-10
OK, from what I can undestand about that device, it is designed to operate on an Apple (appletalk?) wireless network.  So your real issue is not about mounting it or reading the filesystem on it -- it is about making your Kubuntu box interoperable with Apple's network protocol.  About which I know nada.  Sorry.

---

### Post by CallsignBaron on 2011-12-10
That's ok, you have been very helpful and I really appreciate it! I am going to mark this thread solved because the original problem is fixed.

Thanks again!

---

### Post by dabl on 2011-12-10
Glad to help.  This may help with your next challenge:  [http://viebrock.ca/article/22/file-sharing-from-linux-to-os-x-a-quick-guide](http://viebrock.ca/article/22/file-sharing-from-linux-to-os-x-a-quick-guide)

---

