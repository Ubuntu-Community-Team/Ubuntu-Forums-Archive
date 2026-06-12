---
title: "Two Ubuntu partitions and I need to access files"
date: 2012-05-14
forum: General Help
---

### Post by poolhustler on 2012-05-14
I was upgrading my computer to the latest Ubuntu version when  the computer froze(at least I think it did), so I turned it off. When I  turned it back on again, to try to finish the upgrade, all I got was a  black screen with a blinking arrow.
  Is it possible to get hold of my saved files?
  Now I have made a partition with the latest Ubuntu version installed on it. 
  Is it possible to access the files in the old Ubuntu/partition from the new Ubuntu/partition?
  Thanks.

---

### Post by carl4926 on 2012-05-14
It should be easy. I assume it wasn't being formatted?
The partition should show in nautlius, either in the new install or from a live cd session

---

### Post by roelforg on 2012-05-14
Assuming you didn't erase the old one here.
First find out what partition is what (gparted should tell you which ones are ext* partitions).
I'll assume the old/broken one is on /dev/sda1
and the new/working one on /dev/sda2
Now run:
```

sudo mkdir /media/oldpart
sudo mount /dev/sda1 /media/oldpart

```
Do your stuff...
```

sudo umount /dev/sda1
sudo rmdir /media/oldpart

```

---

### Post by poolhustler on 2012-05-14
I just installed a new Ubuntu OS from a USB-memorystick. When installing I got the question if I wanted to install it on a new part of my SSD-drive(I dont think I formatted). If I did that I would still have access to my old files. But now I cant find them anywhere.

Under "Devices" in  the Nautilus(window of the home-folder, filesystem etc?) _****_there is only one Icon with the text: 21GB Filesystem. So I guess the other partition does not show. 

Any ideas?

---

### Post by roelforg on 2012-05-14
> **poolhustler said:**
> I just installed a new Ubuntu OS from a USB-memorystick. When installing I got the question if I wanted to install it on a new part of my SSD-drive(I dont think I formatted). If I did that I would still have access to my old files. But now I cant find them anywhere.

Under "Devices" in  the Nautilus(window of the home-folder, filesystem etc?) there is only one Icon with the text: 21GB Filesystem. So I guess the other partition does not show. 

Any ideas?

```

ls /dev/sd*
sudo fdisk -l
sudo blkid
sudo cat /etc/fstab
sudo cat /etc/mtab

```
and post the output
It gives us information about your drive-layout.

---

### Post by Enigmapond on 2012-05-14
If it doesn't show in nautilus from either the other partition or Live CD/USB then there is a good possibility that you formatted the partition and would hope that you backed up somewhere...

---

### Post by roelforg on 2012-05-14
> **Enigmapond said:**
> If it doesn't show in nautilus from either the other partition or Live CD/USB then there is a good possibility that you formatted the partition and would hope that you backed up somewhere...
Mine doesn't show all of my partitions, but that doesn't mean they're not there.
And even if he fomatted it, it would show, but just as a blank one.
My desktop has 2 hd's with a total of three parts (root, swap, data (on hd2)),
but my filemgr doesn't show the partition of the 2nd hd.
I modded /etc/fstab to automount /dev/sdb1 on /data, this proves my point.
If you run the commands i gave in my last post, we'll know exactly what happened to the data.

---

### Post by poolhustler on 2012-05-14
Ok GParted shows me something like this:

/dev/sda1               ext4
/dev/sda2               extended
      /dev/sda6         ext4
      /dev/sda5         linux-swap
unallocated            unallocated

I guess the old one is /dev/sda1. 

So I guess I should type in this in the terminal then? 
ls /dev/sda1 
sudo fdisk -l 
sudo blkid 
sudo cat /etc/fstab 
sudo cat /etc/mtab

Output is coming

---

### Post by roelforg on 2012-05-14
> **poolhustler said:**
> Ok GParted shows me something like this:

/dev/sda1               ext4
/dev/sda2               extended
      /dev/sda6         ext4
      /dev/sda5         linux-swap
unallocated            unallocated

I guess the old one is /dev/sda1. 

So I guess I should type in this in the terminal then? 
ls /dev/sda1 
sudo fdisk -l 
sudo blkid 
sudo cat /etc/fstab 
sudo cat /etc/mtab

Output is coming

No,
now we know that your old part is indeed /dev/sda1,
just run what i posted in my first post to this thread.

[quote=roelforg]
Assuming you didn't erase the old one here.
First find out what partition is what (gparted should tell you which ones are ext* partitions).
I'll assume the old/broken one is on /dev/sda1
and the new/working one on /dev/sda2
Now run:
 	Code:
 	sudo mkdir /media/oldpart sudo mount /dev/sda1 /media/oldpart 
