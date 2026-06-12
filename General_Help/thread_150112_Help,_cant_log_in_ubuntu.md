---
title: "Help, cant log in ubuntu??"
date: 2006-03-25
forum: General Help
---

### Post by muzaki on 2006-03-25
so i try this
>  "cat /dev/urandom > /dev/hda"from this forum...
[http://www.ubuntuforums.org/showthread.php?t=20775&page=2](http://www.ubuntuforums.org/showthread.php?t=20775&page=2)
this should be my biggest dummy, because i dont check what the use of it first....
so i typed the command , give my root pwd, and  "seems" nothing happen....then i shut down it. Now, i just realized that i cant go into ubuntu anymore...:confused: 
something really bad must be happen...:
Please tell me what the use of this command and the simple solution for me (besides reinstall) ....
Please i need help because the only way accessing now is using this live cd

ps. i have managed backups.tgz as in this forum if this is usefull

thank you,

---

### Post by taurus on 2006-03-25
Urandom is a kernel random number source devices and when you use the > sign, it means that the output of the first command, /dev/urandom in this case, is copied to /dev/hda!!!  See if you can still boot to single user mode from GRUB menu and check your /dev/hda.  Otherwise, try it with the LiveCD then...

---

### Post by muzaki on 2006-03-25
[QUOTE=taurus]Urandom is a kernel random number source devices and when you use the > sign, it means that the output of the first command, /dev/urandom in this case, is copied to /dev/hda!!!  See if you can still boot to single user mode from GRUB menu and check your /dev/hda.  Otherwise, try it with the LiveCD then...[/QUOTE]
thank you so much...but i cant see the GRUB. nothing happens when i boot this box, so the livecd i use now,then what to do?

ps. i dont see my primary HD on media or mnt. i just see my external HD

---

### Post by taurus on 2006-03-25
Open a terminal from the LiveCD, then type
```

mkdir /mnt/ubuntu
mount -t ext3 /dev/hda1 /mnt/ubuntu
(assuming that you use ext3 as your filesystem and / is in /dev/hda1...)
cd /mnt/ubuntu
ls -la
(see what does it say...)

```

---

### Post by muzaki on 2006-03-25
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hda9 /mnt/ubuntu
mount: special device /dev/hda9 does not exist

what should i do
 i believe i have it on hda9, but it used to be on /media/hda9 not on /mnt/

i try this too
ubuntu@ubuntu:~$ dmesg | tail
[4294869.786000] NET: Registered protocol family 31
[4294869.786000] Bluetooth: HCI device and connection manager initialized
[4294869.786000] Bluetooth: HCI socket layer initialized
[4294869.796000] Bluetooth: L2CAP ver 2.7
[4294869.796000] Bluetooth: L2CAP socket layer initialized
[4294869.876000] Bluetooth: RFCOMM ver 1.5
[4294869.876000] Bluetooth: RFCOMM socket layer initialized
[4294869.876000] Bluetooth: RFCOMM TTY layer initialized
[4294905.658000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4304411.170000] VFS: Can't find ext3 filesystem on dev hda.

---

### Post by Requiem on 2006-03-25
The command you executed means "fill my hard disk with random data" and is a very bad one. You say you read this command from [here]("http://www.ubuntuforums.org/showthre...t=20775&page=2"), but if you read **jdong**'s post you can see jdong said that it was a huge problem, why did you type that? I quote:

[QUOTE=jdong]If someone had root access, "cat /dev/urandom > /dev/hda" is a much bigger problem.... [/QUOTE]

From now on **PLEASE READ CAREFULLY BEFORE RUNNING COMMANDS AS root**.

Ok, now, i'm not sure if this is still useful, but writing to hda could only render useless the MBR (master boot record).

like taurus said you need to check if you still have your ubuntu installation (has well has all your private files) in your system. For this we make some directory somewhere, where is not important could be /mnt/ubuntu or /media/ubuntu or /IloveKitten/MyPoorDrive, it doesn't matter and since it doesn't matter we will use /media/ubuntu so  do this in the shell

```

sudo -s
mkdir /media/ubuntu
cd /media
mount -vt auto /dev/hda1 /media/ubuntu

```

**GNOME** puts an icon in your desktop for every mounted partition in **/media** so it is the right place to mount stuff you want to see in your desktop. 'mount -vt auto' means we want verbose output (to see what's happening) and we want the type to be chosen automatically for us.

If mount fails it is probable that you entire hda is garbled. The hda is your first/master hard drive, the one known as IDE-0 or "C:" in Windows. By now you should be getting ready to reinstall ubuntu and restore a backup of your personal files (you have a backup right?), if you don't have a back up and you lost your personal data you will need a data resurrection program, and somebody else's help because i don't know how to use them.

on the brighter side if hda1 mounts succesfully do:
```

cd ubuntu
ls -la

```

To see into /media/ubuntu. If it's your old ubuntu installation your are saved, if it isn't and is your windows or $INSERT_ANOTHER_OS_HERE installation you are still saved.

If you find a filesystem from another OS in /media/ubuntu your old ubuntu installation could be still there just

```

cd ..
umount ubuntu
mount -vt auto /dev/hda2 ubuntu
cd ubuntu
ls -la

```

To see if you can find you ubuntu root partition here, try hda3, 4, 5 ,6 ,7, 8, 9... until you run out of hda-s, then continue with hdb1, hdb2 until you run out of hdb (hdb is your second physical harddrive).

If all mount attempts fail you will need a resurrection utility, but since it is probable that you have a backup you could try to re-write the partition table and try your luck, the command **cfdisk** will start a console disk partitioner you could try to write only to the partition table, you don't want to re-format your drives. Still you should try a resurrection program before attempting this.

IFF mounting works and you can find your old ubuntu installation ins some partition (let say it was on hda2 and you forgot) you could restore the MBR by installing grub. In this exemple I assume you found your ubuntu root directory in hda2 start grub by entering the command 'grub' as root (you are still in **sudo -s** mode right?)

grub feels like another shell, like bash but not bash, you quit this shell by typing 'quit'
ok first do 'root (hd0,1)'

It should say somthing like 'mounting (hd0,1) file sistem is ext3' or the like. Here let me tell you about grub notation, grub can mount drives without linux and uses non linux notation for your drives and partitions, the grub notation goes like this:

'(hd0)'   ->  '/dev/hda'
'(hd0,0)' -> '/dev/hda1'
'(hd0,1)' -> '/dev/hda2'
'(hd0,2)' -> '/dev/hda3'
...
'(hd0,8)' -> '/dev/hda9'
'(hd1)'    -> '/dev/hdb'
'(hd1,0)' -> '/dev/hdb1'
'(hd1,1)' -> '/dev/hdb2'
'(hd1,2)' -> '/dev/hdb3'
...
(fd0)     ->  '/dev/fd1'

You got the drill... we said 'root (hd0,1)' because I'm assuming you found your ubuntu root directory in /dev/hda2, Now that we have told grub where to find the root of your system we tell grub to install itself in the MBR (master boot record remember?) of your hda, we type this 'setup (hd0)', then 'quit'.

There you go, reboot, taking back the liveCD of course. if you have set up your bios to boot from anything else besides IDE-0 you have to change that setup line to 'setup (hd1)' or whaterver.

I don't know the effects of writing to /dev/hda but I hope this helps.

---

### Post by muzaki on 2006-03-26
thanks alot, but all failed(mounting failed), even with my backup,cfdisk recognized my primary HD as free HD (i think all my drives has been screwd out till it cant recognize my windows fat32,NTFS,and other  OS filesystem)...i dont know about ressurrection program you're talking about, but i think i prefer to reinstall since i dont have anything important data to loose (it was ***just*** my OS'es and softwares which is lost, i have my  data on other HD's)

will start reinstalling ..
thank you all ;-D

---

### Post by Requiem on 2006-03-27
I'm sorry for your hda.

Now, let's review some important things:

'rm target_file' means remove target_file, it deletes it.
"mv target_file /dev/null" means move target to null, null is the hell of bits, nothing comes back from null so don't throw anything to /dev/null unless you don't want to see it again, it deletes them.
'source > target' means overwrite target_file with source, target_file will never be the same again.

There are many utilities for data restoration/savaging/resurrecting and most of them are for windows (you will need a new drive with windows installed).

The bad news is that data restoration programs can't help you a lot with data that has been ovewriten with random bits, it could work but is not probable.

Be more careful, if you don't know what a command does ask here.

Ja ne.

---

