---
title: "VirtualBox/VMWare"
date: 2009-07-21
forum: General Help
---

### Post by colintivy on 2009-07-21
Hi Folks!

Being frustrated with some miscellaneous hardware that cannot be used because of the lack of support within Ubuntu, I am wondering if either of the above could be used to to run Win98SE within Hardy and their Win drivers? I know that Linux can be run within Windows like this but have not heard about the reverse. I have a legal Win98SE disk and all the Win driver disks (I am a fugitive from Gates-bloat and apart from small niggles am very happy where I am). Clearly the HD space might be an issue, I do have 30Gb with only Linuxy thins on it. 

Incidentally can anyone pass comment on the desirability of having a separate Home partition when most distro Live CDs usually make you combine it when you install? The Kitz tutorial on separating one out looks a bit formidable.

colintivy :[ 

Tags: VirtualBox,VMWare,Win98SE

---

### Post by hyperdude111 on 2009-07-21
Use virtualbox it is free and easier to use than Vmware.

The Windows versions of these apps have the same features as the linux versions. Any x86 or x64 operating system can be run in a virtual machine (This includes MacOS but because of their license they can ot be officially supported). This is every version of windows and most (about 95%) types of linux.

Linux can run Linux and Windows in a virtual machine (and mac with a few 
hacks)  

Windows can run Linux and Windows in a virtual machine (and mac with a few 
hacks)

---

### Post by raymondh on 2009-07-21
My Virtualization set-up/s:

Mac OSX host virtualizing XP and Ubuntu as guests (using VMWare)
Ubuntu 9.04 host virtualizing XP (using Virtualbox)
XP host virtualizing Ubuntu (guest)

Having a separate /home allows you to re-install/upgrade root without reformatting your /home thus retaining your settings, cnfig files, /home data, etc. 

If you intend to boot several distros, a /data makes more sense because the config files or one distro may confolict with the config files of another.

See Bodhi.zazen's [post]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition").  Scroll down to his thoughts on /home and /data.

Good luck.

---

