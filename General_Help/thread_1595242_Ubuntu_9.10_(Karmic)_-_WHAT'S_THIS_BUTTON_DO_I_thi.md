---
title: "Ubuntu 9.10 (Karmic) - WHAT'S THIS BUTTON DO??? I think I messed up....BIG time..."
date: 2010-10-13
forum: General Help
---

### Post by BCMusic on 2010-10-13
As you can see in the first screenshot, TestDisk shows that the partitions indeed exist, but GParted shows otherwise. They are named "Windows" and "Everything". All I need to do is recover those... I've used TestDisk to "write" the partition table, but when I restarted (as advised by TestDisk) that is when GParted shows that "sda" is "unallocated". In the second screenshot, "Disk Utility" also shows that they exist... They also appear in "Computer".[COLOR=DarkOrange] [COLOR=Blue]*If this is a mounting issue, I've already tried it*[/COLOR][/COLOR]... The error I get when trying to mount either one is:

*"[COLOR=Red]Error mounting: mount exited with exit code 21: fuse: mount failed: Device or resource busy[/COLOR]"*

AFAIK, neither one is "busy"... TestDisk is closed, GParted is closed, and Disk utility is closed. The only thing open is Firefox. I'm currently using the LiveCD...

[SIZE=1]P.S. - On a tiny, un-related side-note, grub is corrupt... "grub rescue" when I restart.... I tried to delete/uninstall Ubuntu, but I obviously did something wrong. Which probably has something to do with this whole damn situation... [/SIZE]](*,)](*,)

**[COLOR=Red]UPDATE: [COLOR=Black]The partitions labeled "Windows" and "Everything" are now accessible instead of giving the mount error, but still unable to boot into windows...[/COLOR][/COLOR]**

Please refer to my last post....

---

### Post by BCMusic on 2010-10-13
Bumping before it gets lost...

---

### Post by Swiftjay on 2010-10-13
> **BCMusic said:**
> Bumping before it gets lost...
You could've acidently mounted it.

in root do : mount

check where the device is then

umount /device -l

this will do a lazy mount and de-mount it regardless of what it's doing.

might wanna do an fsck on the hard drive too just to see it's alright you SHOULD only do this when it's umounted

fsck /dev/sda1  for example


try reboot see if it lets you boot into windows then if not leme know what happends.

---

### Post by BCMusic on 2010-10-13
Ok, doing the "mount" command, I get the following output:

```
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdc1 on /media/D014-DE55 type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdb1 on /media/Backup type fuseblk (rw,nosuid,nodev,allow_other,default_per
```

Restarting the computer brings me to "grub rescue". Then I have to Ctrl+Alt+Del to restart...

---

### Post by djchandler on 2010-10-13
I have a suggestion. Recover your GRUB first, then solve your mounting problem.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

You essentially have the same problem as if a Windows installation overwrote GRUB, Once you solve your GRUB issue, you should be able to boot into Windows and run chkdsk to check the integrity of the ntfs partitions.

Are you actually trying to completely remove Ubuntu of any other Linux installation and return this computer to Windows only?

---

### Post by BCMusic on 2010-10-13
> Are you actually trying to completely remove Ubuntu of any other Linux installation and return this computer to Windows only?Actually, that's pretty much what I want to do. Basically I'd like to "start over". I need my 2 partitions ("Windows" and "Everything") back though... If I fix Grub, will my partitions come back?

EDIT: I noticed that it says "...after installing Windows"... Does it matter if Windows was already installed before installing Ubuntu??

---

### Post by slooksterpsv on 2010-10-13
I hope I didn't miss anything else, but here's my suggestions, on what I've had to do in the past.

If it says that it's mounted or in use, be sure that you have all other windows closed, if needed mount it to /media then unmount it via:
sudo mount /dev/sda2 /media && sudo umount /media

