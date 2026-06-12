---
title: "nautilus seems to ignore file assocations ..."
date: 2009-07-31
forum: General Help
---

### Post by Sysyphus Jones on 2009-07-31
... when I plug in a usb disk or open a truecrypt volume and browse the file system.

Just to clarify, ordinarily if I click say an htm file, firefox (of course) launches or opens a tab if already running. However in the above scenario nautilus doesn't seem to do anything. Right click and select 'open' does nothing, though' open with...' works.

Seems to be general, other file types also fail to open associated apps.

(Thunar and dolphin do seem to honour associations though.)

This seems peculiar to me. Is it some sort of security issue? How can one stop nautilus from doing this?

---

### Post by fragos on 2009-07-31
I've never seen this occur. I don't use truecrypt volumes but do mount disks over NFS with no problem. When you say USB disk are you talking about a FAT format memory stick or a USB connected hard disk that may use a Linux format like EXT3? I would check permissions and ownership to see if the problem lies there.

---

### Post by Sysyphus Jones on 2009-07-31
external usb drive and trucrypt volumes are both formatted to NTFS

my NTFS formatted windows boot partition doesn't seem to show this problem BTW

Perhaps it is a permissions thing, but then it's odd that the other file browsers I tried seem happy to open the files.

Anyway if there isn't a quick fix I'll just live with it 

Thanks for your thoughts

---

