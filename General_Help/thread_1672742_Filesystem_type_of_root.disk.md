---
title: "Filesystem type of root.disk"
date: 2011-01-21
forum: General Help
---

### Post by anand1298 on 2011-01-21
Hi,

I have been doing the, "**How can I access my Wubi install and repair my install if it won't boot?**" ([https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?)) and i was executing the command:
[B]
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk[/B]

After typing this command in my terminal, i get a message as, "**mount: you must specify the filesystem type**"... I know we must specify the filesystem type using '**-t**' but what is the filesystem type of root.disk???

---

### Post by psusi on 2011-01-21
Depends on what you chose when you installed.  Probably ext4.

---

### Post by Rubi1200 on 2011-01-21
Can I suggest something?

There is a whole thread devoted to Wubi issues and solutions:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

If you need more help, let me know.

---

### Post by baliganikhil on 2011-01-21
Yeah most likely ext4.

Give the following command: cat /etc/fstab

---

### Post by bcbc on 2011-01-21
> **anand1298 said:**
> Hi,

I have been doing the, "**How can I access my Wubi install and repair my install if it won't boot?**" ([https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?)) and i was executing the command:
[B]
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk[/B]

After typing this command in my terminal, i get a message as, "**mount: you must specify the filesystem type**"... I know we must specify the filesystem type using '**-t**' but what is the filesystem type of root.disk???
You don't normally need to specify the type. Make sure you're using an Ubuntu live CD that supports ext4 (9.10 or later) and you might need to fsck the root.disk.

Note wubi has a 2 part install - the windows part doesn't install Ubuntu on the root.disk - so if you've never actually booted Ubuntu and seen the Ubuntu install (slideshow) then the root.disk is uninitialized and unmountable.

---

### Post by anand1298 on 2011-01-22
okay... This is what i did... I had 9.04 previously... I installed it by using "Install inside windows" option... I had it working for more than 6 months... Then i found out that 10.10 was released and i downloaded it... Burned it to a CD... I uninstalled 9.04 and installed 10.10, again by choosing "Install inside windows" option... Now, i clicked "reboot now" option... And when i click "Ubuntu" in my boot screen menu, it comes as "No wubildr" and "cannot find GRLDR"... I searched for it in google and i found the site i previously mentioned... And while trying to mount "root.disk", that filesystem type error came... What must i do now??? Now, even if i uninstall 10.10 and install 9.04 again, the same error comes... Any help???

---

### Post by bcbc on 2011-01-22
That error indicates that grub4dos can't find the wubildr file, which has to be in the root of one of your partitions. If it can't find it, it could be due to an excessively fragmented drive.
So first check that the c:\wubildr file exists.
Then try defragmenting (a good idea anyway prior to installing wubi).

Then try booting Ubuntu again.

PS: I also read that there was an issue with reading a wubildr file that is > 137GB from the start of the partition (I believe it was a BIOS limitation, not grub4dos).

---

### Post by anand1298 on 2011-01-23
Thanks for the tip bcbc... What i did was, i copied the two files, wubildr and wubildr.mbr, to all my partitions and booted into ubuntu... My ubuntu successfully installed... :)

---

### Post by bcbc on 2011-01-23
Good to hear. Enjoy!

---

