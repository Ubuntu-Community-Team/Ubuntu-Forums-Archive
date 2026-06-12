---
title: "HELP - External hard drive not working"
date: 2011-10-16
forum: General Help
---

### Post by mushy365 on 2011-10-16
I formatted my external hard drive as EXT4
When i run the command df -T i get
> 
Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/sda1     ext4    73900256  37886284  32260040  55% /
none      devtmpfs      506676       248    506428   1% /dev
none         tmpfs      512300      1292    511008   1% /dev/shm
none         tmpfs      512300       484    511816   1% /var/run
none         tmpfs      512300         0    512300   0% /var/lock
/dev/sdf1     ext4   237343424    191648 225095408   1% /media/EXT-1



Thats shows it there as /dev/sdf1 

In the /media folder i see the EXT-1 folder 
in /media if i do the command  ls -l i get 

> drw-r-xr-x 4 brian brian 4096 2011-10-16 22:25 EXT-1


in Nautilis i can click on folders and get into EXT-1
However in terminal if i do
brian@brian-movie-downloads:/media$ cd EXT-1
i get 
> bash: cd: EXT-1: Permission denied

if i try to create a folder in the eXT-1 folder in Nautilis i get an error permission denied

im not sure what these commands mean but i hope they help 

i did sudo fdisk -l
> 
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9347    75078656   83  Linux
/dev/sda2            9348        9730     3069953    5  Extended
/dev/sda5            9348        9730     3069952   82  Linux swap / Solaris



Help please

---

### Post by gsmanners on 2011-10-16
I think that's working as designed. For any ext2/3/4 filesystem, you really need to create your first folder or two from a root shell or by using sudo mkdir. Then use sudo chown to let users access it.

---

### Post by mushy365 on 2011-10-16
But it wont even let me access the EXT-1 folder in media to create a new folder

---

### Post by Leaf on 2011-10-16
Looks like you might need make a directory using the superuser.
try sudo su then the root pass to get to a root shell, then see if you can navigate to the EXT-1 folder.

---

### Post by mushy365 on 2011-10-16
ok ive got a root shell and ive made a folder on the EXT-1 folder called music
the owner of EXT-1 is the user brian  
the owner of music is root

do i need to change the owner of EXT-1 to root?

---

### Post by Leaf on 2011-10-16
Ok, now that you've got your access to EXT-1 you'll need to use chown to CHange OWNership of the folders.
[http://www.computerhope.com/unix/uchown.htm](http://www.computerhope.com/unix/uchown.htm)
Then you can set additional options (readonly, etc.) using Chmod
[http://www.computerhope.com/unix/uchmod.htm](http://www.computerhope.com/unix/uchmod.htm)

These are a good rundown of what you'll need to use.

for example if you wanted to change ownership of the whole EXT-1 drive, while in the /media folder run
sudo chown -R brian EXT-1
Which will make user brian the owner of that file and all contained (that's the -R flag, it means to recursively select all folders contained)
Then, if you wanted to make the folders readable/writable by anyone you'd sudo chmod -R 666 EXT-1
the 666 is the octal code that refers to whom has what permissions.

---

### Post by mushy365 on 2011-10-16
cheers, i have it running properly now, its set up and shared over network on samba server. Thanks.

---

