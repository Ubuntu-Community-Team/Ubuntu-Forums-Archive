---
title: "Need help getting files from Vista(dead)"
date: 2010-08-20
forum: General Help
---

### Post by Chris.. on 2010-08-20
I have a desktop running Vista Home Premium 32-Bit.  I have no back story on what happened to my computer because i was not there when it happened.  When i boot up it eventually goes to a Unmountable Boot Volume error. All windows recovery options so far have lead to dead ends.

I have files that are on the harddrive that i _**need.**_  I have burnt a Live CD and booted from that but ended up have access problems. I was once able to access folders and files but without read/write permissions, so i was able to see the files but if i tried to copy it would only end up being a 0kb copy.

I now have a USB Bootable key with persistence. But im still have problems with permissions. I have only once been able to view the files once.

I could really use some help on this and im quite noobie with ubuntu, so if you do have any ideas then please explain like your talking to an idiot (i will not take any offense:D)

---

### Post by gradinaruvasile on 2010-08-20
You should be able to copy files from a NTFS partition with no problems. I did it many times from Ubuntu/Debian live CDs/USBs. Maybe the files are damaged.
If you have read permissions that means you can copy the file in normal circumstances.

You should boot from a vista (or maybe XP works too) install cd and enter recovery mode and do a chkdsk.
Dunno exactly how in Vista, i used only XP for this purpose, google it up.

---

### Post by Chris.. on 2010-08-20
Yes but my problem is that i can't just copy and paste.  I tried to use windows recovery and run a chkdsk but since it dosn't detect my drives that was a dead end, since i can't choose which drive to start recovering.

What i want to do is figure out how to change my permission to have read/write to files instead of just folder viewing access.  By default i don't have the permissions to files, only folders.

I heard that if i set up a FTP or network then i might be able to ignore the permissions on the files.

---

### Post by kaldor on 2010-08-20
Wild guess, but try using *gksudo nautilus* in the terminal on the Live CD (Applications>Accessories>Terminal).

That'll bring up a GUI with full read/write permissions. Not sure if it'll work for accessing your Vista partition though.

If you can, try it. Then copy/paste the files from that to a USB drive or something.

Sorry if this is not accurate ^^

---

### Post by efflandt on 2010-08-20
The problem is that if the drive has bad sectors or is otherwise corrupted, you may have trouble reading anything from it.

I had that problem with a failing laptop drive.  When booted from Ubuntu live CD, I could only copy some files from it before copying hung.  Then in an external usb enclosure I could not mount it in Windows or Linux.

But a few weeks later I connected it to my Ubuntu desktop and it magically auto mounted and I was able to copy most necessary files from the user's Windows dir except for a few files and directories that could not be read.

Another time more than one virus corrupted the replacement drive and Windows again refused to boot at all to protect what was left on the drive.  But **chkdsk /f** and then a virus scan in Windows on another PC was able to fix it.

---

