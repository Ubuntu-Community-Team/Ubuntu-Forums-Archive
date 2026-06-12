---
title: "Accessing Windows files from Ubuntu"
date: 2010-07-09
forum: General Help
---

### Post by BlackedOut271 on 2010-07-09
I would like to access my windows files while logged into Ubuntu. I searched for solutions and found multiple answers. The only solution that worked for me was to open a terminal window and input the following:

derek@ubuntu:~$ cd /mnt
derek@ubuntu:/mnt$ sudo mkdir windrive
[sudo] password for derek: 
mkdir: cannot create directory `windrive': File exists
derek@ubuntu:/mnt$ sudo mount -t ntfs /dev/sda1 /mnt/windrive -o "unmask=022"

This created a folder called "windrive" and then 'mounted' the files from my hardrive into the folder.

The issue I have now is that once I shut down my machine and log back in, the files are gone. I then have to open a Terminal Window and redo the above. I know with the Windows Command Prompt you can save your actions as a .exe (I think) Is there a similar method using Ubuntu?

I read that Samba was useful for what I am hoping to accomplish, but I can't figure it out. I went to the Ubuntu Software Center and downloaded 'Samba' (pretty sure it is the correct sofware) but can't figure out how to use it.

So, I am hoping somebody can give me advice on the best way to access my Windows files from Ubuntu, as well as any suitable programs (and how to use them). Thanks in advance!

Software:
Ubuntu 10.04 LTS 64-bit
Windows 7 Ultimate

---

### Post by sisco311 on 2010-07-09
Hi and welcome to the forums!

You can mount Windows drives through the Places menu. See:
[http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

---

### Post by Darkness Des on 2010-07-09
Erm, More directly to what you wanted to do, copy and paste this into a .sh file
```

#!/bin/bash
if [ -e /mnt/windrive ]; then
    sudo mount -t ntfs /dev/sda1 /mnt/windrive -o "unmask=022"
else
    cd /mnt
    sudo mkdir windrive
    sudo mount -t ntfs /dev/sda1 /mnt/windrive -o "unmask=022"
fi

echo "/dev/sda1 has been mounted at /mnt/windrive."
```
Then, cd to the directory where that is and chmod +x it. That's the equivalent of a .bat (and sometimes .exe) file in windows. The .sh extension isn't needed, or an extension at all, but it's considered good form. To use this script, cd to the directory where it is, and type in
```
./script-name.sh
```
but replace script-name.sh with whatever you named your script.

---

### Post by BlackedOut271 on 2010-07-09
> **Darkness Des said:**
> Erm, More directly to what you wanted to do, copy and paste this into a .sh file
```

#!/bin/bash
if [ -e /mnt/windrive ]; then
    sudo mount -t ntfs /dev/sda1 /mnt/windrive -o "unmask=022"
else
    cd /mnt
    sudo mkdir windrive
    sudo mount -t ntfs /dev/sda1 /mnt/windrive -o "unmask=022"
fi

echo "/dev/sda1 has been mounted at /mnt/windrive."
```Then, cd to the directory where that is and chmod +x it. That's the equivalent of a .bat (and sometimes .exe) file in windows. The .sh extension isn't needed, or an extension at all, but it's considered good form. To use this script, cd to the directory where it is, and type in
```
./script-name.sh
```but replace script-name.sh with whatever you named your script.

Thanks for taking the time to help me out! How do I create a .sh file? And will I have to do this every time I login to Ubuntu?

---

### Post by BlackedOut271 on 2010-07-09
> **sisco311 said:**
> Hi and welcome to the forums!

You can mount Windows drives through the Places menu. See:
[http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

I tried this and it mounts the Factory Image partition just fine but won't mount the one I want it too. I'll keep playing around. Any suggestions?

---

### Post by sisco311 on 2010-07-09
> **BlackedOut271 said:**
> I tried this and it mounts the Factory Image partition just fine but won't mount the one I want it too. I'll keep playing around. Any suggestions?

Would you like to mount the partition at boot time or manually after you log in?

---

### Post by Morbius1 on 2010-07-09
And the reason you're not adding a line in fstab to mount this at boot is why?

Unmount /mnt/windrive if it is currently mounted:
```
sudo umount /mnt/windrive
```Make sure the mountpoint is present:
```
sudo mkdir /mnt/windrive
```Add a line in fstab:
```
gksu gedit /etc/fstab
```> /dev/sda1 /mnt/windrive  ntfs    defaults,nls=utf8,umask=022 0       0Save fstab, exit gedit, and back in the terminal type:
```
sudo mount -a
```You'll know instantly if it works.

BTW, with your original mount command and the one presented here in fstab, only root will have write access. Not sure that's what you want.

If you run into difficulties post the output of the following commands so we can see what's up:
```
sudo blkid -c /dev/null
cat /etc/fstab
```

---

### Post by BlackedOut271 on 2010-07-09
> **Darkness Des said:**
> Erm, More directly to what you wanted to do, copy and paste this into a .sh file
```

