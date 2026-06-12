---
title: "WIndows changed ext3 to ntfs"
date: 2009-08-23
forum: General Help
---

### Post by tjb_15 on 2009-08-23
I was trying to fix windows 7 by going to the recovery console and I typed: "bootrec /fixmbr" and then "bootrec /fixboot". But for some crazy reason it decided, when it was installed, to install its boot loader on my data drive. So now my data drive which is formatted in ext3 now shows up as ntfs and can not be opened. I'm royally ticked off at windows boot loader. The only reason I was trying to fix it was so that I could play a game.

Thanks,
tjb

---

### Post by BinaryFeast on 2009-08-23
I don't think Windows actually reformatted your ext3 partition (it can't read ext3, so that may be why it is reporting it as NTFS). It just replaced the MBR with a preconfigured one and installed its own bootloader (which is what those two commands are meant to do), with the result that Ubuntu can't boot (I've been there and typed those commands myself, so I know). Have you tried booting from a live cd and tried to read your Linux partition? If so you could try to reinstall Grub and configure it to boot both OSs again.

---

### Post by tjb_15 on 2009-08-23
> **BinaryFeast said:**
> I don't think Windows actually reformatted your ext3 partition (it can't read ext3, so that may be why it is reporting it as NTFS). It just replaced the MBR with a preconfigured one and installed its own bootloader (which is what those two commands are meant to do), with the result that Ubuntu can't boot (I've been there and typed those commands myself, so I know). Have you tried booting from a live cd and tried to read your Linux partition? If so you could try to reinstall Grub and configure it to boot both OSs again.

Yes I have. I reinstalled it on the OS drive. Its the data drive that was change from ext3 to ntfs. 

I have tried to look at it in the live cd, but I can't.

thanks, 
tjb

---

### Post by tjb_15 on 2009-08-23
Screenshots:
[IMG]http://img.onthehill.info/Screenshots/Screenshot--dev-sdb%20-%20GParted.png[/IMG]
sdb1 should be a ext3
[IMG]http://img.onthehill.info/Screenshots/Screenshot-Information%20about%20-dev-sdb1.png[/IMG]

---

### Post by tjb_15 on 2009-08-24
Using "testdisk" I can see all of my files in "Advanced".

---

### Post by tjb_15 on 2009-08-24
> **tjb_15 said:**
> Using "testdisk" I can see all of my files in "Advanced".
I guess I pressed the right button in testdisk. Now it works

---

