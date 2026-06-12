---
title: "Why does usb drive open VLC?"
date: 2011-11-06
forum: General Help
---

### Post by AVH on 2011-11-06
I have just installed 11.10. Plugging in a usb drive opens VLc. VLC is not selected a a default for anything that I know of. If anyting, I would want the default for a usb to be Nautilus. How can I change this?

---

### Post by lafskelton on 2011-11-06
VLC most likly is set to do that 
ie normally the defualt would open 
so  youll need to find some options to fix it
 
 
]:popcorn:

---

### Post by fragos on 2011-11-06
For some reason storage devices connected via USB are assumed to be a device and therefore an application is offered. Here's where the default applications are changed. Unfortunately as of 11.10 one of the options is no longer open as file system with Nautilus.

System Settings -- System Info -- Default Applications

---

### Post by Briareus on 2011-11-08
> **fragos said:**
> For some reason storage devices connected via USB are assumed to be a device and therefore an application is offered. Here's where the default applications are changed. Unfortunately as of 11.10 one of the options is no longer open as file system with Nautilus.

System Settings -- System Info -- Default Applications

I've had this problem ever since I upgraded from 11.04, and changing the default application settings doesn't do anything for me. VLC was originally set as the default for video, but I tried changing that to KMPlayer and Totem and that didn't do anything. Whenever I plug in a USB stick, VLC starts up, loads every file from it into its playlist and attempts to play them.

Can't find any internal settings in VLC that would be responsible for this, either.

---

### Post by mc4man on 2011-11-08
see this post for command to fix or there is a link in post that shows how to manually remove the problem
[http://ubuntuforums.org/showthread.php?p=11431237#post11431237](http://ubuntuforums.org/showthread.php?p=11431237#post11431237)


Edit: My preferred would be to go to the link & remove the problem directly

---

### Post by AVH on 2011-11-09
> **mc4man said:**
> see this post for command to fix or there is a link in post that shows how to manually remove the problem
[http://ubuntuforums.org/showthread.php?p=11431237#post11431237](http://ubuntuforums.org/showthread.php?p=11431237#post11431237)


Edit: My preferred would be to go to the link & remove the problem directly

Thanks, that worked for me. I am puzzled a to why VLC opened. It is not selected as a default for anything.

---

### Post by mc4man on 2011-11-09
> **AVH said:**
> Thanks, that worked for me. I am puzzled a to why VLC opened. It is not selected as a default for anything.

If you where to open mimeapps.list you'd likely see vlc.desktop as the 1st listed on the inode/directory= line in the [Added Associations] section.
This is quite normal & useful.

The issue for upgraders is outlined in my bug report - 
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/876788](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/876788)

Basically upgraders may have a inode/directory=nautilus-folder-handler.desktop  in the [Default Applications] section. Because that .desktop is no longer used, in some limited instances, when failing to find the listed Default .desktop the action will then use the 1st. listed in the Added section

---