#!/bin/bash
if [ -e /mnt/windrive ]; then
    sudo mount -t ntfs /dev/sda1 /mnt/windrive -o "unmask=022"
else
    cd /mnt
    sudo mkdir windrive
    sudo mount -t ntfs /dev/sda1 /mnt/windrive -o "unmask=022"
fi

echo "/dev/sda1 has been mounted at /mnt/windrive."
```Then, cd to the directory where that is and chmod +x it. That's the equivalent of a .bat (and sometimes .exe) file in windows. The .sh extension isn't needed, or an extension at all, but it's considered good form. To use this script, cd to the directory where it is, and type in
```
./script-name.sh
```but replace script-name.sh with whatever you named your script.

I figured out what you were telling me to do. However, once I type the ./script-name.sh (which was ./mountwin.sh) it said permission denied...

---

### Post by BlackedOut271 on 2010-07-09
> **sisco311 said:**
> Would you like to mount the partition at boot time or manually after you log in?

Boot time

---

### Post by audiomick on 2010-07-09
> **BlackedOut271 said:**
> Boot time
The advice from Morbius1 in post #7 should achieve that, I think.

---

### Post by BlackedOut271 on 2010-07-09
> **Morbius1 said:**
> And the reason you're not adding a line in fstab to mount this at boot is why?

Unmount /mnt/windrive if it is currently mounted:
```
sudo umount /mnt/windrive
```Make sure the mountpoint is present:
```
sudo mkdir /mnt/windrive
```Add a line in fstab:
```
gksu gedit /etc/fstab
```Save fstab, exit gedit, and back in the terminal type:
```
sudo mount -a
```You'll know instantly if it works.

...


When I try to save the fstab file (using gedit) it tells me it is read-only... "You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

What do I do :( Way around this? I tried right-clicking on the fstab file and changing the permissions but it will not allow me.

---

### Post by sisco311 on 2010-07-09
> **BlackedOut271 said:**
> Boot time

See Morbius1's post. 

VFAT/NTFS partitions do not support Unix/Linux ownership and file permissions. You have to set the owner/group and permissions at mount time. The ownership and permissions will apply to all files and directories on the partition.

The fourth field of the entry describes the mount options associated with the filesystem.

uid= Sets owner. Syntax: may use user_name or user ID #.
gid= sets group ownership of mount point. Again may use group_name or GID #.

umask= Sets the umask (the bitmask of the permissions that are not present).
dmask= Sets the umask applied to directories only.
fmask= Set the umask applied to regular files only.

Syntax is "odd" at first.
To set a permissions of 777, umask=000
To set permissions of 700, umask=077

e.g.
```
UUID=**xxxx**    /mnt/windrive    ntfs    defaults,dmask=002,fmask=113,gid=plugdev    0    0
```

This entry will mount the partition with read/write permissions for the group plugdev and read permissions for other. The first user is, by default, in the plugdev group, to grant write access for another user add it to the plugdev group:
```
sudo gpasswd -a user plugdev
```

**xxxx** is the UUID of the partition. To get the UUID run:
```
sudo blkid -c /dev/null -o list  /dev/sda1
```

---

### Post by Morbius1 on 2010-07-09
> When I try to save the fstab file (using gedit) it tells me it is  read-only... "You do not have the permissions necessary to save the  file. Please check that you typed the location correctly and try again."

Open a terminal and type:
```
gksu gedit /etc/fstab
```
You can only edit this file as root.

---

### Post by BlackedOut271 on 2010-07-09
> **Morbius1 said:**
> Open a terminal and type:
```
gksu gedit /etc/fstab
```You can only edit this file as root.

No luck. Here is the outcome of my terminal window...

```

