---
title: "Western Digital 'My Book' External Hard Drive - Problem with Permissions (chmod)"
date: 2009-11-17
forum: General Help
---

### Post by Th3Professor on 2009-11-17
(Subject says it.) I'm unable to chmod - even with sudo or as root - the files/directories on the external drive. The odd thing is, I don't think it was like that just the other day (and I haven't made changes to settings (that I recollect))... Any idea how to chmod that rascal?
Thanks!

Update-
Here's the df -T...
```
/dev/sde1     vfat    932G  750G  183G  81% /media/My Book
```

---

### Post by Th3Professor on 2009-11-18
Holy cow, my post has already been buried under 3+ pages of posts. :(
I'm really hoping there's a way to do simple tasks like renaming files on the drive, right now permissions are set to 700 and I cannot change that... and I am unable to, even as root or sudo, change anything on the external drive other than add files or delete files.

---

### Post by Th3Professor on 2009-11-19
?

---

### Post by scouser73 on 2009-11-19
Here's what I usually do for changing file permissions.

**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your  folder/file/drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your folder/file/drive.

---

### Post by lavinog on 2009-11-19
I don't think you can use chmod on fat filesystems
How are you mounting the drive.
gvfs should automatically give you the permissions you need to access the files.

---

### Post by Th3Professor on 2009-11-19
> **lavinog said:**
> I don't think you can use chmod on fat filesystems
How are you mounting the drive.
gvfs should automatically give you the permissions you need to access the files.

It auto-mounts. And today it is actually *working*... letting me rename files/etc. Wow that is just weird. I don't like how it just up and decides to let me or not let me have control over it. grrrr

> **scouser73 said:**
> Here's what I usually do for changing file permissions.

**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your  folder/file/drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your folder/file/drive.

Cool beans. I'll go ahead and try that and in future situations where the external drive gets colicy/stubborn that'll, well, prevent the stubbornness of the hard drive.

---

### Post by hailholyghost on 2009-11-20
scouser73,

I tried that and it won't let me do it, even when I'm logged in as root and the computer says that I am the owner.

It's like I have a virus and I can't even write on my own external hard drive!!  ARRGGGH

I have no idea what caused this.

Are there any other possible solutions?

Thanks for your time!

---

### Post by warfacegod on 2009-11-20
> **hailholyghost said:**
> scouser73,

I tried that and it won't let me do it, even when I'm logged in as root and the computer says that I am the owner.

It's like I have a virus and I can't even write on my own external hard drive!!  ARRGGGH

I have no idea what caused this.

Are there any other possible solutions?

Thanks for your time!

Have you tried chown in terminal? 

sudo chown -R username:username /media/drivename

---

### Post by lavinog on 2009-11-20
chown chmod, and chgrp will not work on fat file systems.  It has more to do with the permissions set by mount, but could mean that there is a problem somewhere.
post the output of dmesg.
and post the output of mount.

mount gives me this for one of my flash drives:
```

/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

```
notice the rw, uid, and gid

---

### Post by P4man on 2009-11-20
I think lavinog is correct. And im guessing the problem only occurs or doesnt occur when another drive (or usb stick) is inserted, changing the drive order.

OP can you post the output of
```

cat /etc/fstab
```

?

---

### Post by hailholyghost on 2009-11-20
This is indeed strange! But misery loves company, I'm glad to see I'm not the only one with this problem!

> **P4man said:**
> I think lavinog is correct. And im guessing the problem only occurs or doesnt occur when another drive (or usb stick) is inserted, changing the drive order.

OP can you post the output of
```

cat /etc/fstab
```

?

david@david-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=dfbf4ba3-9c8e-4818-adb2-d7e4cf505872 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=8f87ecd3-a1b5-4cec-83d2-8fb8a3556a5c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

david@david-laptop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/david/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=david)
/dev/sdb1 on /media/SEA_DISK type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

The output from dmesg was too long for the terminal to display.  Is there any specific thing I should be looking for?

Thank you so much P4Man and lavinog, I really appreciate any help you can give!

---

### Post by lavinog on 2009-11-20
> **hailholyghost said:**
> 
[code]
/dev/sdb1 on /media/SEA_DISK type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
[code]
This looks right...were you having permissions problems with this drive?
Is there a switch on the drive to turn on write protect?

> 
The output from dmesg was too long for the terminal to display.  Is there any specific thing I should be looking for?

you could attach /var/log/dmesg instead.

---

### Post by hailholyghost on 2009-11-21
lavinog,

I am so confused....

david@david-laptop:~$ gksudo nautilus
Initializing nautilus-share extension

** (nautilus:7089): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** (totem:7140): DEBUG: Init of Python module
** (totem:7140): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:7140): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:7140): DEBUG: Creating Python plugin instance
** (totem:7140): DEBUG: Init of Python module
** (totem:7140): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:7140): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:7140): DEBUG: Creating Python plugin instance

