---
title: "Ubuntu 10.04 not loading issue."
date: 2010-06-14
forum: General Help
---

### Post by [AK]Zip on 2010-06-14
I did quite a bit of searching and found others having the same issue, but it was when they update some old version which dated back to 2008. Since then a lot has changed so a similar issue but a different fix needed.

I installed ubuntu 10.04 desktop i386 on a server computer since I wanted a full GUI. It was done as a clean install onto a Dell PowerEdge 2650 with a dual Xeon 2.4GHz and 1.5GB memory. The hdd is a SCSI 36GB running without raid.

I am getting an error of "Alert! /dev/disk/by-uuid/.. does not exist. Dropping to a shell!" and so forth. You can see the whole thing at the bottom of my post. If I type exit it will fully load and function correctly, but I need it to do it without having to type exit because I will be using this for WOL/teamviewer in a different location.

I have spent more time then I would have ever imagined doing all of this so I signed up here in search of help. I am not a pro so any and all help would be appreciated.

[IMG]http://i45.tinypic.com/20r440x.jpg[/IMG]

[FONT=monospace][/FONT]
My sudo fdisk -l is below.

[img]http://i45.tinypic.com/28vptl5.jpg[/img]

Thanks,
Alex

---

### Post by garvinrick4 on 2010-06-14
Do you have the install CD. If you do put it in and boot off of it. Go to gparted in System/Admin and open it. Right click on sda1 and choose label and make it lucid.
Then click the green arrow up on top to apply it. Close gparted.
 Go to applictions to accessories to terminal and open a terminal.

```
sudo mkdir /media/lucid

``````
sudo mount /dev/sda1 /media/lucid
```                          ```
sudo grub-install --recheck --root-directory=/media/lucid [/dev/sda]("file:///media/dev/sda") 
``````
sudo umount /media/lucid 
``` (not a typo)

We are doing this very quickly just to make sure that it has a mount point and the grub2 is installed correctly. First thing I always do and most of time is problem it seems.
Your mount point is /media/lucid and not media/and your UUID #, long #. Easier to deal with.
Restart and take disk out and let her boot up.

---

### Post by [AK]Zip on 2010-06-14
I will try that and report back.

---

### Post by [AK]Zip on 2010-06-14
Nope I still get the same error as before when booting without the CD.

First I did the label:
[IMG]http://i45.tinypic.com/bdrtyx.jpg[/IMG]

Then the rest:
[IMG]http://i45.tinypic.com/s6ujgk.jpg[/IMG]

Any other suggestions?

Thanks,
Alex

---

### Post by garvinrick4 on 2010-06-14
It said the same thing about not finding /dev/by UUID/784993928220j2j dropping to shell.

---

### Post by [AK]Zip on 2010-06-14
Yes exactly the same error as before as if nothing was ever done.

---

### Post by garvinrick4 on 2010-06-14
Has anyone seen the error posted in #1 at mounting? /dev/disk/by-UUID is missing.

---

### Post by [AK]Zip on 2010-06-14
If anyone else can make any suggestions I would appreciate it otherwise I will be forced to go to the dark side (Windows).

---

### Post by [AK]Zip on 2010-06-15
Anyone? I really don't want to go over to Windows for this.

---

### Post by [AK]Zip on 2010-06-16
I am running Windows 2008 Server, but I just remembered how much I hate this thing... :( I think I may try Fedora.

---

### Post by john newbuntu on 2010-06-16
You mentioned that you could eventually boot into Ubuntu.  Open a terminal and type:
```
sudo dpkg --configure -a
```I thought this bug was fixed a long time ago.  Anyway, here's the bug report:
[https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/358654](https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/358654)

If this does not work, you could try the suggestion in post#15 on the bug report with the proper initrd version (look at the /boot directory) or you could just say 'all' for the version without quotes.

---

### Post by [AK]Zip on 2010-06-16
Those are issues people are having after updating. I did a clean install and have the exact same issue. I tried everything I could find on that page you listed and still no go sadly.

---

### Post by [AK]Zip on 2010-06-16
I just downloaded the ubuntu iso from another location and burned on another computer. I will try and install again and hopefully this fixes it. If anything I may try an older version of Ubuntu.

---

### Post by [AK]Zip on 2010-06-16
Nope still the same problem. I guess I will try 9.1 now.

I have some additional memory and SCSI hdd on the way so I will try installing again on that once it comes in. If still no go I really do give up and probably back to windows 2008 server.

---

### Post by [AK]Zip on 2010-06-16
Ubuntu 9.10 installed and loaded just fine. Any suggestions on how to update to 10.04 without having the problem I had before?

---

### Post by [AK]Zip on 2010-06-21
I tired with different HDD's and memory and still the same issue. I guess it is some sort of compatibility issue with 10.04. I will stick with 9.1 for now.

---

