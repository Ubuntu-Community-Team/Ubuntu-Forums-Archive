---
title: "2 Last little issues"
date: 2011-03-11
forum: General Help
---

### Post by thatoneguy99 on 2011-03-11
I am new to Ubuntu and ive gotten myself all setup except for two things that I just can't quite figure out.
  Problem 1: I have Thunderbird setup with the minimize to tray add on. I have it setup to start on boot but I would like it to start and then minimize to the system tray without me having to manually minimize it. I just can't figure it out.
   Problem 2: I have mounted a windows share with smbfs and it is in the fstab file but when the computer boots I have to type in terminal ```
sudo mount -a
``` then terminal asks me for root password and then another box comes up after that that just says password. In the second password box it doesnt matter what you type in it will still mount. Even leaving it blank mounts. I read in some other threads about editing rc.local and also visudo. Neither one of those fixed it. I also made a script to run the above command and then added it to system>preferences>startup applications. That didn't work either.

Any information would be very helpful. After these two tiny issues I will be good to go.

---

### Post by Krytarik on 2011-03-11
As for the Thunderbird question: You could use "wmctrl" to *close* Thunderbird right after it is run, therefore I would create a script and place it in Startup Applications instead of the current one of Thunderbird. "wmctrl" is in the official repos, the script may look like this, you have to adjust the delays to the speed of your machine:
```
#!/bin/sh
sleep 13
thunderbird &
sleep 5
DISPLAY=:0.0 wmctrl -c Thunderbird

```As for the mounting issue: I have no experience with smbfs, but at first I would check if the "auto" option is set in "fstab". About the second password query, sorry, I can't help.

---

### Post by thatoneguy99 on 2011-03-12
Half solved Problem 2. I used CIFS instead of SMBFS in the fstab file and then added password=(i left it blank). If you have questions and would like to see my exact fstab contents let me know. I have downloaded and installed wmctrl but I just havent messed with it yet. Im almost there.

---

### Post by Krytarik on 2011-03-12
Indeed, I have one question: I noticed that if I mount NTFS partitions that way:
```
/dev/sda6 /media/Data ntfs-3g rw,nosuid,nodev,allow_other,default_permissions,umask=007,uid=1000,gid=46 0 0

```
and move/copy files on those with Nautilus, the timestamps always change, whatever action one does. Do you know how to avoid this?

Since its the setup of my mom's machine I didn't really care about it so far. But I have to re-arrange my own partitions in the near future (Windows filessystems are still in FAT32, and I need to access unallocated spare space), and I am considering either a full-fledged linux disk, since I only very rarely use Windows (maybe once a year for the electronic tax return) and I don't even have it installed currently, or switching at least some partitions to NTFS.

---

### Post by thatoneguy99 on 2011-03-12
As far as mounting a partition I havent dabbled in that realm yet. The only mounting I have done is of a Windows shared folder. I am using my Netbook that came with Windows but I just formatted the HD and put Ubuntu on the whole thing. I have another computer with a dual boot of Windows XP and Kubuntu, which is not that good BTW, maybe its just KDE. I havent messed with mounting the other partition yet because I started messing with the Netbook. Pardon me for the dumb question but what does the timestamp do exactly? Have you tried Dolphin file manager and if so does it do the same thing? Im gonna look into your fstab entry some more and see what I come up with.

---

### Post by thatoneguy99 on 2011-03-12
One more thing I dont know if you got your fstab entry off of the forum but if you did and want to know more about it you can type man mount.cifs into terminal to see how everything works.

---

### Post by Krytarik on 2011-03-12
No, actually I took the entry out of "mtab" after I set up my mom's Ubuntu, and modified it a bit to our needs. Unfortunately I can't test it extensively, because its, like I said, my mom's machine, and I only rarely have access to it via VNC. As for the timestamps, they actually state the date/time they have been modified and accessed, and on Windows filesystems also the date/time of their creation.

---