derek@ubuntu:~$ sudo mount -a
mount: mount point gedit does not exist
derek@ubuntu:~$ cd /mnt/windrive
derek@ubuntu:/mnt/windrive$ sudo mount -a
mount: mount point gedit does not exist
derek@ubuntu:/mnt/windrive$ sudo blkid -c /dev/null
/dev/loop0: UUID="8aec6c9b-0a30-4302-b948-9c3fa8d9a629" TYPE="ext4" 
/dev/sda1: LABEL="HP" UUID="CECE7327CE73074D" TYPE="ntfs" 
/dev/sda2: LABEL="FACTORY_IMAGE" UUID="949CA48C9CA46A86" TYPE="ntfs" 
derek@ubuntu:/mnt/windrive$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sda1    /host    ntfs    defaults,nls=utf8,umask=0222,nosuid,nodev    00
/dev/sda2    /media/FACTORY_IMAGE    ntfs    defaults,nls=utf8,umask=0222    00
/host/ubuntu/disks/root.disk    /    ext4    loop,errors=remount-ro    0    1
/host/ubuntu/disks/swap.disk    none    swap    loop,sw    0    0

gksu gedit /etc/fstab


derek@ubuntu:/mnt/windrive$ 

```

---

### Post by Morbius1 on 2010-07-09
I made two mistakes. 

First, I can't read. Your using KDE so there is no gedit.

Second, You know I had a gut feeling this was a Wubi install. Should have asked.

Go into dolphin or whatever the file manger is in KDE these days and go to the following folders to see if you can find the windows partition:
> /host
/media

---

### Post by BlackedOut271 on 2010-07-09
> **Morbius1 said:**
> I made two mistakes. 

First, I can't read. Your using KDE so there is no gedit.

Second, You know I had a gut feeling this was a Wubi install. Should have asked.

Go into dolphin or whatever the file manger is in KDE these days and go to the following folders to see if you can find the windows partition:

I have Ubuntu 10.04. I think it's GNOME right? Kubunu is KDE?

---

### Post by sisco311 on 2010-07-09
> **BlackedOut271 said:**
> No luck. Here is the outcome of my terminal window...

```

derek@ubuntu:~$ sudo mount -a
mount: mount point gedit does not exist
derek@ubuntu:~$ cd /mnt/windrive
derek@ubuntu:/mnt/windrive$ sudo mount -a
mount: mount point gedit does not exist
derek@ubuntu:/mnt/windrive$ sudo blkid -c /dev/null
/dev/loop0: UUID="8aec6c9b-0a30-4302-b948-9c3fa8d9a629" TYPE="ext4" 
/dev/sda1: LABEL="HP" UUID="CECE7327CE73074D" TYPE="ntfs" 
/dev/sda2: LABEL="FACTORY_IMAGE" UUID="949CA48C9CA46A86" TYPE="ntfs" 
derek@ubuntu:/mnt/windrive$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sda1    /host    ntfs    defaults,nls=utf8,umask=0222,nosuid,nodev    00
/dev/sda2    /media/FACTORY_IMAGE    ntfs    defaults,nls=utf8,umask=0222    00
/host/ubuntu/disks/root.disk    /    ext4    loop,errors=remount-ro    0    1
/host/ubuntu/disks/swap.disk    none    swap    loop,sw    0    0

gksu gedit /etc/fstab


derek@ubuntu:/mnt/windrive$ 