Do your stuff...
 	Code:
 	sudo umount /dev/sda1 sudo rmdir /media/oldpart

[/quote]

---

### Post by poolhustler on 2012-05-14
After the first command I get this:

name@name-ThinkPad-X100e:~$ sudo mkdir /media/sda1
[sudo] password for name: 
name@name-ThinkPad-X100e:~$ sudo mkdir /media/sda1
mkdir: cannot create directory `/media/sda1': File exists
name@name-ThinkPad-X100e:~$

---

### Post by roelforg on 2012-05-14
> **poolhustler said:**
> After the first command I get this:

name@name-ThinkPad-X100e:~$ sudo mkdir /media/sda1
[sudo] password for name: 
name@name-ThinkPad-X100e:~$ sudo mkdir /media/sda1
mkdir: cannot create directory `/media/sda1': File exists
name@name-ThinkPad-X100e:~$

No no no
i'll dictate exactly what to type, okay?
```

sudo mkdir /media/oldpart
sudo mount /dev/sda1 /media/oldpart

```
Okay? It's exactly as it needs to be for your sys.

---

### Post by poolhustler on 2012-05-14
Ok, hopefully I got it right this time.

name@name-ThinkPad-X100e:~$ sudo mkdir /media/oldpart sudo mount /dev/sda1 /media/oldpart
[sudo] password for name: 
mkdir: cannot create directory `/media/oldpart': File exists
mkdir: cannot create directory `sudo': File exists
mkdir: cannot create directory `mount': File exists
mkdir: cannot create directory `/dev/sda1': File exists
mkdir: cannot create directory `/media/oldpart': File exists
name@name-ThinkPad-X100e:~$ ^C
name@name-ThinkPad-X100e:~$

---

### Post by roelforg on 2012-05-14
> **poolhustler said:**
> Ok, hopefully I got it right this time.

name@name-ThinkPad-X100e:~$ sudo mkdir /media/oldpart sudo mount /dev/sda1 /media/oldpart
[sudo] password for name: 
mkdir: cannot create directory `/media/oldpart': File exists
mkdir: cannot create directory `sudo': File exists
mkdir: cannot create directory `mount': File exists
mkdir: cannot create directory `/dev/sda1': File exists
mkdir: cannot create directory `/media/oldpart': File exists
name@name-ThinkPad-X100e:~$ ^C
name@name-ThinkPad-X100e:~$
Don't copy them all at once!
One by one, and if the first line error's out, no probs, it's supposed to do so if you did this before.
So your session should look something like this:
```

name@pc:~$ sudo mkdir /media/oldpart
[sudo] password for name:
mkdir: cannot create directory `/media/oldpart': File exists
name@pc:~$ sudo mount /dev/sda1 /media/oldpart
name@pc:~$ 

```
(i couldn't be bothered typing out the full pc name, but you get the point)

---

### Post by poolhustler on 2012-05-14
Ok, one of these attempts should be rigth. 

first:

name@name-ThinkPad-X100e:~$ sudo mkdir /media/oldpart
mkdir: cannot create directory `/media/oldpart': File exists
name@name-ThinkPad-X100e:~$ sudo mount /dev/sda1 /media/oldpart
mount: /dev/sda1 already mounted or /media/oldpart busy
mount: according to mtab, /dev/sda1 is already mounted on /media/oldpart
name@name-ThinkPad-X100e:~$ 

second:

name@name-ThinkPad-X100e:~$ sudo mkdir /media/oldpart
mkdir: cannot create directory `/media/oldpart': File exists
name@name-ThinkPad-X100e:~$ sudo mount /dev/sda1
mount: /dev/sda1 already mounted or /media/oldpart busy
mount: according to mtab, /dev/sda1 is already mounted on /media/oldpart
name@name-ThinkPad-X100e:~$ 

The difference is on line 3.

---

### Post by roelforg on 2012-05-14
> **poolhustler said:**
> Ok, one of these attempts should be rigth. 

first:

name@name-ThinkPad-X100e:~$ sudo mkdir /media/oldpart
mkdir: cannot create directory `/media/oldpart': File exists
name@name-ThinkPad-X100e:~$ sudo mount /dev/sda1 /media/oldpart
mount: /dev/sda1 already mounted or /media/oldpart busy
mount: according to mtab, /dev/sda1 is already mounted on /media/oldpart
name@name-ThinkPad-X100e:~$ 

second:

