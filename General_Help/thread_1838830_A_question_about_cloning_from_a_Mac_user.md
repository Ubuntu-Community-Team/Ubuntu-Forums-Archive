---
title: "A question about cloning from a Mac user"
date: 2011-09-04
forum: General Help
---

### Post by rmcellig on 2011-09-04
My main OS (for now :-))is Mac OS Lion. I have used Macs since 1988, and am now really making a concerted effort to immerse my self in Linux. There is something about Linux that always draws me back. 

On my Mac, I use a free program called Carbon Copy Cloner. What I love about this app is that overnight, it creates a bootable clone of my internal drive to an external USB drive. This way if anything happens to my internal drive, I can always boot from the cloned USB drive and clone back to a brand new HD if need be. 

I am hoping that there is something similar in the Linux world. I don't want to have to always have to restart my Mac from something like Clonezilla to clone my drive when on my Mac I can use CCC to seamlessly clone my drive daily.

If I ever switch over to Linux 100% I need to know that there are ways of doing this type of cloning.

---

### Post by FormatSeize on 2011-09-04
I found [this](http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk) via a quick Google search. I have no experience with cloning disks, so I'm not sure what can go right or wrong with this.

---

### Post by brucehohl on 2011-09-04
rmcellig, since you want redundancy in case of disk failure another option (if your computer will hold 2 disks) would be to set-up software RAID1 during the Ubuntu install. If you do this  you should read about the linux software raid tool mdadm and make sure you know how to replace a failed disk (i.e. test). I have software raid1 on several PCs - it works well.

---

### Post by rmcellig on 2011-09-05
OK. Here is the bottom line for me and maybe cloning is overkill. What I want to do is if my computer fails and I need to get back up and running quickly, what is the best way to do this? Backup my home directory and other pertinent directories to another place so that all I wold have to do is restore the backups to a new ubuntu install? If there are better quicker ways of getting back up and running, I would really be interested!!

Thanks!!!!!

---

### Post by brucehohl on 2011-09-05
> Backup my home directory and other pertinent directories to another place so that all I wold have to do is restore the backups to a new ubuntu install?

That is exactly what I do ... here is what I do more specifically:

(1) I put all my important data in one location - under /home/user1 under directories like Documents, Pictures, Music, etc.
(2) I rsync this important data to both a second disk and space on remote computer.  (I plan to change my remote backup to Unbuntu One shortly.)

I share via Samba /home/user1 so I can use this data from any other local machine in my house (or remote via a tunnel or sshfs). 

If my main PC goes down I have options:
(1) Keep working from the backed-up files ...
(2) Fix the main PC and copy over any changed files.
(3) Move the files and arrangement to another PC.

I keep the local backup (as well as the remote backup) because restoring lots of data from a remote backup can take a long time, and I only backup my test virtual machine disks locally due to their large size.

Maybe this will give you some ideas for what will work best for you.

---

### Post by nothingspecial on 2011-09-05
What about clonezilla

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by cbowman57 on 2011-09-05
> **nothingspecial said:**
> What about clonezilla

[http://clonezilla.org/](http://clonezilla.org/)

It's quick, it's easy & it works.

That's my first recommendation.

---

### Post by rmcellig on 2011-09-05
I just came across something that is really easy to use to clone a drive in Linux and I think I can convince my friends who want to switch who are real newbies that this is probably as easy as it gets. It's called Redo backup. I'm cloning my wife's PC at the moment/ Now this is really simple. Boot from th Live CD or USB stick, click on the backup tab, choose the source and destination and that's it. Want to restore the backup image? Click on the Restore and restore the image. Very simple.

---

### Post by cbowman57 on 2011-09-05
That does sound like a nice piece of software.  Is it limited to disk cloning or can it also do partitions?

---

### Post by leclerc65 on 2011-09-05
Parted Magic contains Clonezilla and more.

---

### Post by rmcellig on 2011-09-05
The boot CD has Firefox, Partition software, various tools etc... I think that Parted Magic has about the same thing. I have a copy of Parted Magic software somewhere. It's a very good CD to have on hand. I will try Clonezilla again. I wish they had a more user friendly interface. I'm OK with it but someone like my Mom would be totally lost.

---

### Post by linuxuser12345 on 2011-09-05
In the Ubuntu Software Center, there is a program called "Dell Recovery." Download and install it. This program creates a bootable copy of your entire system, if something should happen to it, and yes it works on systems other than Dell.

---

