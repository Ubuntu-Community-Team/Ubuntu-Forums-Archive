---
title: "Weird problem with permissions and things of the sort"
date: 2011-05-24
forum: General Help
---

### Post by umwhat on 2011-05-24
I mount my Windows 7 hard drive(?) and put my games onto that, and then run my games through wine. I do this because there's not enough space on my Ubuntu partition. 

I'm having a problem with doing that now though. The mount's folder/name now has an underscore at the end of it (Acer_), and my games' shortcuts are linked from "Acer", not "Acer_" so I can't open them. I can't run any of the games anyway. Normally, the 'execute' option is set for me. For some strange reason, it isn't anymore. I also can't change it or run it through terminal because I don't have the permissions to do so. The strangest thing is that everything was working perfectly just a day or 2 ago.

I'm not too bothered about the name of the folder being changed; that's no big deal. I just need a way to gain permission to make those files executable, otherwise I just get some warning error saying it's dangerous or whatever. Or is there more to it?

---

### Post by jerryjustly on 2011-05-24
I usually change the permissions of my files to "read and write" when need be by doing the following:
1. Open Accessories;Terminal
2. Type the following into the terminal, making sure that there is a space after 777.

sudo chmod 777 

3. Drag and drop the file/s anywhere onto the terminal.
4. Press enter and then enter your password.

You can also make a file executable by following the above instructions and replacing "sudo chmod 777" to "sudo chmod +x"

Also anytime you need permission to do something in the terminal, you can start the command with sudo.

---------------
[http://www.dotdeb.com](http://www.dotdeb.com) is a great place to find deb packages.

---

### Post by umwhat on 2011-05-25
Didn't work. :(
I tried both commands. Tried 777 first, dropped file (tried the folder, all files), entered password, still can't make it an executable. If I try to run the file through terminal it tells me I don't have the permissions.

---

### Post by webofunni on 2011-05-25
Can you share the command that you are executing in terminal ?

---

### Post by Morbius1 on 2011-05-25
> The mount's folder/name now has an underscore at the end of it (Acer_), and my games' shortcuts are linked from "Acer", not "Acer_" It almost looks like you have a mount statement in fstab that is being ignored and it's being mounted through Nautilus or Places on the fly which is turning off execute by default.

Why not post the output of the following commands so we can get to the bottom of this:
```
sudo blkid -c /dev/null
cat /etc/fstab
mount
```

---

### Post by webofunni on 2011-05-25
I guess it is 

```

sudo blkid -c /dev/null

```

not bklid

---

### Post by Morbius1 on 2011-05-25
Quite right, quite sloppy :oops:

---

### Post by webofunni on 2011-05-25
But its a good method to get partition details. Thanks for that ;-)

---

### Post by umwhat on 2011-05-25
mazar@mazar-laptop:~$ sudo blkid -c /dev/null
/dev/sda1: LABEL="PQSERVICE" UUID="72E0965FE09628FD" TYPE="ntfs" 
/dev/sda2: LABEL="SYSTEM RESERVED" UUID="B24096C940969427" TYPE="ntfs" 
/dev/sda3: LABEL="Acer" UUID="D624985024983589" TYPE="ntfs" 
/dev/sda5: UUID="1d22a859-1dbd-407d-a782-af681a7599ea" TYPE="ext4" 
/dev/sda6: UUID="e1150462-89c4-4b9b-b616-612d3ae2db1b" TYPE="ext4" 
/dev/sda7: UUID="49e11cc7-a419-4a60-9617-ebad1c862ead" TYPE="swap" 
/dev/sda8: UUID="7b02a761-d41f-47ab-88c7-7f73a7e5f3d7" TYPE="swap" 
/dev/sda9: UUID="e9c6f289-d729-4251-a316-63babdb35c66" TYPE="ext4" 
/dev/sda10: UUID="108ceac9-fca6-45e1-b3aa-f14d10809b75" TYPE="swap" 
mazar@mazar-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=e1150462-89c4-4b9b-b616-612d3ae2db1b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=49e11cc7-a419-4a60-9617-ebad1c862ead none            swap    sw              0       0
mazar@mazar-laptop:~$ mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro,commit=0)
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
gvfs-fuse-daemon on /home/mazar/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mazar)
/dev/sda3 on /media/Acer_ type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
mazar@mazar-laptop:~$

---

### Post by Morbius1 on 2011-05-25
Well, you can automount the ntfs partition fast enough:

[COLOR=Black][1] Unmount the current partition:
[/COLOR]```
[COLOR=Black]sudo umount /media/Acer_[/COLOR]
```[COLOR=Black]
[/COLOR][2] Make a home for the partition:
```
sudo mkdir /media/Acer
```[COLOR=Blue]*I have a feeling it's already there but it will tell you that.*[/COLOR]

[3] Edit fstab as root:
```
gksu gedit /etc/fstab
```[4] Add the following line to the end of fstab:
```
UUID=D624985024983589 /media/Acer ntfs defaults,uid=1000,umask=000 0 0
```[5] Save fstab, exit gedit and back in the terminal run the following command to test for errors and mount the partition - no reboot necessary:
```
sudo mount -a
```

---

### Post by webofunni on 2011-05-25
That partition is there, you may also need to remove it 

```

/dev/sda3 on /media/Acer_ type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_ permissions)

```

---

### Post by Morbius1 on 2011-05-25
That's why I had him unmount it:
> [COLOR=Black][1] Unmount the current partition:
[/COLOR]```
[COLOR=Black] sudo umount /media/Acer_ [/COLOR]
```


---

### Post by webofunni on 2011-05-25
unmounting will remove that from fstab ?

---

### Post by umwhat on 2011-05-25
It worked! Thank you, Morbius and Web! :D

---

### Post by Morbius1 on 2011-05-25
> **webofunni said:**
> unmounting will remove that from fstab ?
If it were in fstab, no. Unless I made another error he has no entry for /media/Acer_ in fstab.

---

