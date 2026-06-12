---
title: "Few Problems"
date: 2006-04-30
forum: General Help
---

### Post by HiJinks on 2006-04-30
Im very new to linux and <3 ubuntu, but I have a few problems, maybe you can tell me what to do or point me in the right direction.

Major Problems:
I have my pc setup as follows:
2 Harddrives, both 80gb.
The first one is split into two partitions, 50 gig for windows, 27ish for linux.
My second harddrive has all my apps on it,(music/games/movies etc.) and I run them from windows. How do I get some games/music from harddrive 2, to the linux partition?

Ubuntu detects ati as my gfx card, but it doesnt detect what type, it just says unknown device. I have a x800xl

Ubuntu detects my sound card perfectly (sound blaster LIVE! 5.1) but I have no sound.

Those are the only major issues that I need help with asap.
The rest of my issues I can go without but it would be nice If I got help with them.

Minor Problems:
Not really a problem but How do I change the UI around, are there any special apps?

I installed frostwire but everytime I select it from the applications>internet box it does nothing.

thanks for all the help =D

---

### Post by rado_london on 2006-04-30
Hi.
I only can help with getting the apps/music stuff. But I need some info about the partition you use for the hard drive. Is it ntfs or fat32?

---

### Post by TLE on 2006-04-30
[QUOTE=HiJinks]How do I get some games/music from harddrive 2, to the linux partition?[/QUOTE]
I asuming!(Since your post doesn't actully say so) that you mean that you have Windows(NTFS) partitions and you want to know how you get acces to them while in linux. This is described in the starter guide. Press the help button in GNOME (it's the live preserver thingy) and press the "Ubuntu 5.10 starter guide" now there should be a menu in the left, here find "Mounting Windows partitions", it might be under partitions or Windows or something like that, look a little around, there is a lot of good stuff there. Anyway it's also [here]("http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only")

[QUOTE=HiJinks]Ubuntu detects ati as my gfx card, but it doesnt detect what type, it just says unknown device. I have a x800xl[/QUOTE]
Is it a problem? I mean of course it's a little troubeling but if the card does what it is supposed to ?! Try and check if hardware acceleration works, type:
```
fglrxinfo
```
It should say ATI...something, if it says MESA anywhere there then you don't have Hardware3D acceleration. If that's the case there is a howto to fix that [here]("http://www.ubuntuforums.org/showthread.php?t=75378")

[QUOTE=HiJinks]Ubuntu detects my sound card perfectly (sound blaster LIVE! 5.1) but I have no sound.[/QUOTE]
Well if it just does do not work at all you'll probably have to do some trouble shooting, you could try and change the sound system in System/Preferences/Multimedia System Selector to something else (ALSA or ESD or one of the other ones) to see if that works, otherwise post back here.

[QUOTE=HiJinks]Not really a problem but How do I change the UI around, are there any special apps?[/QUOTE]I'm just not sure what you mean, how to change themes on the desktop ?
Regards TLE

Oh, by the way, as the [Guidelines]("http://www.ubuntuforums.org/index.php?page=policy") say, you'll probably get a lot more respons if you make the title of your post more descriptive ;)

---

### Post by HiJinks on 2006-04-30
> I asuming!(Since your post doesn't actully say so) that you mean that you have Windows(NTFS) partitions and you want to know how you get acces to them while in linux. This is described in the starter guide. Press the help button in GNOME (it's the live preserver thingy) and press the "Ubuntu 5.10 starter guide" now there should be a menu in the left, here find "Mounting Windows partitions", it might be under partitions or Windows or something like that, look a little around, there is a lot of good stuff there. Anyway it's also here
mount: /dev/hdb1 already mounted or /media/windows/ busy
mount: according to mtab, /dev/hdb1 is mounted on /media/hdb1

is what I get when I try mounting my second harddrive, I checked in media/hdb1 and it won't let me access D: . Yes it is ntfs 

> It should say ATI...something, if it says MESA anywhere there then you don't have Hardware3D acceleration. If that's the case there is a howto to fix that here
My graphics come up as mesa and Im going to do what it says in the page you linked me.
edit: I configured it, went through all the menus, I have done this before and rebooted, it still comes up as mesa :(
> 
Well if it just does do not work at all you'll probably have to do some trouble shooting, you could try and change the sound system in System/Preferences/Multimedia System Selector to something else (ALSA or ESD or one of the other ones) to see if that works, otherwise post back here.
I tried all the things in multimedia system selector, 2 give me errors, the other 2 (ALSA/ESD) dont make any sounds when I hit test.

> I'm just not sure what you mean, how to change themes on the desktop ?
Yes pretty much the themes on my desktop :p

> Oh, by the way, as the Guidelines say, you'll probably get a lot more respons if you make the title of your post more descriptive
sorry for not reading the guidelines ](*,)

---

### Post by TLE on 2006-05-01
About Windows partitions, could you post the output of the df command and the contents of your fstab```
df
cat /etc/fstab
```

