---
title: "Getting SCO OpenServer floppy disks open on Ubuntu"
date: 2009-09-29
forum: General Help
---

### Post by PMI on 2009-09-29
Hi all, I'm a super Unix newbie.

Problem:
We have an old plasma cutting software called Cybermation from Cimtec and on SCO OpenServer as the OS. The motherboard died and also the hard drives freezes at a certain point when it loads. 

My friend recommended me to use a more popular Unix OS. So here I am. The Cybermation installation are in floppy disks. I did the things I found when I searched for "floppy" help (by including file system: vfat and ext2. I was able to read the old Windows floppy disks. But I was not able to read the Cybermation disks; error is "Can't mount the file."

Am I missing an extension?
How can I get Ubuntu to read these floppy disks?
Any help is very appreciated.



I also reinstalled SCO OpenServer. Their website wasn't much help. How do I read the floppy drive in OpenServer?

---

### Post by BitJunkie on 2009-09-29
I'm not familiar with Openserver 6, only 5.0.X. Most software floppies for SCO that I have seen are either for use with "custom" or are just tar format. 

For "custom", log in to a text session as root and type "custom" (without the quotes). Use the arrow keys and tab to move around. Select Software->Install new -> from the local machine. For the Media Device, the drop-down should show something like "Floppy Disk Drive 0". Select that and custom will examine the floppy and present a list of software it found on the disk. Select what you need and go from there.

For tar, create temp directory and extract the files there. This assumes the floppy is the first floppy disk in the system (fd0): 
mkdir /tmp/cmation
cd /tmp/cmation
tar xvf /dev/fd0
After this, there is usually an install script or the folder contains the application file to run.

I hope this helps.

---

### Post by PMI on 2009-09-29
The disks are in tar format. Thanks.

But how do I figure which is the script or application file?
Do I look for a certain extension?

---

### Post by BitJunkie on 2009-09-29
Sometimes shell scripts have a ".sh" extension. 

In the directory where you extracted the files, run "ls -l" (those are letters, not numbers). On the left, files with an x in the permissions are executable, e.g. -rwxrwxr--. Anything obvious from the filenames that include the execute bit? BTW, its never a good idea to run a program if you aren't sure what it does, especially as root.

---

### Post by dcstar on 2009-09-30
> **PMI said:**
> Hi all, I'm a super Unix newbie.

Problem:
We have an old plasma cutting software called Cybermation from Cimtec and on SCO OpenServer as the OS. The motherboard died and also the hard drives freezes at a certain point when it loads. 

My friend recommended me to use a more popular Unix OS. So here I am. The Cybermation installation are in floppy disks. I did the things I found when I searched for "floppy" help (by including file system: vfat and ext2. I was able to read the old Windows floppy disks. But I was not able to read the Cybermation disks; error is "Can't mount the file."

Am I missing an extension?
How can I get Ubuntu to read these floppy disks?
Any help is very appreciated.


I also reinstalled SCO OpenServer. Their website wasn't much help. How do I read the floppy drive in OpenServer?

The chances of SCO binaries working on a Linux system are small.

You can build a custom Linux kernel with SCO filesystem support, but as far as running SCO programs you will probably need a SCO system - which you may well be able to install as a VM inside a Linux host.

---