```

*gksu gedit /etc/fstab* is a command for opening the fstab file as root in the text editor. Remove it from the fstab file. 

Wubi by default mounts the Windows partition, with read only permissions, in the /host directory.

This is the relevant line from the fstab file:
```
/dev/sda1    /host    ntfs    defaults,nls=utf8,umask=0222,nosuid,nodev    0     0
```

EDIT:
You have create another entry for the windows partition:
```
/dev/sda1    /mnt/windrive    ntfs    defaults,dmask=002,fmask=113,gid=plugdev    0    0
```

If you want the windows partition to show up in the places menu, then mount it in the /media directory:
```
/dev/sda1    **/media/windrive**    ntfs    defaults,dmask=002,fmask=113,gid=plugdev    0    0
```
Just make sure that the mount point exists:
```
sudo mkdir /media/windrive
```

---

### Post by BlackedOut271 on 2010-07-09
> **Morbius1 said:**
> I made two mistakes. 

First, I can't read. Your using KDE so there is no gedit.

Second, You know I had a gut feeling this was a Wubi install. Should have asked.

Go into dolphin or whatever the file manger is in KDE these days and go to the following folders to see if you can find the windows partition:

Okay, night not matter, but I stumbled upon the fact that I can access the windows files by navigating to /host. I'm guessing this is because it was a Wubi install (should have mentioned that before). I'll try the above. I would like it to show in Places...

---

### Post by BlackedOut271 on 2010-07-09
> **sisco311 said:**
> *gksu gedit /etc/fstab* is a command for opening the fstab file as root in the text editor. Remove it from the fstab file. 

Wubi by default mounts the Windows partition, with read only permissions, in the /host directory.

This is the relevant line from the fstab file:
```
/dev/sda1    /host    ntfs    defaults,nls=utf8,umask=0222,nosuid,nodev    0     0
```You have to edit this line to fit your needs, e.g:
```
/dev/sda1    /mnt/windrive    ntfs    defaults,dmask=002,fmask=113,gid=plugdev    0    0
```If you want the windows partition to show up in the places menu, then mount it in the /media directory:
```
/dev/sda1    **/media/windrive**    ntfs    defaults,dmask=002,fmask=113,gid=plugdev    0    0
```Just make sure that the mount point exists:
```
sudo mkdir /media/windrive
```

Alright, I created the 'windrive' folder inside the 'media' folder. I changed the line of code in the fstab file to read:
```
/dev/sda1       /media/windrive         ntfs    defaults,dmask=002,fmask=113,gid=plugdev    0    0
```

The Windows files are still in the /host directory. How do I get them into the /media directory?

---

### Post by sisco311 on 2010-07-09
> **BlackedOut271 said:**
> Alright, I created the 'windrive' folder inside the 'media' folder. I changed the line of code in the fstab file to read:
```
/dev/sda1       /media/windrive         ntfs    defaults,dmask=002,fmask=113,gid=plugdev    0    0
```

The Windows files are still in the /host directory. How do I get them into the /media directory?

Oh, sorry, edit the fstab file to:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sda1    /host    ntfs    defaults,nls=utf8,umask=0222,nosuid,nodev    00
/dev/sda2    /media/FACTORY_IMAGE    ntfs    defaults,nls=utf8,umask=0222    00
/host/ubuntu/disks/root.disk    /    ext4    loop,errors=remount-ro    0    1
/host/ubuntu/disks/swap.disk    none    swap    loop,sw    0    0

/dev/sda1       /media/windrive         ntfs    defaults,dmask=002,fmask=113,gid=plugdev    0    0
```

Wubi must be able to access the the disk image files from /host/ubuntu/disks/.

---

### Post by BlackedOut271 on 2010-07-09
> **sisco311 said:**
> Oh, sorry, edit the fstab file to:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sda1    /host    ntfs    defaults,nls=utf8,umask=0222,nosuid,nodev    00
/dev/sda2    /media/FACTORY_IMAGE    ntfs    defaults,nls=utf8,umask=0222    00
/host/ubuntu/disks/root.disk    /    ext4    loop,errors=remount-ro    0    1
/host/ubuntu/disks/swap.disk    none    swap    loop,sw    0    0

/dev/sda1       /media/windrive         ntfs    defaults,dmask=002,fmask=113,gid=plugdev    0    0
```Wubi must be able to access the the disk image files from /host/ubuntu/disks/.

So here is what my fstab looks like now:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sda1    /host            ntfs    defaults,nls=utf8,umask=0222,nosuid,nodev    0    0
/dev/sda2    /media/FACTORY_IMAGE    ntfs    defaults,nls=utf8,umask=0222    0    0
/host/ubuntu/disks/root.disk    /    ext4    loop,errors=remount-ro    0    1
/host/ubuntu/disks/swap.disk    none    swap    loop,sw    0    0

/dev/sda1    /media/windrive        ntfs    defaults,dmask=002,fmask=113,gid=plugdev    0    0
```

