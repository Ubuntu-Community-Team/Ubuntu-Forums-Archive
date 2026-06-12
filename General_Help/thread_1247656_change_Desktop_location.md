---
title: "change Desktop location"
date: 2009-08-23
forum: General Help
---

### Post by guss606 on 2009-08-23
Hi all.. 

I have UNR 9.04 installed.. I want to change the Desktop location from */home/guss* to */media/DATA/Desktop* 

How can I do that?? 
Thanks guys

---

### Post by P4man on 2009-08-23
google on "ubuntu change desktop location" gives me this:
[http://ubuntuforums.org/showthread.php?t=173097](http://ubuntuforums.org/showthread.php?t=173097)

---

### Post by guss606 on 2009-08-23
I tried *sudo mount -o bind /home/guss /media/DATA/Desktop*, logged out and logged in but nothing happend.. 
Any ideas.. please I need to do that

---

### Post by guss606 on 2009-08-23
OMG OMG OMG... WHAT I'VE DONE.. 
I lost my orginal file Desktop.. 

I want it back... what should i do.. pleaseeeee help

---

### Post by michy99 on 2009-08-23
What is the output of these commands?```
ls ~
mount
```

---

### Post by P4man on 2009-08-23
You moved your entire homefolder I think!

reboot should bring it back to normal though. Then try

```
sudo mount -o bind /media/DATA/Desktop /home/guss/Desktop 
```

---

### Post by guss606 on 2009-08-23
Thank you very much guys for your help... 
P4man: Thats exactly what I did and it worked perfectly... Thanks again

---

### Post by P4man on 2009-08-24
dont forget to modify your fstab if you want to make this permanent. This mount command will only last until the next boot. And sure make not to make typo's or forget parts or reverse the order when you edit fstab!

---

### Post by guss606 on 2009-08-24
Yes man,, that mount lasted untill I reboot my computer, POOH, it's gone.. 
I was goin to ask here about how to make this permenantly?? I know that I am bothering you alot, but if you can explain me in details how to do that.. 
Thank you in advance.

---

### Post by P4man on 2009-08-24
open a terminal and type:
```
gksudo gedit /etc/fstab
```

add this line to the file:
```

/media/DATA/Desktop /home/guss/Desktop auto bind 0 0
```

Copy paste it so you make no typo's (and check the locations, to make sure I didnt make any typo's :) ). remember everything is case sensitive.

---

### Post by guss606 on 2009-08-29
Hi man, 
Thank you for this,, I have made exactly what you told me about making this thing permenantly, but still each time i reboot its gone,,, so each time i reboot I have to mount partition ***DATA*** and write ***sudo mount -o bind /media/DATA/Desktop /home/guss/Desktop*** in terminal to make it work... 
Do you have any solution to make this always work without all this fuss each time i reboot??!!

---

### Post by guss606 on 2009-08-30
Help !!!

---

### Post by P4man on 2009-08-30
show me your fstab.

---

### Post by guss606 on 2009-08-30
how do i do that?

---

### Post by P4man on 2009-08-30
```
cat /etc/fstab
```

---

### Post by guss606 on 2009-08-30
guss@guss-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=c37f5942-7c5a-4892-b759-3144d09a26f6 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=7fdc9abe-f0f5-4ace-a21a-cbfd8f679dae none            swap    sw              0       0
/media/DATA/Desktop /home/guss/Desktop auto bind 0 0

---

### Post by P4man on 2009-08-30
ok you added the mount command for Desktop, but you're not mounting data, so i guess thats doomed to fail. We'll need to add a line to mount DATA before you mount the desktop there.

Can you provide the output of:

```
mount
``` 

and

```
sudo blkid
```

---

### Post by guss606 on 2009-08-30
guss@guss-laptop:~$ mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/guss/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=guss)
/dev/sda3 on /media/DATA type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)






guss@guss-laptop:~$ sudo blkid
[sudo] password for guss: 
/dev/sda1: UUID="C4BEF1EABEF1D540" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="7A0A329E0A3256FB" LABEL="OS" TYPE="ntfs" 
/dev/sda3: UUID="EC94A38294A34E40" LABEL="DATA" TYPE="ntfs" 
/dev/sda5: UUID="c37f5942-7c5a-4892-b759-3144d09a26f6" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="7fdc9abe-f0f5-4ace-a21a-cbfd8f679dae"




P.S.  DATA is already mounted in this session.

---

### Post by P4man on 2009-08-30
Ok, I hope im getting this right :)

edit your fstab:

> gksudo gedit /etc/fstab

add this line before the line where you mount the Desktop:

```
UUID=EC94A38294A34E40 /media/DATA ntfs-3g quiet,defaults,rw 0 0
```
So it looks like:

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda5 during installation
UUID=c37f5942-7c5a-4892-b759-3144d09a26f6 / ext3 relatime,errors=remount-ro 0 1

# mount ntfs partition as DATA:
UUID=EC94A38294A34E40 /media/DATA ntfs-3g quiet,defaults,rw 0 0

# mount swap
UUID=7fdc9abe-f0f5-4ace-a21a-cbfd8f679dae none swap sw 0 0

# mount Desktop in to DATA partition:
/media/DATA/Desktop /home/guss/Desktop auto bind 0 0
```

---

### Post by jjgomera on 2009-08-30
if you use gnome edit file /home/<user>/.config/user-dirs.dirs

and change the line to something as:

```
 XDG_DESKTOP_DIR="/media/DATA/Desktop"
```

you must too open **gconf-editor** and unchecked the checkbox apps/nautilus/preferences/desktop_is_home_dir

---

### Post by guss606 on 2009-08-31
Hello again..
P4man: I did exactly what you told me to do so it looks exactly like the code you wrote to me.. but still I have the same issue..

jjgomera: I also did that.. but no result..

Any ideas..



Do you recommend reinstalling Ubuntu again??

---

### Post by guss606 on 2009-09-01
Help !!

---

### Post by P4man on 2009-09-01
can you give a little bit more info :s ?
Is the DATA partition now mounted or not upon boot?
If it isnt, did you double and triple check the fstab for errors (including errors made by me) ? Can you still mount it manually ? If not, then you may have to boot windows to remove the "dirty bit" from the NTFS after a untidy shutdown.

---

### Post by guss606 on 2009-09-01
when I installed Ubuntu I opened the DATA partition and it asked me for authoraisation and I gave it the password and checked the first box (forgot what it says)...  and yeah I still can open it every time I open Ubuntu

---

### Post by P4man on 2009-09-01
you're not being very clear.. I still dont know if the data partition is mounted upon fresh boot or not? If its not, check the fstab

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