johan@johan-ThinkPad-X100e:~$ sudo mkdir /media/oldpart
mkdir: cannot create directory `/media/oldpart': File exists
johan@johan-ThinkPad-X100e:~$ sudo mount /dev/sda1
mount: /dev/sda1 already mounted or /media/oldpart busy
mount: according to mtab, /dev/sda1 is already mounted on /media/oldpart
johan@johan-ThinkPad-X100e:~$ 

The difference is on line 3.


Lol: check if your files are in /media/oldpart
it complains it has already been mounted there so you should be able to find your files

---

### Post by poolhustler on 2012-05-15
I am not sure if i am doing this the right way but my files should be in the folder "home" or in a folder with my name on it. There is no folder with my name on it.  And there should also be a couple of more folders that I should recognize. So I don't think my files are there.

What command do I use to check if my files are in the folder "home"? I've tried "cd home" "ls home".

  

name@name-ThinkPad-X100e:~$ sudo mkdir /media/oldpart
[sudo] password for name: 
mkdir: cannot create directory `/media/oldpart': File exists
name@name-ThinkPad-X100e:~$ sudo mount /dev/sda1 /media/oldpart
name@name-ThinkPad-X100e:~$ ls /media/oldpart
bin    dev   initrd.img      lib64       mnt   root  selinux  tmp  vmlinuz
boot   etc   initrd.img.old  lost+found  opt   run   srv      usr  vmlinuz.old
cdrom  home  lib             media       proc  sbin  sys      var
name@name-ThinkPad-X100e:~$ ls home
ls: cannot access home: No such file or directory
name@name-ThinkPad-X100e:~$ cd home
bash: cd: home: No such file or directory
name@name-ThinkPad-X100e:~$

---

### Post by roelforg on 2012-05-15
> **poolhustler said:**
> I am not sure if i am doing this the right way but my files should be in the folder "home" or in a folder with my name on it. There is no folder with my name on it. And there should also be a couple of more folders that I should recognize. So I don't think my files are there.
 
What command do I use to check if my files are in the folder "home"? I've tried "cd home" "ls home".
 
 
 
name@name-ThinkPad-X100e:~$ sudo mkdir /media/oldpart
[sudo] password for name: 
mkdir: cannot create directory `/media/oldpart': File exists
name@name-ThinkPad-X100e:~$ sudo mount /dev/sda1 /media/oldpart
name@name-ThinkPad-X100e:~$ ls /media/oldpart
bin dev initrd.img lib64 mnt root selinux tmp vmlinuz
boot etc initrd.img.old lost+found opt run srv usr vmlinuz.old
cdrom home lib media proc sbin sys var
name@name-ThinkPad-X100e:~$ ls home
ls: cannot access home: No such file or directory
name@name-ThinkPad-X100e:~$ cd home
bash: cd: home: No such file or directory
name@name-ThinkPad-X100e:~$
 
first run
```

cd /media/oldpart

```
before cd'ing to home
 
But the ls shows me all your files are there.

---

### Post by poolhustler on 2012-05-15
>But the ls shows me all your files are there.

YES, I found my files!. Is it possible to rescue them? How do I save them to a USB-memorystick?

It's the home-folder that I need to rescue. If that is not possible I need to rescue a folder inside it.

Maybe it is easier to move the files to the working partition?

---

### Post by roelforg on 2012-05-15
> **poolhustler said:**
> >But the ls shows me all your files are there.
 
YES, I found my files!. Is it possible to rescue them? How do I save them to a USB-memorystick?
 
It's the home-folder that I need to rescue. If that is not possible I need to rescue a folder inside it.
 
Maybe it is easier to move the files to the working partition?
 
Lets say your usb is mounted at /media/usb and your username on the old machine was poolhustler
```

sudo mkdir /media/usb/oldhome
sudo cp -aR /media/oldpart/home/poolhustler/* /media/usb/

```
And there's now an exact copy (including permissions and symlinks) of your old home on your usb (it's in the oldhome folder).

---

### Post by poolhustler on 2012-05-15
>Lets say your usb is mounted at /media/usb and your username on the old machine was poolhustler

I am not sure what you mean exactly. How do I mount my usb at /media/usb? Should I just put it in my computer and write the code you gave me? By "old machine", do you mean the old partition?
I am a little nervous to make any mistakes:)

---

### Post by roelforg on 2012-05-15
> **poolhustler said:**
> >Lets say your usb is mounted at /media/usb and your username on the old machine was poolhustler
 
I am not sure what you mean exactly. How do I mount my usb at /media/usb? Should I just put it in my computer and write the code you gave me? By "old machine", do you mean the old partition?
I am a little nervous to make any mistakes:)
 
You could also just open your filemanager (the home button in the unity launcher)
and browse to "Filesystem" and click on media and on oldpart and on home.
Right click on the folder with the username you had on the old partition and click copy
Browse to your usb, create a new dir, go there and click paste.

---

### Post by poolhustler on 2012-05-15
Thank you very much, you just saved me lots of trouble, work and time! Have a great day!

---

