---
title: "Mapping Local Share"
date: 2010-05-25
forum: General Help
---

### Post by DMustaine on 2010-05-25
Hello, I apologize if this should be in the "networking" forum, but everything I saw there is about getting a network working...

Hopefully I'll give enough information here, I am trying to map a local network drive permanently at each log on.

I have read the following pages:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read)
[http://ubuntuforums.org/showthread.php?t=162439](http://ubuntuforums.org/showthread.php?t=162439)
[http://ubuntuforums.org/showthread.php?t=784734](http://ubuntuforums.org/showthread.php?t=784734)
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

I am a Windows professional in the IT industry, but sadly I can't get this working. I am new to Ubuntu, I've been playing with a portable USB with persistence for a few months, and set up a dual boot with XP on my Dell Vostoro 1510 finally last week.

I'm running 9.10, and recently did all updates except going to the next version (it was hard enough getting everything going on this Dell I didn't want to risk my install).

I have a Lacie NAS drive locally, let's say the address is "10.10.10.100". There is a share on it let's say called "share01". There is a password let's say it is "password".

I am connected with a Broadcom Corporation BCM4312, and I can boot and be connected a few seconds after (I don't have a wired option)...

Following the instructions I have noted I can't get it to work. I am guessing since I don't get connectivity until after my desktop is up the script to map the drive can't see anything (until the wireless is up).

To make it funky, I can open a playlist in Rhythmbox, it asks for my sudo password, then bam I have the drive mapped, and it plays.

Any simple walk-through's  would be greatly appreciated. I am totally new to this environment, but for the past few months have made everything work with some searching; hence my committal to a full on live environment instead of the USB.

My goal is to have the mapped drive on the desktop, and under "places" as I will be storing all my documents there for both OS's.

Thank you, and I will gladly offer any information that is needed to resolve this.

---

### Post by DMustaine on 2010-05-25
Bump, WOW, 30 minutes later and on the second page... didn't know this forum was this fluid.

---

### Post by DMustaine on 2010-05-26
Anyone got an idea?

---

### Post by Morbius1 on 2010-05-26
Do you have an entry in fstab that you are using to mount the remote share or are you using a script somewhere.

Post the line that you using and maybe it's that. 

If it's in fstab then there is a problem with the new accelerated boot process where fstab is being executed before the network is up. If you use the following command in a terminal can you access the remote share:

```
sudo mount -a
```

---

### Post by Morbius1 on 2010-05-26
If it's an fstab entry you could try this approach: [http://ubuntuforums.org/showthread.php?p=9346192#post9346192](http://ubuntuforums.org/showthread.php?p=9346192#post9346192)

---

### Post by bodhi.zazen on 2010-05-26
> **DMustaine said:**
> Hello, I apologize if this should be in the "networking" forum, but everything I saw there is about getting a network working...

Hopefully I'll give enough information here, I am trying to map a local network drive permanently at each log on.

I have read the following pages:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read)
[http://ubuntuforums.org/showthread.php?t=162439](http://ubuntuforums.org/showthread.php?t=162439)
[http://ubuntuforums.org/showthread.php?t=784734](http://ubuntuforums.org/showthread.php?t=784734)
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

I am a Windows professional in the IT industry, but sadly I can't get this working. I am new to Ubuntu, I've been playing with a portable USB with persistence for a few months, and set up a dual boot with XP on my Dell Vostoro 1510 finally last week.

I'm running 9.10, and recently did all updates except going to the next version (it was hard enough getting everything going on this Dell I didn't want to risk my install).

I have a Lacie NAS drive locally, let's say the address is "10.10.10.100". There is a share on it let's say called "share01". There is a password let's say it is "password".

I am connected with a Broadcom Corporation BCM4312, and I can boot and be connected a few seconds after (I don't have a wired option)...

Following the instructions I have noted I can't get it to work. I am guessing since I don't get connectivity until after my desktop is up the script to map the drive can't see anything (until the wireless is up).

To make it funky, I can open a playlist in Rhythmbox, it asks for my sudo password, then bam I have the drive mapped, and it plays.

Any simple walk-through's  would be greatly appreciated. I am totally new to this environment, but for the past few months have made everything work with some searching; hence my committal to a full on live environment instead of the USB.

My goal is to have the mapped drive on the desktop, and under "places" as I will be storing all my documents there for both OS's.

Thank you, and I will gladly offer any information that is needed to resolve this.

Honestly, it is not all that difficult. Linux uses fstab to "map" network shares (the terminology is a bit different in Linux).

What entry are you using for fstab ?

Is your mount working ? Can you mount the share from nautilus and / or the command line ?

```
sudo mount -t cifs //10.10.10.100/share01 /media/share01 -o username=xxx
```

Where "xxx" is the user name used for the share (typically a log in name).

You should be asked for a password. You may need to make the mount point first :

```
sudo mkdir /media/share01
```

---

### Post by DMustaine on 2010-05-29
Thanks for the replies!!!


fstab has the following entries (hidden info for security)
```

sw              0       0
//10.x.x.x/xxx1  /media/xxx1  cifs  defaults,uid=1000,gid=1000,credentials=~/.smbpasswd,umask=777  0  0

```When I try
```

sudo mount -a

```I get the following:
```
mount: wrong fs type, bad option, bad superblock on //10.x.x.x/xxx1,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

> Is your mount working ? Can you mount the share from nautilus and / or the command line ?

```
sudo mount -t cifs //10.10.10.100/share01 /media/share01 -o username=xxx
```Where "xxx" is the user name used for the share (typically a log in name).

You should be asked for a password. You may need to make the mount point first :```
sudo mkdir /media/xxx1
```
No, when trying mount -t cifs I get the following error:
```
mount: block device //10.x.x.x/xxxx1 is write-protected, mounting read-only
mount: cannot mount block device //10.x.x.x/xxx1 read-only
```It's perplexing... like I emntioned I open the music player and voila, asks me for password and mounts the drive, but until then I'm stuck.



Again, THANK you for the replies and suggestions, I'm trying best I can, but have had a few long days... I'll be back at it hard soon.

---

### Post by bodhi.zazen on 2010-05-29
In this line :

//10.x.x.x/xxx1  /media/xxx1  cifs  defaults,uid=1000,gid=1000,credentials=~/.smbpasswd,umask=777  0  0

1. Remove "defaults"
2. Add users.
3. Use the full path to credentials.
4. Add noperm

> //10.x.x.x/xxx1  /media/xxx1  cifs users,uid=1000,gid=1000,credentials=/home/user/.smbpasswd,umask=777,noperm  0  0

From there watch the syntax and permissions of your credentials file.

---

### Post by DMustaine on 2010-06-16
Don't know how or why, or what i did different... I did a fresh install on a new hard drive, and not only did my Broadcom wireless work right away, but I mapped the drive, and not I can just click on it in "places" and viola, there every time.

Thanks for all the help everyone, I think something must have been funky in my last install (it was from a USB "live" install of Ubuntu).

---