Still not showing up in my Places... When I navigate to /media , the files are there though. Just had to restart my machine. So I guess the last thing I need to do is get the /media/windrive to show in the Places area.

---

### Post by BlackedOut271 on 2010-07-09
I just used the old 'drag and drop' technique in the file browser and drug the 'windrive' directory onto the left panel. Now it shows up in places. Thank you so so so much for taking the time to assist me! I really appreciate it.

---

### Post by BlackedOut271 on 2010-07-09
Thanks Sisco for the permissions breakdown

---

### Post by sisco311 on 2010-07-09
You're welcome!

---

### Post by quimkaos on 2010-07-09
you should have listen to the 1st reply you had to your post blackedout, from sisco! He even points you to a tutorial! Install NTFS Configuration Tool (ntfs-config), and you wont have to manually config the fstab file. Thou that comment by darkness des must have been just to confuse you! haha

---

### Post by BlackedOut271 on 2010-07-09
> **quimkaos said:**
> you should have listen to the 1st reply you had to your post blackedout, from sisco! He even points you to a tutorial! Install NTFS Configuration Tool (ntfs-config), and you wont have to manually config the fstab file. Thou that comment by darkness des must have been just to confuse you! haha

Ya after all the work, I took a step back and reviewed. I figured out how to use the ntfs config. Much easier lol

---

### Post by Morbius1 on 2010-07-09
Although one could argue that since this was a Wubi install the windows partition was already mounted and present in fstab so there was no need to mount it again.

---

### Post by sisco311 on 2010-07-09
> **Morbius1 said:**
> Although one could argue that since this was a Wubi install the windows partition was already mounted and present in fstab so there was no need to mount it again.

True. It's probably a better solution to mount it once, under /host, with rw permissions for a user or group and symlink the /host dir to /media/windows or something. 


I was thinking a little more about this... /dev/sda1 holds the Windows installation. Granting rw permissions for a regular user to all the system files is a security risk. 

I would let /dev/sda1 to be mounted with read only permissions and use bindfs to remount the user's home directory (<root>\Documents and Settings\<username> or <root>\Users\<username>) with rw permissions. What do you think?

---

### Post by Morbius1 on 2010-07-10
> **sisco311 said:**
> I would let /dev/sda1 to be mounted with read only permissions and use bindfs to remount the user's home directory (<root>\Documents and Settings\<username> or <root>\Users\<username>) with rw permissions. What do you think?
You're the master of bindfs in this ( or any other ) forum. I have noticed a problem with binding things to my home folder though. I've tried it twice and it stops the booting process. The only way to recover was to boot into another OS ( I multiboot ) and remove the line. I don't know if this is another upstart problem like the one mentioned in your howto or simply user error. The same line works if I bind it to something outside my home directory however so a bindfs to /media/windrive should work.

The only other point is that in his original post BlackedOut271 was using the following line to mount the partitions manually:
> sudo mount -t ntfs /dev/sda1 /mnt/windrive -o "unmask=022"As a regular user he only had read access to the mountpoint and only wanted a way to make it mount at boot to a location other than /host.

---

### Post by sisco311 on 2010-07-10
> **Morbius1 said:**
> You're the master of bindfs in this ( or any other ) forum. I have noticed a problem with binding things to my home folder though. I've tried it twice and it stops the booting process. The only way to recover was to boot into another OS ( I multiboot ) and remove the line. 

If it's an Upstart or mountall issue, you could try to write an Upstart job to make sure that bindfs runs after all partitions are mounted,
/etc/init/bindfs.conf:
```

#
#/etc/init/bindfs.conf
#

description     "run bindfs after all partitions are mounted"

start on mounted

script
bindfs [options] dir mountpoint
end script

```

---

### Post by Morbius1 on 2010-07-10
sisco311, Thanks I'll try that the next time.

---

