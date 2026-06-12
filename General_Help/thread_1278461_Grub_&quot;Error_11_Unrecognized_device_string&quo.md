---
title: "Grub &quot;Error 11: Unrecognized device string&quot;"
date: 2009-09-29
forum: General Help
---

### Post by samuelhug on 2009-09-29
About a week ago when I restarted my computer I got the following error when grub tried to boot.

```
Booting command-list

root b4643e8b-619f-4bf6-8e4e-0d610f081685

Error 11: Unrecognized device string
```

b4643e8b-619f-4bf6-8e4e-0d610f081685 is the UUID of my /boot partition.

This is my menu.lst
```
title		Debian GNU/Linux, kernel 2.6.28-15-pentium4
root		b4643e8b-619f-4bf6-8e4e-0d610f081685
kernel		/vmlinuz-2.6.28-15-pentium4 root=UUID=3df8d684-70d6-4509-85d4-c712a9043c18 ro quiet splash
initrd		/initrd.img-2.6.28-15-pentium4
```

I later got around the problem by changing it to 
```
title		Debian GNU/Linux, kernel 2.6.28-15-pentium4
root		(hd0,4)
kernel		/vmlinuz-2.6.28-15-pentium4 root=UUID=3df8d684-70d6-4509-85d4-c712a9043c18 ro quiet splash
initrd		/initrd.img-2.6.28-15-pentium4
```

does anybody have any idea why this happened?

---

### Post by pipax on 2009-10-02
Hi, I got the same today after automatic updates were installed, for some reason kernel 2.6.28-15 64bit was installed while this was already done a few weeks ago by a previous update.
So that wasn't changed.
But after the update the system rebooted resulting in "Error 11: Unrecognized device string".
Fortunately I could boot my 32bit Ubuntu partition and from there examined menu.lst..
See below the differences between the old and the new menu.lst:

After update

title        Debian GNU/Linux, kernel 2.6.28-15-generic
root        bcce5ca8-c31c-4ac4-820f-5f89a3679f6e
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=bcce5ca8-c31c-4ac4-820f-5f89a3679f6e ro quiet splash
initrd        /boot/initrd.img-2.6.28-15-generic

Before update

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        bcce5ca8-c31c-4ac4-820f-5f89a3679f6e
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=bcce5ca8-c31c-4ac4-820f-5f89a3679f6e ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

Apart from the title and the quit at the end they are the same...

After overwriting my "new" menu.lst with the one before the update the problem was solved. :)
It looks like the change in the title to "Debian GNU/Linux" caused the problem..
I still wonder why a kernel-update was presented while I had that kernel already in use from a previous automatic update....

---

### Post by oldfred on 2009-10-02
The difference is root vs UUID.
The entry is 
root   (hdx,y)
or
uuid UUIDnumber

It will not work with
 root UUIDnumber

---

### Post by pipax on 2009-10-03
> **oldfred said:**
> The difference is root vs UUID.
The entry is 
root   (hdx,y)
or
uuid UUIDnumber

It will not work with
 root UUIDnumber
Thanks Oldfred, that explained the issue.

---

### Post by FeyerbrandX on 2009-10-30
I've apparently gotten the same problem.  It's 4 in the morning, so I want to make absolutely sure that I don't implode the system by putting in the wrong (hdX,Y) format.

I dual boot Vista and currently 9.04, and am running on the 9.04 live CD now.  Vista boots fine, but since I last logged into Ubuntu a week or two ago, got the error, but decided just to sit on it until 9.10 came out and get all repair and update stuff settled in one go.

Here is my Menu.lst 

----
default 1
timeout 15

title Other operating systems:
root 

title Windows Vista/Longhorn (loader)
root (hd0,0)
chainloader +1
savedefault
makeactive

title Windows Vista/Longhorn (loader)
root (hd0,2)
chainloader +1
savedefault
makeactive

title Ubuntu 9.04, kernel 2.6.28-15-generic
root 
kernel /boot/vmlinuz-2.6.28-15-generic root=UUID=cd7f846f-142a-4a8d-99de-4b68ca274d56 ro quiet splash
initrd /boot/initrd.img-2.6.28-15-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root 
kernel /boot/vmlinuz-2.6.28-15-generic root=UUID=cd7f846f-142a-4a8d-99de-4b68ca274d56 ro  single
initrd /boot/initrd.img-2.6.28-15-generic

title Ubuntu 9.04, memtest86+
root 
kernel /boot/memtest86+.bin
quiet
-----


Here is the result of fdisk-l
----
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37660   302503918+   7  HPFS/NTFS
/dev/sda3           37661       38913    10064722+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4186b3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19699   158232186    7  HPFS/NTFS
/dev/sdb2   *       19700       38128   148030942+  83  Linux
/dev/sdb3           38129       38913     6305512+   5  Extended
/dev/sdb5           38129       38913     6305481   82  Linux swap / Solaris
-----

Seeing any other problem so far's result, I *think* I need to change the relevant parts of menu.lst to:

----
title Ubuntu 9.04, kernel 2.6.28-15-generic
root **hd(0,1)**
kernel /boot/vmlinuz-2.6.28-15-generic root=UUID=cd7f846f-142a-4a8d-99de-4b68ca274d56 ro quiet splash
initrd /boot/initrd.img-2.6.28-15-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root **hd(0,1)**
kernel /boot/vmlinuz-2.6.28-15-generic root=UUID=cd7f846f-142a-4a8d-99de-4b68ca274d56 ro  single
initrd /boot/initrd.img-2.6.28-15-generic

title Ubuntu 9.04, memtest86+
root **hd(0,1)**
kernel /boot/memtest86+.bin
quiet
----

But I'd much rather know than just think.  That one sda5 throws me; that maybe the memtest86+ or recovery mode needs to be hd(0,4), so before I pull the trigger, I'll sleep on it and hope for an answer.

Thanks

edit(4 in the morning BB code bracket mess)

---

### Post by FeyerbrandX on 2009-10-30
Unfortunately, I don't know how to give a Live CD account admin rights to fix this file.  Any further help would be appreciated.

And after looking at what dumped this off the main page, I think I'll just fix it and wait on 9.10...

---

### Post by KPjotr on 2009-10-30
> **FeyerbrandX said:**
> Unfortunately, I don't know how to give a Live CD account admin rights to fix this file.  Any further help would be appreciated.

And after looking at what dumped this off the main page, I think I'll just fix it and wait on 9.10...
I think you can simply enter "sudo". It won't ask for a password.

---

### Post by FeyerbrandX on 2009-10-30
I managed to get it working through directly editing the "root" line at start up.  After that things mushroomed out of hand, but I got it back under control.

The root cause of my original problem was that I somehow forgot how to work the grubeditor tool properly.  I remember just being able to delete old versions of ubuntu's loader without repercussions, but the last time (before the error originally occured) it wiped out the suffix to "root".  And it did it again just now.  The simple "sudo gedit...." command worked to fix the whole thing after I chased the error from Ubuntu, to Vista and back again.

Thanks for the help KPjotr.

I'm not shutting my computer off for a week, I've seen the bootloader too much in a day.

---

