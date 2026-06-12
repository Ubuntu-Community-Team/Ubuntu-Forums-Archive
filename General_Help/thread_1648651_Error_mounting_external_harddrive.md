---
title: "Error mounting external harddrive"
date: 2010-12-19
forum: General Help
---

### Post by andrecamp on 2010-12-19
Hi,

Whenever I plug in my external harddrive and try to access it i get the following error. 
> 
**Unable to mount Iomega HDD**

DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

Please help, because I need to access my data.

---

### Post by lmarmisa on 2010-12-19
> **andrecamp said:**
> Hi,

Whenever I plug in my external harddrive and try to access it i get the following error. 


Please help, because I need to access my data.

Disconnect your external hard drive, open a terminal, type this command and post its output:

```

ls -l /media

```

---

### Post by andrecamp on 2010-12-19
This is the output I get.

> total 8
drwxr-xr-x 2 root root 4096 2010-12-19 04:01 external
drwx------ 2 root root 4096 2010-12-19 13:51 Iomega HDD


---

### Post by lmarmisa on 2010-12-19
There are two directories created. Do you have more USB devices plugged?. Did you create manually any of these directories?. If not, these directories (or at least one of them) could be the reason you are not able to mount your USB drive.

I would like to check a last point. So, please post the outputs of these commands (no USB external device connected, please):

```

ls -la /media
ls -l /media/external
ls -l "/media/Iomega HDD"
cat /etc/fstab
cat /etc/mtab

```Kind regards,

Luis

---

### Post by andrecamp on 2010-12-19
Thanks for the reply. The outputs are below. 

ls -la /media
> total 16
drwxr-xr-x  4 root root 4096 2010-12-19 20:32 .
drwxr-xr-x 22 root root 4096 2010-12-19 03:51 ..
drwxr-xr-x  2 root root 4096 2010-12-19 04:01 external
drwx------  2 root root 4096 2010-12-19 20:32 Iomega HDD


ls -l /media/external
> total 0



ls -l "/media/Iomega HDD"
> ls: cannot open directory /media/Iomega HDD: Permission denied


cat /etc/fstab
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=9e15243b-4d42-4dc1-9ddc-f599de4b4b45 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8d819984-1558-49a7-8f65-4e70d1a49ab4 none            swap    sw              0       0


cat /etc/mtab
> /dev/sda1 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/andre/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=andre 0 0


---

### Post by lmarmisa on 2010-12-19
Did you create manually any of the directories **external** or **Iomega HDD**?

Are you sure no external USB storage device is connected to your system?.

---

### Post by lmarmisa on 2010-12-19
If you did not create those directories, I recommend to delete them.

Type these commands:

```

sudo rm -rf /media/external
sudo rm -rf /media/I*

```Reboot your system and check if the problem is solved.

---

### Post by andrecamp on 2010-12-19
I restarted my computer and I didn't turn of the external during the reboot. Then right before Ubuntu's loading screen came up, a whole bunch of black lines saying stuff like dev/sdb corrupt and stuff like that.

I am now back in Ubuntu and I can't open up the external. I go into Disk Utility. I see the harddrive listed there though. I can safely remove it. But oddly, it doesn't recoginze the file system on the harddrive which is supposed to be NTFS.

And in regards to the previous comment. I did create the folder /external/ and I tried to force mount the harddrive to that folder.

---

### Post by lmarmisa on 2010-12-19
> **andrecamp said:**
> I restarted my computer and I didn't turn of the external during the reboot. Then right before Ubuntu's loading screen came up, a whole bunch of black lines saying stuff like dev/sdb corrupt and stuff like that.

I am now back in Ubuntu and I can't open up the external. I go into Disk Utility. I see the harddrive listed there though. I can safely remove it. But oddly, it doesn't recoginze the file system on the harddrive which is supposed to be NTFS.

And in regards to the previous comment. I did create the folder /external/ and I tried to force mount the harddrive to that folder.

I suppose you typed the two commands I recommended. I suppose you typed these commands with no external HD plugged. Please, confirm these details.

I would like to know if the booting process of Ubuntu is normal now.

---

### Post by andrecamp on 2010-12-19
I typed the commands with the harddrive plugged in. And I restarded my computer and plugged it in after the restart and had it plugged in during the restart and nothing helped.

---

### Post by lmarmisa on 2010-12-19
> **andrecamp said:**
> I typed the commands with the harddrive plugged in.

Hmmm. I hope your external drive was not really mounted while you typed the commands and you did not delete your data.

