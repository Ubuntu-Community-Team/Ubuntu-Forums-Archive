---
title: "Vmplayer : running my Ubuntu install on XP ?"
date: 2006-06-12
forum: General Help
---

### Post by guix on 2006-06-12
I can install Vmplayer under XP and install an Ubuntu.
But can I run my real Ubuntu install under XP ?

---

### Post by aysiu on 2006-06-12
It will be a real Ubuntu install--it may not be your *existing* Ubuntu install, though.

---

### Post by guix on 2006-06-12
Thanks Aysiu.

Well, no, I don't see the point... I have my Ubuntu install for everything except games and a few progs. I keep my important data on Ubuntu (emails, photos, palm database...), accessing to this existing Ubuntu install would have been nice on XP for this, but I don't want to keep my whole data in a virtual Ubuntu install on XP.

Another solution could be Xen ? But I don't want it to load everytime in XP because of the game perf loss...

---

### Post by aysiu on 2006-06-12
Maybe someone will reply back with a neat trick to convert an existing partition into a virtual partition for VMPlayer to use. I'm not a VMPlayer expert.

---

### Post by guix on 2006-06-12
I wouldn't do it :-)
Well it doesn't matter...

---

### Post by mannheim on 2006-06-12
I've never done it, but the documentation for VMware Workstation says that you can set up vmware to use one of your "real" disks as a virtual disk in the virtual machine. This is an option which is intended specifically for a dual-boot machine, which is your situation. The relevant page in vmware's documentation is [here.]("http://www.vmware.com/support/ws55/doc/ws_disk_dualboot.html") I don't know if you can set that up in the Player version.

Myself, I'd be a bit nervous in case something got hosed. The instructions seem to refer mostly to Windows. It is a bit like taking your hard drive out of one machine and putting it in another machine, and hoping it will still work. This sort of "transplant" should work with ubuntu under similar hardware, I think; but I guess you will need to worry about needing different xorg.conf files for the two "machines", different fstab files and perhaps a few other things. I don't know how you would manage that.

---

### Post by guix on 2006-06-12
Yes, kind of dangerous hu ;-) ?

---

### Post by cjm5229 on 2006-06-12
Hi, Theoretically, VMware Server will allow you to transfer files between host and virtual machines. But to transfer from your Ubuntu files to the Virtual machine you would have to either put them on a fat partition to get access to it in Windows. But you should be able to mave everything you need form your Home files to the Virtual Machine, and then just reinstall your apps. There is a How to in the forums on installing VMware Server, It's free, but it it is still in beta,  I personally have not succeded in getting the networking to work in it. I was trying to load Windows in Ubuntu though so it might work better the other way.  One thing about it though, if you put it in and it is a bust, all you have to do is delete the virtual machine files. In other words it won't break anything if it fails to work.   Try It, and good luck.

---

