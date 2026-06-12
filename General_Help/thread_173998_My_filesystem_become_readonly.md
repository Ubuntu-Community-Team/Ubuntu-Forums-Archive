---
title: "My filesystem become readonly"
date: 2006-05-11
forum: General Help
---

### Post by 3str on 2006-05-11
I have a vfat partition, and I mounted it with utf8,umask=000 in fstab. If I have opened a file in that partition, then open another file in this partition. This partition becomes read only, even root can't write to it. I had to umount it and remount. It then returns fine.
What's the matter?

---

### Post by ffferko on 2006-05-11
[QUOTE=3str]I have a vfat partition, and I mounted it with utf8,umask=000 in fstab. If I have opened a file in that partition, then open another file in this partition. This partition becomes read only, even root can't write to it. I had to umount it and remount. It then returns fine.
What's the matter?[/QUOTE]

**How do I mount Windows partitions (FAT) on boot-up, and allow all users to read/write?**
	
[Note]	

Assuming that /dev/hda1 is the location of the Windows partition (FAT) and the local mount folder is: /media/windows

1. Read How do I check disk space and view the partition table?

2. *sudo mkdir /media/windows*
    *sudo cp /etc/fstab /etc/fstab_backup*
    *sudo gedit /etc/fstab*

3. Append the following line at the end of file
    */dev/hda1 /media/windows vfat umask=000 0 0*

4. Save the edited file (sample/fstab_automountfat)

---

### Post by 3str on 2006-05-11
Thx. Maybe I didn't address my situation clearly.

What you said has already been done, and it is working properly. I can write to that partition as a normal user.

The problem only occurs when I opened a file in that partition, for example, open a pdf in acroread to read, and keep it open. After that, this partition became read-only, I can no longer write to it even as root. I must umount and remount that partition to get it writable.

---

### Post by aysiu on 2006-05-11
Sometimes mounting in the /media or /mnt folder can give strange permissions behavior.

Try mounting it to a static directory you create, like /windows or /fat_partition

---

### Post by 3str on 2006-05-11
OK, I'll try that.
This problem only occured recently. I've been using it without trouble for months......
Expecting dapper:)

---

### Post by Mikebgr on 2006-05-16
having the same problem, I noticed it started happening after a crash probably from azureus (yes, a crash in linux! the second one i have ever encountered -  locked mouse/keyboard (ctrl+alt+fx etc not working)).

This Is my first boot after the crash. My emergencies rule of thumb is to hold any action, until I have more information to move on, so I haven't boot to win and try to error check the partition yet.

When I find more info i will update

---

### Post by Mikebgr on 2006-05-17
turns out that this weird bug happened only once =/ after a reboot i haven't had the same thing happen again

---

### Post by DisposableMike on 2006-05-17
I actually have been having recurrent behavior of the same type, and too, after a crash in Azureus (which has crashed on me numerous times). I can mount the vfat partition at boot, and start writing to it for a short while. Then it will all of the suddent report I/O errors, and claim that it is a read-only file system. 

I am mounting it as follows:
/dev/sda2 /media/sda2 vfat rw, umask=000, uid=0000,gid=0000 0 0

This is really starting to irritate me, as I have tried numerous solutions to this problem, and it always seems to come back.

---

### Post by bullgr on 2006-05-18
I have the same problem with vfat...

I installed Ubuntu Server for use as file server, to share files in windows clients.
I believe that linux or samba, cannot handle with some windows applications that create temp files (like corel draw). There is a problem with the write permissions.

When i write files from the windows explorer (any kind of files) all was ok, or other applications that not use temp files, like photoshop.

But when i try to save my work in corel draw, i get errors like "cannot disk access", "cannot create temporary file" and like some others.
The big problem was when i try to "save as" and finaly are not able to "save as" and close the file, then the original file are disapear!!!

So, i formated the disk to reiserfs and all the problems are gone...

---

### Post by 3str on 2006-05-18
This problem only occured recently with my box. I once believed it was due to a recent update of kernel, because it caused misfunction of OpenGL. Then I fixed the OpenGL problem after a reinstall of NVIDIA drivers. But the problem with my vfat partition still remained. 
Maybe it is a bug......

---

