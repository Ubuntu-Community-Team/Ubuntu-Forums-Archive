---
title: "User's $HOME/.dmrc file is being ignored ;_;"
date: 2009-07-30
forum: General Help
---

### Post by Blu Fox on 2009-07-30
Yeah, I recently tried to partition my hard drive so my home folder can have it's own cozy partition (since so many members on here recommend it). I followed [this]("http://www.psychocats.net/ubuntu/separatehome") website's instruction and when I reboot, I get this message:

"User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users" 

After I click ok on that message, it doesn't logs in or anything, just a black screen with a movable mouse :<

I would like help as simple as possible since I'm a flat out linux/ubuntu noob, seriously I suck at this.

---

### Post by merlinus on 2009-07-30
Enter these commands in a terminal, and you should be good to go:

```
chmod 644 /home/username/.dmrc
chmod 755 /home/username
```You may have to add sudo before each, if you get an error message, and substitute your actual username for username.

---

### Post by Blu Fox on 2009-07-30
Tried entering the first one but all I get is this
```
chmod: cannot access `/home/franky/.dmrc': No such file or directory

```
*was assuming that I had to replace 'username' with my username which is franky..duh*

I'm using a live CD right now, if that makes any difference.

---

### Post by merlinus on 2009-07-30
It won't work from the live cd, because your linux partition is not mounted.  Startup and login as usual, ignoring the error message, and follow the steps I suggested.

---

### Post by Blu Fox on 2009-07-30
That's the thing, I can't really log in. Just gives me a black screen with a mouse and nothing else.

---

### Post by Blu Fox on 2009-07-30
Should I just do a reinstall? I have my home folder on a separate partition anyways and I still have backup DVD's with my music and stuff. I hope I don't have to but if I do, then I will...less someone can still help

---

### Post by Blu Fox on 2009-07-31
nvm. I just reinstalled. 1st reinstall, woohoo...

---

### Post by nothingspecial on 2009-07-31
Just so you know for next time.

When the grub loading dialogue appears press escape and you will be able to boot into recovery mode. You could then have issued those commands and saved your install.

---

### Post by Rob_BCN on 2009-08-09
Hi all,

I have exactly the same problem: I tired to move my partition following the instructions at the psychocats page and got the same error. 

I have tried the fixes mentioned there and those I found at [http://how2ubun2.blogspot.com/2009/06/how-to-solve-dmrc-and-home-permission.html](http://how2ubun2.blogspot.com/2009/06/how-to-solve-dmrc-and-home-permission.html) (which includes those given above), but nothing works.

Any ideas?

Thanks in advance.

---

### Post by mcduck on 2009-08-09
> **nothingspecial said:**
> Just so you know for next time.

When the grub loading dialogue appears press escape and you will be able to boot into recovery mode. You could then have issued those commands and saved your install.

Or press Ctrl-Alt-F1 to drop into TTY to run the commands, since they don't require recovery mode and logging in to a terminal should still be possible even with .dmrc permission problems.

---

### Post by CaptainMark on 2009-08-09
failing that it is possible to chmod your home folder from the live cd just run ```
sudo fdisk -l
```to get the name of your harddrive usually /dev/sda1 then run ```
sudo mkdir /mnt/hdd
sudo mount /dev/sda1 /mnt/hdd
```making sure you change sda1 for whatever your main partition is called. after mounting hdd you can run an altered version of the last code ```
sudo chmod 644 /mnt/hdd/home/username/.dmrc
sudo chmod 755 /mnt/hdd/home/username
```making sure you change username to your actual username. Correct me if im wrong im still fairly new to this also, 
Unmount then reboot

---

### Post by Rob_BCN on 2009-08-09
Hi Mark,

I just tried your suggestion from the live CD and got the same result: cannot access '/mnt/hdd/home/rob/': No such file or directory.

I tired on both partitions where home might be: sdb3 (the 'new' home partition) and sdb1 (the root partition where home was (or still is--I don't know)).

---

### Post by CaptainMark on 2009-08-09
if youve mounted it correctly can you access it by clicking places>computer>file system>mnt>hdd?

---

### Post by Rob_BCN on 2009-08-09
Yes. When I mount sdb1, I can access it in places>computer>file system>mnt>hdd.

---

### Post by martinbaselier on 2009-08-09
If you follow CaptainMark's instructions for mounting from the livecd. 

What does **cat /mnt/hdd/etc/fstab** show ?

I have a feeling something is wrong there. Either that or you have a /home/ directory in your /home/ directory. 

Mount your home partition in the same way as your root partition, and it check if it does not contain a /home/ folder

---

### Post by Rob_BCN on 2009-08-09
**cat /mnt/hdd/etc/fstab** shows this:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=fd6f58d4-1a53-4153-837c-f39574d297d7 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=d22d31ae-3e58-40a2-99e7-5393ea4cfc9f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by CaptainMark on 2009-08-10
whats the output from ```
sudo ls -lah /mnt/hdd/
```and also ```
sudo ls -lah /mnt/hdd/home
```

---

### Post by Rob_BCN on 2009-08-10
For 

     ```