I know sometimes if I've mounted something in Terminal and cd'ed into the directory, it won't let me do anything with the volume (like GParted, etc.) until I've cd / (cd'ed into the root) cause it detects when cd is in cd /media or cd /media/somedrive

---

### Post by djchandler on 2010-10-13
> **BCMusic said:**
> Actually, that's pretty much what I want to do. Basically I'd like to "start over". I need my 2 partitions ("Windows" and "Everything") back though... If I fix Grub, will my partitions come back?

EDIT: I noticed that it says "...after installing Windows"... Does it matter if Windows was already installed before installing Ubuntu??

If all you want to do is recover your Windows, you may not need to recover GRUB, although installing GRUB should search your disk and find your partitions properly, just as recovering NT boot loader or Vista boot loader should do this for ntfs only i.e, it won't recognize the Linux ext4 or swap partitions

If you read further down on that page, there is a method for recovering the Windows boot loader. Recovering Vista or 7 is different from recovering XP. So which version of Windows are you using? MS Technet has articles describing how to recover your boot loader. Somewhere else on this forum that has been discussed in the past, including posts I've made.

PS I'm going to bed (where I should have been hours ago).

---

### Post by BCMusic on 2010-10-13
I literally can't do anything with these partitions... I don't understand why they show up in TestDisk and Disk utility, but not GParted...

---

### Post by mastablasta on 2010-10-13
did you repair GRUB as it was suggested?

---

### Post by Swiftjay on 2010-10-13
> **BCMusic said:**
> I literally can't do anything with these partitions... I don't understand why they show up in TestDisk and Disk utility, but not GParted...
if you do sudo apt-get intall grub2 then reboot and try selecting your hard drive, is it still the same outcome?

---

### Post by BCMusic on 2010-10-13
> if you do sudo apt-get intall grub2 then reboot and try selecting your hard drive, is it still the same outcome?When I reboot after doing that, I get the following output:

```

GRUB loading
error: no such partition
grub rescue>

```
As previously mentioned, the partitions show up in Disk Utility and TestDisk, but not GParted.

---

### Post by Swiftjay on 2010-10-13
> **BCMusic said:**
> When I reboot after doing that, I get the following output:

```

GRUB loading
error: no such partition
grub rescue>

```As previously mentioned, the partitions show up in Disk Utility and TestDisk, but not GParted.


K as mentioned before try mounting the partition sudo mount /dev/sda2 /mnt

what does it still say the partition doesn't exist?

---

### Post by BCMusic on 2010-10-14
> **Swiftjay said:**
> K as mentioned before try mounting the partition sudo mount /dev/sda2 /mnt

Should I be mounting sda4 instead?

For some clarification on listed partitions in Disk Utility, I've attached a screenshot.

sda1 = Windows...
sda2 = Programs for Windows...
sda3 = I'm assuming a broken install of Ubuntu while trying to sort this stuff out...
sda4 = My ***original*** Ubuntu installation...
sda5 = Used by #4...
sda6 = Swap...

All of this started when I tried to resize a partition and move a partition using GParted... Can anyone explain why Disk Utility can see them, but not GParted??

---

### Post by BCMusic on 2010-10-14
Bumping from page 11...

---

### Post by Swiftjay on 2010-10-14
> **BCMusic said:**
> Bumping from page 11...
You said you wanted to access the files for windows partition, so no you don't want to mount sda4 you wanna mount sda2.

If sda2 mounts then you can easily set up the fstab to mount it at startup.

If sda2 mounts all you have to do is something simular to do this in fstab

/dev/sda2 /media/A2983E3E983E10F1              ntfs   

first make a directory where you want it to be mounted to so say in the media folder

so:

mkdir /media/Windows

Then in the fstab do:

You either have to do sudo vi /etc/fstab or be in root to edit it.  You might wanna try using vim as a editor though some people use nano as it's more user friendly.  I prefer vim.

you have to install vim first though so just do apt-get install vim

then vim /etc/fstab and just add this in there:

/dev/sda2 /media/Windows            ntfs    


However, that's if you can mount it first.  If you can't mount it, well there must be some problem wit hthe hard drive, i'd suggest doing a fsck on it.

Let me know if you can mount it first and we'll take it from there.

---

### Post by BCMusic on 2010-10-14
I don't need access to the files. All I want to do is get my Windows to boot again... My Windows partition has been mounted in /media ever since I restarted the LiveCD. Remember, sda1 is the Windows OS, and sda2 contains the program files for Windows... But since GRUB is corrupt (I'm assuming, since it brings me to the "rescue" prompt), I am unable to do that...

---

### Post by djchandler on 2010-10-15
What version of Windows are you trying to recover? You need your Windows installation CD or DVD to recover your Windows. How you proceed after booting your Windows installation disc depends on which version of Windows you are recovering, It looks to me like the MBR and the partition table needs to be rebuilt. If you don't have a Windows installation CD or DVD, you need the recovery discs from your computer manufacturer.

---

### Post by BCMusic on 2010-10-15
Okay, I really appreciate all the help you guys have given so far... But I did something to fix it that I think should be posted, as it would certainly help anyone else in my situation...
 
All of this started when I deleted/resized/moved a partition. After that, when I would restart my computer, I would be taken to the "grub rescue" prompt. Well, I booted back into the LiveCD, and re-installed grub. I found a thread (can't remember which one, it's on this site, maybe you guys can figure it out if you read a little further?) that gave instructions on how to repair grub, but I can't remember the steps given. It involved using a command that called for the mounting of the partition holding the Ubuntu OS. After that, a command was given that installed grub directly to the partition specified (in my case it was "/media/sda5")... Well, after that, I was finally able to select which OS to boot, so I selected Windows (XP). Once booted into Windows, I used a program called EASEUS Partition Master to delete all of the partitions along with their files except for "Windows" and "Everything (sda1 and sda2 respectively). So Ubuntu had finally been deleted :(. After that, I used a feature in Partition Master called "Rebuild MBR". Once I clicked that and applied, I was no longer seeing the "grub rescue" prompt, it would load straight to Windows!! Now, everything is back to normal (before installing Ubuntu) and I think I'm gonna give it another try... **Thanks again everyone!!**

---