** (totem:7140): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name
** Message: Error: Could not read from resource.
gstfilesrc.c(860): gst_file_src_create_read (): /GstPlayBin:play/GstFileSrc:source:
system error: Input/output error

** (totem:7140): DEBUG: Finalizing Python plugin instance
** (totem:7140): DEBUG: Finalizing Python plugin instance
pure virtual method called
terminate called without an active exception
** (totem:7160): DEBUG: Init of Python module
** (totem:7160): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:7160): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:7160): DEBUG: Creating Python plugin instance
** (totem:7160): DEBUG: Init of Python module
** (totem:7160): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:7160): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:7160): DEBUG: Creating Python plugin instance

** (totem:7160): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name
** Message: Error: Could not read from resource.
gstfilesrc.c(860): gst_file_src_create_read (): /GstPlayBin:play/GstFileSrc:source:
system error: Input/output error

** (totem:7160): DEBUG: Finalizing Python plugin instance
** (totem:7160): DEBUG: Finalizing Python plugin instance
** (totem:7172): DEBUG: Init of Python module
** (totem:7172): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:7172): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:7172): DEBUG: Creating Python plugin instance
** (totem:7172): DEBUG: Init of Python module
** (totem:7172): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:7172): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:7172): DEBUG: Creating Python plugin instance

** (totem:7172): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name
** (totem:7172): DEBUG: Finalizing Python plugin instance
** (totem:7172): DEBUG: Finalizing Python plugin instance
** Message: Error: Could not read from resource.
gstfilesrc.c(860): gst_file_src_create_read (): /GstPlayBin:play/GstFileSrc:source:
system error: Input/output error

** Message: Error: Could not read from resource.
gstfilesrc.c(860): gst_file_src_create_read (): /GstPlayBin:play/GstFileSrc:source:
system error: Input/output error


** (nautilus:7089): WARNING **: Couldn't open file:///media/SEA_DISK/Film%20Reserve/Fast%20Times: Could not read from resource.
** (totem:7205): DEBUG: Init of Python module
** (totem:7205): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:7205): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:7205): DEBUG: Creating Python plugin instance
** (totem:7205): DEBUG: Init of Python module
** (totem:7205): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:7205): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:7205): DEBUG: Creating Python plugin instance

** (totem:7205): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name
** (totem:7205): DEBUG: Finalizing Python plugin instance
** (totem:7205): DEBUG: Finalizing Python plugin instance

** (nautilus:7089): WARNING **: Hit unhandled case g-io-error-quark:21 in fm_report_error_setting_group

and then...

I tried /var/log/dmesg, but it told me I didn't have permission to do so, even after logging in as root.  I tried gksudo /var/log/dmesg, and it gave a new window "starting administrative application" I think, which shut down before I could see what was going on.  No output in the terminal was displayed.
I can find no button on the drive besides the power switch, lol.


Thanks much lavinog!

-I am Dazed and Confused....

---

### Post by P4man on 2009-11-21
> **hailholyghost said:**
> 

I tried /var/log/dmesg, but it told me I didn't have permission to do so, **even after logging in as root.  I** tried gksudo /var/log/dmesg, and it gave a new window "starting administrative application" I think, which shut down before I could see what was going on.  No output in the terminal was displayed.
I can find no button on the drive besides the power switch, lol.


You enabled root account?
One way or the other your system looks seriously messed up. Check your permissions and ownership of your home folder, but if you messed with permissions outside your home, I think a reinstall is the only real solution...

---

### Post by hailholyghost on 2009-11-21
I tried logging in as root with "su" and got "Authentication Failure".  I tried typing root in the terminal, to see what happened, and then I installed a program ROOT which I find has nothing to do with the permissions problems that have plagued this computer since installation about a year ago, on a 3 year old laptop.

I can't log in as root on my own computer!!!! 

so I booted through recovery mode and tried to edit sudoers (Case 2 in [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)) but I made some error when writing out a few lines to match what they had there, now I can't access the file anymore, whether booting from recovery or normal mode.

