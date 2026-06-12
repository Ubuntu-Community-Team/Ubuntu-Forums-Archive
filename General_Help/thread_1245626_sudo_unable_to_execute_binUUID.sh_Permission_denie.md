---
title: "sudo: unable to execute /bin/UUID.sh: Permission denied"
date: 2009-08-20
forum: General Help
---

### Post by billdotson on 2009-08-20
Why can't I run a script I wrote as root? It has been chmod 777 ed , I even put it in /bin. This is a LiveCD.

> ubuntu@ubuntu:~$ sudo UUID.sh
sudo: unable to execute /bin/UUID.sh: Permission denied


This happens with other things as well. For example:

sudo ntfslcone /dev/sda1 -r -O /mnt/backup/IMG.img would say permission denied but if I put that command inside of a script and ran it it would run fine. Why is this UUID one being such a pain?

Here is the script: 

```
#! /bin /sh

umount -a
x=1
y=1
while [ $y -le 7 ]
do
  if [ $x -le 4 ]
    vol_id /dev/sda$x --uuid >> /home/ubuntu/Desktop/UUID.txt
  else
  fi
  let x+=1  
  vol_id /dev/sdb$y --uuid >> /home/ubuntu/Desktop/UUID.txt
  let y+=1
done
```

---

### Post by bodhi.zazen on 2009-08-20
First, no space in the shebang

#!/bin/bash

Second, did you make it executable ?

```
sudo chmod a+x /bin/UUID.sh
```

Last you should probably keep that script either in ~/bin (still owned by root mind you) or /usr/local/bin

It is not critical, just a tradition.

---

### Post by billdotson on 2009-08-21
Yes it was made to be executable. I use chmod by the numbers instead of a,x and whatever the other is. I did not see the space in the shebang so that might have been it. Could you explain why it happens with other commands where they won't give me permission unless they are in a script and ran with sudo preceding? 

Yeah, I usually just have a folder called scripts sitting in my home partition and a backup of it on another partition. All the scripts in it are executable but the actual folder isn't in the path as far as I know.

---

### Post by bodhi.zazen on 2009-08-21
> **billdotson said:**
> Yes it was made to be executable. I use chmod by the numbers instead of a,x and whatever the other is. I did not see the space in the shebang so that might have been it. Could you explain why it happens with other commands where they won't give me permission unless they are in a script and ran with sudo preceding? 

Yeah, I usually just have a folder called scripts sitting in my home partition and a backup of it on another partition. All the scripts in it are executable but the actual folder isn't in the path as far as I know.

So you got it working then ?

I am not following your question, can you give an example ?

---

### Post by billdotson on 2009-08-21
To run lots of commands that require root permission the only way I can run them is to write them in a bash script and do sudo ./SCRIPT.sh. I can't just type: "sudo cd /media/backup" or "sudo ntfsclone /dev/sdb1 -s -o /dev/sda1/OSbackup.img" I would have to put "cd /media/backup" in a script and run it as sudo ./cd.sh. or put "ntfsclone /dev/sdb1 -s -o /dev/sda1/OSbackup.img" in ntfs.sh and run sudo ./ntfs.sh.

Why doesn't putting sudo in front of a command (even with pipes included) work for me a lot of the time? Does it have to do with editing the timestamp on how long root access is preserved?

It gets fairly annoying to have to write up a script every time I want to copy a file or run an operation on a folder that has root access only.

---

### Post by bodhi.zazen on 2009-08-22
It depends on the command. You can not directly pipe or re-direct with sudo, and if you cd you probably then need to use a ; 

cd /foo; ls 

If you want to use sudo you need to use a more complex configuration.

Assuming ls.txt is owned by root :

```
sudo touch ls.txt
```

sudo ls >> ls.txt # this command fails with a permission denied error.

```
sudo bash -c "ls > ls.txt" # This works
```

---

### Post by billdotson on 2009-08-27
Thanks bodhi I will try that.

Do you have any idea why the permissions are acting funny? Shouldn't sudo chmod -R 744 on a mount point allow users to navigate and read/copy files but just not anything else? It made it where you couldn't even navigate in the folder using cd and in nautilus you couldn't see that there were any files in there. It did this on an ext3 partition that was mounted and a FAT32 partition.

---

### Post by billdotson on 2009-08-28
Any idea on those permissions?

---

### Post by bodhi.zazen on 2009-08-28
Permissions depend on the file system

Linux native (ext3) are set with chown and chmod
Windows native (FAT) are set when you mount the partition.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

Without additional information (file system, exact command) it is hard to be more specific.

---

### Post by blueridgedog on 2009-08-28
> **billdotson said:**
> To run lots of commands that require root permission the only way I can run them is to write them in a bash script and do sudo 

Some general observations about this:  Mount drives in locations you own - or give yourself ownership of existing locations.  You can control the mount location and the ownership of that location so you do not need sudo to do maintenance.  Create a binary directory for your user (as mentioned - ~/bin or similar).  I may be misunderstanding the root cause of your issues, but in my use of Ubunutu, and in trying to learn to work in a "rootless" system, I have generally gotten in the habit of setting things up so that my user account can manager my media and the utilities that I write to make things work.

---

### Post by billdotson on 2009-08-29
I had it mounted on /media/backup and did sudo chmod -R 744 /media/backup.
This made all files inaccessible and completely unreadable by any user other than root. I could not even cd into the directory from the terminal. I also tried this on the other folder when it was unmounted and I believe I tried changing the owner to ubuntu:ubuntu (livecd) but I can't remember whether I did that when it was mounted or not.

All the commands except for chown were tried on both the ext3 partition and the fat32 partition.

---