Graphics card: You say you configured it, did you do a full re-install the way the howto says, also remember to update your package sources first```
sudo apt-get update
```. I'm only asking because I **know** that howto has helped a lot of other people, myself included, btw I have the exact same graphics card !

I'm a little lost on the sound issue. But you try and have a look to see if this thread helps: [http://www.ubuntuforums.org/showthread.php?t=26567&highlight=multiple+sound]("http://www.ubuntuforums.org/showthread.php?t=26567&highlight=multiple+sound")
I noticed there was something there about that a single device could look the card, something which could be troubleshoot by doing ```
killall esd
``` and then trying to start a sound application. But try a read and see if there is something there that'll work for you.

About themes and other eyecandy have a look at this thread:
[http://www.ubuntuforums.org/showthread.php?t=87481]("http://www.ubuntuforums.org/showthread.php?t=87481")
in there is a link to the Breezy costumization guide. In that look under eye-candy. I think you'll particularly enjoy:
[http://doc.gwos.org/index.php/Desktop_EyeCandy]("http://doc.gwos.org/index.php/Desktop_EyeCandy")

Hope some of it helps

---

### Post by HiJinks on 2006-05-01
My sound works now thanks a ton!

heres the output from those 2 commands:

mike@home-443447a10f:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda2             26178104   2841968  22006356  12% /
tmpfs                   518220         0    518220   0% /dev/shm
tmpfs                   518220     12644    505576   3% /lib/modules/2.6.12-10-k7/volatile
/dev/hda1             51552552   9871284  41681268  20% /media/hda1
/dev/hdb1             78140128  35186676  42953452  46% /media/hdb1
mike@home-443447a10f:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hdb1       /media/hdb1     ntfs    defaults        0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Ill relook that video howto and the system eye candy later :D
edit: my video works now also just need mount and im set :p

---

### Post by TLE on 2006-05-01
[QUOTE=HiJinks]My sound works now thanks a ton![/QUOTE]
Great, your welcome
[QUOTE=HiJinks]
heres the output from those 2 commands:

mike@home-443447a10f:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda2             26178104   2841968  22006356  12% /
tmpfs                   518220         0    518220   0% /dev/shm
tmpfs                   518220     12644    505576   3% /lib/modules/2.6.12-10-k7/volatile
/dev/hda1             51552552   9871284  41681268  20% /media/hda1
/dev/hdb1             78140128  35186676  42953452  46% /media/hdb1
mike@home-443447a10f:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hdb1       /media/hdb1     ntfs    defaults        0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
[/QUOTE]
Yeah that looks about fine so it should be mounted on boot-up. It might be a permission problem. You can chech that by trying to see if you can get acces to those directories as root. Ok if you are familiar with Midnight Commander do
```
sudo mc
```
now enter your root code and try to manoeuvre to the mount point and see if you can get acces. If that's the case we know what the problem is and can try and fix it so the permission are rigth at boot-up.

---

### Post by HiJinks on 2006-05-01
I never used mc before and the command isn't found O_o

but I look in the properties of the drive and it says I'm not the file owner so I'm guessing it is a permission problem

---

### Post by PaulL on 2006-05-01
What does the line in /etc/fstab say about the Windows partition. It sounds like you don't have it set as in the guide (look for 0222 in the line). If this is not the case only root will be able to see the files. It probably says it is already mounted because it is - you are not allowed to see the files as an normal user.

---

### Post by PaulL on 2006-05-01
Sorry I see you have posted the relevant lines, but I'm sure thats the problem: here's a line from my fstab (change the sdb3 to whatever your drive is, and the slow_scsi to whatever you mount the partition as

/dev/sdb3       /slow_scsi      ntfs    nls=utf8,umask=0222 0       0

---

### Post by HiJinks on 2006-05-01
sudo mount /dev/hdb1 /media/windows/ ntfs nls=utf8,umask=0222 0 0

is what I put in and it still aint working, do I have to reboot?

---

### Post by TLE on 2006-05-01
No don't bother trying to mount it manually, you should change it in the fstab configuration file (That way it'll mount automaticaly when you boot, so when we're done just reboot and it should work). It is located in at /etc/fstab, so do the following (But be carefull this is a system configuration file). So first lets make a backup
```
sudo cp /etc/fstab /etc/fstab_backup05022006
```
then edit the file
```
sudo gedit /etc/fstab
```
Then change the apropriate line the way PaulL outlined, save it and reboot. By the way, the second  collum is the mount point, that's the:
```
/media/hda1
/media/hdb1
```
You don't have to change them (I can see that you wrote something about /media/windows before), but if you do! you must create this folder and change it's permissions so your normal user have acces to it.

EDIT: Oh by the way. We may have to change the permissions of those original folders also. So if you make the changes and it still doesn't work, don't worry then we just need to unmount it and change the permissions once, and then we're set.

---

### Post by HiJinks on 2006-05-01
okay it worked thanks alot =D

---