sudo ls -lah /mnt/hdd/ 
```I get: 

```
total 112K
drwxr-xr-x  24 root root 4.0K 2009-08-08 15:26 .
drwxr-xr-x   3 root root   60 2009-08-10 18:32 ..
drwxr-xr-x   2 root root 4.0K 2009-07-14 18:57 bin
drwxr-xr-x   3 root root 4.0K 2009-07-30 20:31 boot
lrwxrwxrwx   1 root root   11 2009-06-27 14:15 cdrom -> media/cdrom
drwxr-xr-x   4 root root 4.0K 2009-04-20 14:06 dev
drwxr-xr-x 137 root root  12K 2009-08-09 08:19 etc
drwxr-xr-x   3 root root 4.0K 2009-08-08 16:44 home
drwxr-xr-x   4 root root 4.0K 2009-08-08 15:26 home_backup
lrwxrwxrwx   1 root root   33 2009-07-30 20:31 initrd.img -> boot/initrd.img-2.6.28-14-generic
lrwxrwxrwx   1 root root   33 2009-06-27 14:49 initrd.img.old -> boot/initrd.img-2.6.28-13-generic
drwxr-xr-x  19 root root 4.0K 2009-07-18 14:39 lib
drwx------   2 root root  16K 2009-06-27 14:15 lost+found
drwxr-xr-x   3 root root 4.0K 2009-08-09 08:13 media
drwxr-xr-x   2 root root 4.0K 2009-04-13 09:33 mnt
drwxr-xr-x   2 root root 4.0K 2009-08-08 15:14 new
drwxr-xr-x   2 root root 4.0K 2009-08-08 15:14 old
drwxr-xr-x   2 root root 4.0K 2009-04-20 13:59 opt
drwxr-xr-x   2 root root 4.0K 2009-04-13 09:33 proc
drwx------  16 root root 4.0K 2009-08-08 16:38 root
drwxr-xr-x   2 root root 4.0K 2009-07-30 20:30 sbin
drwxr-xr-x   2 root root 4.0K 2009-03-06 16:21 selinux
drwxr-xr-x   2 root root 4.0K 2009-04-20 13:59 srv
drwxr-xr-x   2 root root 4.0K 2009-03-31 09:02 sys
drwxrwxrwt   6 root root 4.0K 2009-08-09 08:19 tmp
drwxr-xr-x  12 root root 4.0K 2009-06-30 21:24 usr
drwxr-xr-x  15 root root 4.0K 2009-04-20 14:07 var
lrwxrwxrwx   1 root root   30 2009-07-30 20:31 vmlinuz -> boot/vmlinuz-2.6.28-14-generic
lrwxrwxrwx   1 root root   30 2009-06-27 14:49 vmlinuz.old -> boot/vmlinuz-2.6.28-13-generic
```And for:

```
sudo ls -lah /mnt/hdd/home
```I get:

```
total 12K
drwxr-xr-x  3 root root 4.0K 2009-08-08 16:44 .
drwxr-xr-x 24 root root 4.0K 2009-08-08 15:26 ..
drwxr-xr-x  4 root root 4.0K 2009-08-08 16:44 home_backup
```Rob

---

### Post by CaptainMark on 2009-08-10
Your problem is you have no home directory for yourself, in /mnt/hdd you should find a directory called home, which is there, fine. In that directory should be a directory for each of the users of that partition, normally you would find /mnt/hdd/home/rob (when running live cd) or just /home/rob (when running from your hdd)
In other words you've not changed the permissions of your .dmrc file, wherever it is, chances are, its okay. It's been moved somewhere by mistake, or if your really unlucky, deleted.
What id recommend from here is to try and find your home folder (your videos and music and everything) try mounting your hdd from the live cd and run a search for a file name that you know will be in the home folder.
You do seem to have 2 directories called home_backup ones in /mnt/hdd and anothers in /mnt/hdd/home
Check in these, post back

---

### Post by Rob_BCN on 2009-08-10
Ok, I have 2 copies of my home: 1 at mnt/hdd/home/home_backup/rob and the other at: mnt/hdd/home_backup/rob -- they both contain the same things. It looks like it was what martinbaselier said it might be: my home is in my home.

This is all in sdb1. The reason I got myself into this was that I was trying to move my home to a separate partition, sbd3. When I mount sbd3, I can't open it because I'm not the owner. Is it possible I also managed to copy a home there too but I messed up with something else?

Thanks for you help, anyway. I'm pretty lost with this.

---

### Post by CaptainMark on 2009-08-11
Dont worry just move your home file back to where its meant to be so the path is complete /mnt/hdd/home/rob/documents(etc.) 
try rebooting, if that doesnt boot fine then go back to the beginning of this post and do the chmod commands, that should sort you.

---

### Post by michy99 on 2009-08-11
> **CaptainMark said:**
> Dont worry just move your home file back to where its meant to be so the path is complete /mnt/hdd/home/rob/documents(etc.) 
try rebooting, if that doesnt boot fine then go back to the beginning of this post and do the chmod commands, that should sort you.

The home directory should NOT be at /mnt/hdd/home/rob, it should be at /home/rob.

---

### Post by CaptainMark on 2009-08-12
thanks for you help michy99 your right, but if you backtrack through this thread rob asked if we could restore his home file from a live cd and i already instructed him to mount his hdd in /mnt/hdd, hence /mnt/hdd/home/rob

---

### Post by Rob_BCN on 2009-08-12
Ok, I might be getting somewhere now.

I moved rob to: mnt/hdd/home and ran:

```
chmod 644 /home/username/.dmrc
chmod 755 /home/username
```and got no error messages as I had before.

When I rebooted, the system ran a disk check before giving me the usual 'User's $HOME/.dmrc file' message. It then did something different. It displayed a message which said:

> Could not update ICE authority file /home/rob/.ICEauthorityAnd then another message:

> There is a problem with the configuration server (usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)I had a quick look on the Internet and tried running the commands below to fix the first problem: 

```
chown rob:rob mnt/hdd/home/rob/.ICEauthority
chmod 644 mnt/hdd/home/rob/.ICEauthority
exit
```But I got errors on both ('invalid user' on the first and 'no such file' for the second).

---

### Post by CaptainMark on 2009-08-12
if your booting from the hard drive now you need to drop the /mnt/hdd your now dealing with just /home/rob if your not on the live disk. 
you can try those commands again without the /mnt/hdd but honestly i dont know about this new issue, its something ive never come across but it sounds like a permissions problem, on my setup /usr/lib/libgconf2-4/gconf-sanity-check-2 has permissions of 755.
Try this code ```
sudo chmod 755 /usr/lib/libgconf2-4/gconf-sanity-check-2
``` its worth a shot, im sort of stabbing in the dark now. 
also you need to run the chmod commands with sudo rights```
sudo chmod 644 /home/rob/.dmrc
sudo chmod 755 /home/rob
``` that should drop your .drmc error message, after that im stumped but im new to this also, maybe someone else can help. Maybe open another post with the new error message.
Good luck and happy ubuntuing
ps. when you have ubuntu and you cant resist playing with it, make sure before you do, your fully prepared to reinstall, ive got my reinstalation and reconfiguration time down to 70 mins,

---

### Post by Rob_BCN on 2009-08-13
I'll give that command a shot and see how it goes.

If not, reinstalling is not a problem. I was planning on doing it this weekend when I had more time if I couldn't get it sorted out before then.

I might look around or post somewhere else, but it's proabably easier to reinstall and start again.

Thanks for you help anyway. I have actually learned something in the process (not difficult as a knew next to nothing beforehand).

Rob

---

