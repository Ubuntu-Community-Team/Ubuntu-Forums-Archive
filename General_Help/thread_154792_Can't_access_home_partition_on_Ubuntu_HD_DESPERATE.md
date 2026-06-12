---
title: "Can't access /home partition on Ubuntu HD *DESPERATE*"
date: 2006-04-03
forum: General Help
---

### Post by thespazzz on 2006-04-03
Hey guys,

I need some help bad.  I'm in the process of trying to reformat and reinstall Windows and Ubuntu.  The OS's have there own hard drives with Windows being on the Primary Master Drive and Ubuntu being on the Secondary Slave drive.

The method I was going to use was

1. copy all the files I needed from the Windows NTFS drive to the Ubuntu Drive.
2. Repartition and format the Windows Drive with NTFS and FAT32
3. Install Windows
4. Mount Ubuntu Drive in Knoppix (as the windows install killed grub) and copy the backup files to the FAT32 partition on the first hard drive.
5. Wipe the partition information from the second (Ubuntu) drive.
6. Install Ubuntu which configures Grub.
7. PARTY!

However Knoppix will not allow me to mount the ubuntu partition that contains my /home directory where the backup information is, thus leaving me stuck on step 4.

I tried following the information located at [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub)

But the Grub Installer can't find the nessisary files.

So now i've got all my important files trapped on the Ubuntu drive.   Can somebody please help me?

---

### Post by blackbeastofaarrgh on 2006-04-03
Try using the Ubuntu LiveCD. Those have always worked for me. The disk manager mounts disks fine on my end.

---

### Post by thespazzz on 2006-04-03
I booted using the LIVE cd and it did not mount the drives.

Unfortunatly due to the "well documented yet unsolved" screen resolution issue the live cd is near useless for me.

**EDIT UPDATE: I was able to find the disk manager in the Live CD.  It reads the disk in question as inaccessable.

---

### Post by testube_babies on 2006-04-04
Try this, it worked for me:

Boot from the normal Ubuntu installation CD.
When it prompts you to hit enter for a normal installation or type something in, type "rescue" and hit enter.

Follow the instructions until it gives you a terminal.

In the terminal, type "grub-install /dev/hda"

*I really don't know what damage this could potentially do to your system, all I know is that it reinstalled the grub menu for me after a Windows installation overwrote it.

EDIT:  never mind.  I'm an idiot and didn't realize that those were the instructions posted on the wiki.  Sorry.

---

### Post by thespazzz on 2006-04-04
Bump and more info.

Im convinced that when I installed Ubuntu the partitioner used LVM to setup my /home and /root partitions.  I can boot from the install CD in rescue mode and access the drive.

The listing I have using the rescue mode to boot the OS shell shows

/dev/hda1 <-- NTFS partition for windows on HDA
/dev/hda2 <-- FAT32 partition for windows on HDA
/dev/hdb1 <-- /boot partition for Ubuntu on HDB which I can access fine in Knoppix or LiveCD
/dev/hdb4 <-- Assuming this to be my /root partition on HDB
/dev/hdb5 <-- Assuming this to be my /home partition on HDB
/dev/ubuntu/ <--and below something to do with lvm?
/dev/ubuntu/root
/dev/ubuntu/home

Now I can select /dev/ubuntu/root and boot my os shell in rescue mode.
and I can also access /dev/ubuntu/home using the alternative shell and see all my files with a ls command.

So i'm assuming that if I can get my old Ubuntu install to boot I'll be able to access the files just as they were when I made the backups.  However all attempts to load GRUB have failed.

Or if someone can give me a quick and dirty way to copy these files from the rescue mode shell to /dev/hda2. That would accomplish what I need.

---

### Post by thespazzz on 2006-04-04
Final Bump... ISSUE SOLVED

I never did find out if this is an issue of LVM or not but if someone has this same issue later on you can try these steps.

1. Boot from the Ubuntu Installation CD

2. When prompted at Boot instead of pressing enter or typing server type, rescue then press enter.

3. Answer the questions and when prompted to select your root directory select the partition that contains your /home directory in a readable format.  In my case this was /dev/ubuntu/home.

4. You will then be told that there is no root file system on that partition and would you like use the default shell.  Select Yes.

5. You will then have a prompt.  Your /home directory will be mounted in /target.  The next thing to do is to create a mount point for the HD partition you want to move your files too.  In this case I had a fat32 partition on the first hard drive so the commands I entered were

mkdir /mnt
mkdir /mnt/fat32

6. Then mount the file system.
mount /dev/hda2 /mnt/fat32

7.  After this its a simple copy command.
cp -r /target/spazzz/backups /mnt/fat32/backups.

This will take some time depending on how many files you have and how large they are.  I went to the store and cameback about an hour later and it was done.

Restart.  Your files should now be safely i in the location you copied them.

---

### Post by Aliby on 2006-04-18
I have been using Ext2IFS which enables you to access (read & write) your ext3 partitions from windows. I am still a newb and used to find it invaluable to be able to edit fstab, grub config files from windows. I don't do so nearly as much anymore. Now I wold use it if I have some debs I have downloaded in windows and want to move them into Ubuntu for later.
[http://www.fs-driver.org/index.html]("http://www.fs-driver.org/index.html")

---