I tried to advise you in order to type the different commands with no external HD plugged in.

I apologize if I confused you in any way.

I recommend to boot your system normally and then plug in your external drive. Why?. Because if the MBR of the external drive has some loader in its [Master Boot Record]("http://en.wikipedia.org/wiki/Master_boot_record") area, you could have a bad start of your system.

Could you send me the output of this command with your external HD pluggged in?

```

mount

```

---

### Post by andrecamp on 2010-12-20
I really appreciate your help so far. Thanks. And the output is below.

> /dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/andre/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=andre)
/dev/sdb1 on /media/Lexar type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


---

### Post by lmarmisa on 2010-12-20
An external hard drive is mounted now. This is a vfat file system.

This hard drive is mounted in [B]/media/Lexar
[/B]
Please, type this command:

```

ls -l /media/Lexar

```

---

### Post by andrecamp on 2010-12-20
The Lexar is a USB stick I had inserted in. Sorry if that made things a little more confusing. The harddrive is the IOMega.

---

### Post by andrecamp on 2010-12-20
And here's the output with no other input devices besides the external harddrive. 

> /dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/andre/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=andre)


---

### Post by lmarmisa on 2010-12-20
> **andrecamp said:**
> And here's the output with no other input devices besides the external harddrive.

The IOmega drive is not mounted at the moment.

Could you post the contents of the folder /media?

```

ls -la /media

```Do you know if you have installed the program gparted?.

Type this command to install it:

```

sudo apt-get install gparted

```

---

### Post by andrecamp on 2010-12-20
This is the output. And, I have GParted installed.

> total 12
drwxr-xr-x  3 root root 4096 2010-12-20 05:44 .
drwxr-xr-x 22 root root 4096 2010-12-19 03:51 ..
drwx------  2 root root 4096 2010-12-20 05:31 Iomega HDD


---

### Post by lmarmisa on 2010-12-20
Open GParted and select the device /dev/sdb.

Tell me if something is shown or try to post a capture of the window.

---

### Post by andrecamp on 2010-12-20
I've posted the screen shot here.

---

### Post by lmarmisa on 2010-12-20
I see a red icon showing some kind of problem. Do you read some text warning associated to this icon?.

Type this command too:

```

lsusb

```

---

### Post by andrecamp on 2010-12-20
The error associated with the red icon is posted.

The output to that command is. 

> Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:0083 Microsoft Corp. Basic Optical Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0930:0508 Toshiba Corp. Integrated Bluetooth HCI
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 059b:0370 Iomega Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


---

### Post by lmarmisa on 2010-12-20
I see a similar situation to that of your first post.

Do you see any change?. What about the previous message?.

```
**Unable to mount Iomega HDD**

DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

```

Is your system showing this message now?.

---

### Post by andrecamp on 2010-12-20
Now when I tried to mount it using Disk Utility, this is the error I get now.

---

### Post by andrecamp on 2010-12-20
Interestingly, I found this article telling me how to force mount.
So I tried it. This is the output so far... I just wonder how long this will take....

> 
andre@andre-Satellite-P200:~$ sudo mkdir /media/windows
andre@andre-Satellite-P200:~$ sudo mount /dev/sdb1 /media/windows -o force
Did not find any restart pages in $LogFile and it was not empty.
The file system wasn't safely closed on Windows. Fixing.
^C 

---

### Post by lmarmisa on 2010-12-20
OK. I would like to repeat the attempt to delete the folder "/media/Iomega HD" but step by step.

Please, shutdown the system. Then unplug the Iomega hard drive.

Start again your system and type this command:

```

ls -la /media

```

I would like to check if the dir IomegaHD is still there.

Do not plug again your hard drive until I say it.

---

### Post by andrecamp on 2010-12-20
I did what you said. The only thing there is the windows directory I made. 

> total 12
drwxr-xr-x  3 root root 4096 2010-12-20 06:24 .
drwxr-xr-x 22 root root 4096 2010-12-19 03:51 ..
drwxr-xr-x  2 root root 4096 2010-12-20 06:24 windows


---

### Post by andrecamp on 2010-12-20
So the problem is solved... I got referred to TestDisk. And its great. I am currently backing up the information from my external harddrive. 

I just followed these instructions.
[http://www.cgsecurity.org/wiki/OS_Notes#Linux_and_48-bit_LBA](http://www.cgsecurity.org/wiki/OS_Notes#Linux_and_48-bit_LBA)

Then after I used TestDisk to go into my harddrive and copy the folders to my laptop. Now, after I back up my information, I can go in and format the harddrive.

---

