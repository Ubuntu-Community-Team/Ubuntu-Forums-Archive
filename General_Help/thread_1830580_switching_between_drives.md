---
title: "switching between drives"
date: 2011-08-21
forum: General Help
---

### Post by spec36 on 2011-08-21
First let me advise I am using xbmc live, which is a cut down version of Ubuntu for media stores.

Lets say I have two drives in my ubuntu (xbmc) system, drive C and D. How do I switch between these drives in the shell? I think I go to /media and drive D should be listed, but its not. 

I have a 2TB drive partitioned as NTFS ( I want to be able to see the content in Widows if the drive is ever moved) but I can not see this drive in the /media directory. Am I looking in the wrong place? How can I determine if the system is detecting it? Do I need to mount it?

I need to access this drive, as I will be using sftp from my main machine to transfer content onto the xbmc machine.

Any help would be greatly appreciated.

---

### Post by L a r r y on 2011-08-22
> **spec36 said:**
> First let me advise I am using xbmc live, which is a cut down version of Ubuntu for media stores.

Lets say I have two drives in my ubuntu (xbmc) system, drive C and D. How do I switch between these drives in the shell? I think I go to /media and drive D should be listed, but its not. 

I have a 2TB drive partitioned as NTFS ( I want to be able to see the content in Widows if the drive is ever moved) but I can not see this drive in the /media directory. Am I looking in the wrong place? How can I determine if the system is detecting it? Do I need to mount it?

I need to access this drive, as I will be using sftp from my main machine to transfer content onto the xbmc machine.

Any help would be greatly appreciated.

In the Windows operating system, drives are lettered, with Drive A and B being floppy drives, and C being the first hard drive (or hard drive partition), with additional drives, CD drives, memory sticks and such being assigned letters above C.

In Linux, we refer to drives as if they were files or folders, beginning with /dev for device. First drive is /dev/sda (or /dev/hda) and second is /dev/sdb (or /dev/hdb) and so on.

We further refer to drive partitions by appending a numeral on the end of the drive reference, starting with 1 (/dev/sda1).

In Linux the parent directory of the filesystem is / (called "root.").  (Therein lies a subdirectory /root, which is the superuser's home directory, but that's drifting from the point.)

In the /etc folder there is a **[COLOR="DarkRed"]f[/COLOR]**ile**[COLOR="DarkRed"]s[/COLOR]**ystem **[COLOR="DarkRed"]tab[/COLOR]**le, contained in the **[COLOR="DarkRed"]fstab[/COLOR]** text file.

In Ubuntu, drives may be mounted in the /media folder, 
say, at /media/dev/sda6 for Partition number 6 on  the first hard drive.

You may specify that a drive partition be mounted at bootup by editing the /etc/fstab file in a text editor.  You may mount a drive at any point in your filesystem tree.

/mnt is often used in many Linux distros for mounting drive partitions.

To boot from a drive, some information must be edited into the /grub/menu.lst (old) or by editing files in the grub2 boot menu.  I'm new to Grub2, so I would have to research that myself.

I hope this gives you some leads to do research on for a better understanding.

(It took me awhile to grasp the concept of / being "OUT THERE." having come from the Windows idea of reaching into the computer and laying my hands on Drive C and so on.)

---

### Post by decrepit on 2011-08-22
if you do 
sudo fdisk -l

That will show your drives and how they are listed.

Any partitions not already available can be mounted automatically on boot up by adding them to the above mentioned /etc/fstab

---

### Post by elliotn on 2011-08-22
if u have disk utility it can show u name of the drive, etc

---

### Post by spec36 on 2011-08-22
Thanks for the information everyone. fdisk -l is what I was looking for to identify the drive that needed to be mounted. Very informative and I learned a lot about the linux filesystem in this post.

Thanks.

---