This is so confusing!

It's so ridiculous that I can't even do this with my own computer!

I'm wondering what the pluses and minuses of upgrading to 9.10 are, I don't know if its a good idea or if it will fix this or not.  I just hope the weapon of last resort (complete re-installation) isn't necessary.

-In desperate need of help!

-Much appreciated:)

---

### Post by P4man on 2009-11-21
> **hailholyghost said:**
> 

I can't log in as root on my own computer!!!! 

This is so confusing!

It's so ridiculous that I can't even do this with my own compute

Not at all. You just proved why sudo is a good policy.
Here is some reading for you:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If the problem is permissions of your home folder, open a terminal and type
```
sudo chown -R user:user /home/user
sudo chmod -R 644 /home/user
```
replace user with your own username

If you messed up permissions outside that, then I got no idea.

---

### Post by lavinog on 2009-11-22
> **hailholyghost said:**
> lavinog,

I am so confused....


press alt-f2
type /var/log and hit run.
Nautilus should open that folder.
find dmesg, right-click it and select compress.
in the compress window select an archive format such as .zip or .tar.gz
set the location to your home folder.

now attach the archive you just created.

---

### Post by hailholyghost on 2009-11-23
This is very strange.

This permissions problem only starts halfway through transferring files to the external hard drive.  I can find no reason for this.

I've attached the dmesg.tar.gz file.

I hope to be doing computational chemistry with this computer (AMBER, CHARMM, etc)

On a side note, these forums are great.  Don't know where I'd be without you lavinog!

Muchas gracias!!!

---

### Post by lavinog on 2009-11-23
I was gave you the wrong info.
it was /var/log/messages
which has the same info as the command dmesg...so if you can post the messages file instead...sorry.

---

### Post by lavinog on 2009-11-23
I wonder if this has anything to do with your problem:
```
[    2.860231] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
```
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/296710](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/296710)

I also noticed that you are using an intrepid kernel:
```
[    0.000000] Linux version 2.6.27-15-generic (buildd@vernadsky) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Oct 20 06:52:09 UTC 2009 (Ubuntu 2.6.27-15.43-generic)
```
I had problems with usb devices in Intrepid.
You may want to consider upgrading...If not try the karmic live cd and see if the problem still exists.

edit:  If you are not using intrepid, it may be that grub is loading the wrong kernel.

---

### Post by hailholyghost on 2009-11-24
Yeah, my root system is really screwed... I tried 

"sudo aptitude update && sudo aptitude safe-upgrade && sudo aptitude full-upgrade" 

to get the system on Karmic Koala, but got ">>> sudoers file: syntax error, line 19 <<<
sudo: parse error in /etc/sudoers near line 19"
 in the sudoers file.

How can I edit this file to correct the mistake?  I can't even get into it.

Nor can I upgrade, the update manager will not show upgrade to another system, presumably b/c I am not root.

I read the thread you posted, couldn't find a fix there, maybe I missed it.  I saw the "Fix Released" link, which just offered a chance to comment.

Again, I really appreciate your time lavinog!

---

### Post by lavinog on 2009-11-25
```
gksudo update-manager --dist-upgrade
```

---

### Post by Bernard_ivo on 2010-01-12
Dear all, 
I've just bought new WD My Passport Studio HD. It is formated for MAC use -hfsplus. I do have problem with permissions as I can't write on it. I assume that being MAC formated may be a problem (planning to reformat it). But can I change the permissions without formating to extXXX or NTFS? gksudo nautilus did not work for me. Any suggestions?
mount output:
/dev/sdc3 on /media/My Passport type hfsplus (rw,nosuid,nodev,uhelper=hal)

Ubuntu 9.04 - Jaunty Jackalope

Issue fixed by formatting to ext3 - though I lost 23 GiB and current free space decreased to 434 GiB. Probably no way to fix this.

Thanks

---

### Post by scouser73 on 2010-01-12
Hi Bernard, try to reformat it to NTFS using Gparted, if you manage to do that without a problem then the space on your drive should read 465.7Gb, [*assuming that it's a 500Gb HDD*].  NTFS doesn't take up a vast quantity of space like other file systems.

---

### Post by Bernard_ivo on 2010-01-12
Thanks, that is what I've just done - only 79MB used. Though I wanted to use Linux file-system :)
Problem solved: formated to ext4 then using tune2fs -m 1 /dev/sdc[number where the HDD is mounted] decreased the reserved blocks to only 1%

Cheers

---

