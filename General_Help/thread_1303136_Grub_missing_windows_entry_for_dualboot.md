---
title: "Grub missing windows entry for dualboot"
date: 2009-10-27
forum: General Help
---

### Post by AustenB on 2009-10-27
Hello,

I recently updated ubuntu, and it gave me an option to keep my menu.lst the way it is, or change it to some other things.  I foolishly chose to change it to maintainers specifications or something, and now my Windows Vista loader option is missing from my grub menu.  Even though it was named Vista Loader, it was actually for Windows 7 btw. 

I did not make a backup of my menu.lst.

How can I set it up so I can boot into windows from grub again?

Thanks, any help appreciated

---

### Post by oldfred on 2009-10-28
To tell you exactly what the entry is we need you partition list. I assume you are not on Karmic yet as that is totally different.

sudo fdisk -l

backup
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
Edit
gksudo gedit /boot/grub/menu.lst

entry either before or after the automagic lines, but adjust for your partition:

title Windows 7 Ultimate, chainloader (on /dev/[COLOR=DarkRed]sda1[/COLOR])
rootnoverify ([COLOR=DarkRed]hd0,0[/COLOR])
savedefault
chainloader +1

---

### Post by AustenB on 2009-10-28
Partition List:

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1306    10490413+  27  Unknown
/dev/sda2   *        1307       14054   102397875    7  HPFS/NTFS
/dev/sda3           14055       22644    68999175    7  HPFS/NTFS
/dev/sda4           22645       30401    62308102+   5  Extended
/dev/sda5           22645       23919    10241406   83  Linux
/dev/sda6           30380       30401      176683+  82  Linux swap / Solaris
/dev/sda7           23920       30379    51889918+  83  Linux


```I'm thinking it's on sda2, so do I just backup and edit with the lines you gave and I'll be good to go?

---

### Post by fluffman86 on 2009-10-28
are you sure it's not sda2 or sda3?  Win7 should be on an ntfs partition...

---

### Post by AustenB on 2009-10-28
Ya my bad, I just edited the last post, sda2 is the main, sda3 is a seperate partition for storage.  sda1 is some acer manufacturer factury defualt thingy (i just booted into it lol).

---

### Post by AustenB on 2009-10-28
Thanks guys, it works now, so I changed the entry to

title Windows 7 Ultimate, chainloader (on /dev/sda2)
rootnoverify (hd0,1)
savedefault
chainloader +1

and it works fine now.  :popcorn:

---

