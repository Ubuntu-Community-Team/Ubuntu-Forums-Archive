---
title: "Moving the home directory"
date: 2005-02-21
forum: General Help
---

### Post by Al5274 on 2005-02-21
I am have a dual boot sytem WinXp and Ubuntu.
My Ubuntu partion is 3GB.
Also at present my Home directory is installed on this 3GB partition.
I Also have a 200GB USB hardrive thats formated and partioned.
Is it possible to move my Home directory to a Fat32 partion on my USB drive by just using Konqueror....selecting the directory and moving it?
Do I need to edit any thing etc?

---

### Post by kassetra on 2005-02-21
[QUOTE=Al5274]I am have a dual boot sytem WinXp and Ubuntu.
  My Ubuntu partion is 3GB.
  Also at present my Home directory is installed on this 3GB partition.
  I Also have a 200GB USB hardrive thats formated and partioned.
 Is it possible to move my Home directory to a Fat32 partion on my USB drive by just using Konqueror....selecting the directory and moving it?
  Do I need to edit any thing etc?[/QUOTE]
  
  There is actually quite a bit involved in moving your home partition
  Here you go:
  1. Create a filesystem on your usb drive:
 To create a filesystem on the new partition, first make sure you know the exact device name for the new partition (for example, /dev/sda5). If you're not sure of the exact device name, stop now and double-check!
   ```
sudo mkfs.ext2 /dev/<put device name here>
``` 
  
  2.Mount the new filesystem in /mnt
      Create a directory called /mnt/newpart, and then mount the new partition there:
   ```
sudo mount /dev/<device name> /mnt/newpart
``` 
  
  3. Drop to single-user mode
 I delayed this step as long as possible to maximize system availability, but we now must drop into single-user mode, and copy files from /home to /mnt/newpart. You shouldn't have any files open in /home, and entering single-user mode eliminates this possibility:
   ```
sudo init 1
``` 
  
  4. Change directories to /home and copy files
      Type the following:
   ```
cd /home
  sudo cp -ax * /mnt/newpart
```
  
  5. Use the new partition (when old /home is a partition)
  Unmount the old partition by typing:
   ```
cd /
  sudo umount /home
``` 
  
  Then, unmount and remount the new partition:
   ```
sudo umount /mnt/newpart
  sudo mount /dev/<device name> /home
``` 
  
 Now, the new partition is available at /home and is ready to be used. We can perform the last few steps in multiuser mode. Exit single-user mode, so that the system is back up and running, by pressing CTRL-D. 
 
   **Important:** After the system starts up normally, sudo edit /etc/fstab so that /dev/<device name> is now mounted automatically at /home instead of your old partition. For example, change this line from:
  
 
  ```
/dev/hda3 /home ext2  defaults  1 2
``` 
 ```
/dev/<device name> /home ext2  defaults  1 2
```
 
 back to the next steps here:
 ```
cd /
 sudo mv /home /home.old
 sudo mkdir /home
 sudo mount /dev/<device name> /home
``` 
 
 Now, leave single user mode by pressing CTRL-D. When the system is back
 up and running, edit /etc/fstab and add a line like the following:
 ```
/dev/<device name> /home ext2  defaults  1 
``` 
 
 That way, your new partition will get mounted correctly the next time the system is rebooted.

---

### Post by Al5274 on 2005-02-21
Thanks alot for the quick reply.  Ill give it a go tonight.

Cheers!

---

### Post by Jad on 2005-02-21
in simple why you don't create new user with a new home directory pointed to your USB Harddrive ? and then copy all files in your X home directly to the new one?

---

### Post by kassetra on 2005-02-21
[QUOTE=Jad]in simple why you don't create new user with a new home directory pointed to your USB Harddrive ? and then copy all files in your X home directly to the new one?[/QUOTE]
  
 When you create a new user, their home directory will be created under the current /home partition, thus creating the same problem -- it will still be on the little partition and not the usb drive. There is no way to use the new drive as the /home partition without either wiping and redoing your partition table or going through the steps I described.

---

### Post by piedamaro on 2005-02-21
However, maybe it can be done (altough I doubt), but you can't have your home dir on a fat filesystem (fat doesn't handle file owners and permissions). You'll have problems, e.g running X because of missing permissions on ~/.ICEauthority and the like.

---

### Post by Al5274 on 2005-02-23
I was hoping to create my home directory on a fat32 partition on my USb drive so winxp could read and write to it.  However I will format it to ext2.
One more thing tho.........I created the directory on my far32 called "newpart" as described in number 2 code.  I then tried the "sudo init 1" as in step 3 and my screen went blank and locked up....? any ideas!  (I rebooted and all seems fine now.)

---

