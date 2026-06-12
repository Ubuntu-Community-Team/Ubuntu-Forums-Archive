---
title: "External HDD Problem"
date: 2010-03-02
forum: General Help
---

### Post by Durduman on 2010-03-02
1st I installed vista on laptop, then installed linux on external drive. I had a problem with grub that consisted in not booting vista when external drive was not plugged ( trough usb ). now... I followed some steps with advice on how to fix this problem and now.... I cannot see my external HDD. My ubuntu is not booting anymore from HDD and when I enter vista and plug in the external hdd it won't even see it ( it just plys a liitle sound that notifies me I plugged some usb device.... i think ). Please help this complete noob.     


this is the other thread:
 [http://ubuntuforums.org/showthread.php?t=1419959](http://ubuntuforums.org/showthread.php?t=1419959)

---

### Post by Ghost|BTFH on 2010-03-02
> **Durduman said:**
> this is the other thread:
 [http://ubuntuforums.org/showthread.php?t=1419959](http://ubuntuforums.org/showthread.php?t=1419959)

Sorry I do not have a solution at this time, but a reply will help bump it back up to the top...and I can tell you that it sounds like you ravaged grub and left the master boot record whimpering in the corner...

In other words, Vista has no clue what you just plugged in, other than it can recognize that "something" was plugged in - because Windows requires a working MBR too.

The only thing I can even vaguely suggest right now is to fire up the Ubuntu Live CD with the External HD plugged in, run gparted from System -> Administration -> gparted

Switch to the External HD (You should be able to tell which is which from the size of the drive and type of partitions - hopefully.

Then find the / partition and set it to bootable by right clicking on it and selecting Manage Flags.

This is advanced stuff however, and it might just be easier for you to reinstall to the External HD.  Of course, if I were doing this, I'd disconnect my Vista drive, so Ubuntu wouldn't see it and would simply create a direct MBR for solo booting - not dual boot.

In so doing, I would be able to use the BIOS and the USB device (plugged in or not) to dictate which one booted.

But like I said, this is only off the top of my head, hopefully someone can give you more detailed advice than this. :)

Cheers,
Ghost|BTFH

---

### Post by Durduman on 2010-03-02
overwhelming....

---

