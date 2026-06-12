---
title: "import xp file into ubuntu"
date: 2010-03-06
forum: General Help
---

### Post by toyoracer on 2010-03-06
Good day, I am a noobie. I have a dual boot xp ubuntu . I have mounted my xp disc.

I have cad program that I need to import files from xp  to ubuntu wine running same  cad program. I will be checking out linux cad programs Later in the mean time I want to use some programs I am familiar with while learning linux. So first how to import files. 

Also would it be logical to have a partition for these programs for better management and ease  of use? I have a 250GB drive for ubuntu  1- 40GB install  2- 5GB swap 3- 50GB /home which nothing seems to go to, the rest empty. used ext4.

Would appreciate any insight. Do i need to give more detail or is just the facts a better question.

---

### Post by flippo on 2010-03-06
What medium are your windows files on? (flash drive, Hard Drive, network storage, etc)

---

### Post by toyoracer on 2010-03-06
Xp is on 60GB NTFS

---

### Post by flippo on 2010-03-06
Hard drive?

please open a terminal and type these commands.  Post their output (they may prompt you for a password):
```
df -h
sudo blkid
sudo cat /etc/fstab
```

---

### Post by toyoracer on 2010-03-06
craig@craig-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              37G   14G   21G  41% /
udev                  502M  272K  502M   1% /dev
none                  502M  348K  501M   1% /dev/shm
none                  502M  192K  502M   1% /var/run
none                  502M     0  502M   0% /var/lock
none                  502M     0  502M   0% /lib/init/rw
none                   37G   14G   21G  41% /var/lib/ureadahead/debugfs
/dev/sda1              56G   47G  9.2G  84% /media/0CC88198C88180A6
/dev/sdb3              78G  184M   74G   1% /media/_home*
craig@craig-desktop:~$ sudo blkid
[sudo] password for craig: 
Sorry, try again.
[sudo] password for craig: 
/dev/sda1: UUID="0CC88198C88180A6" TYPE="ntfs" 
/dev/sdb1: UUID="5b6dbdda-f40c-414e-8bc8-ae103dd901aa" TYPE="ext4" 
/dev/sdb3: LABEL="/home*" UUID="0517fe33-f8d8-4a4f-bad5-2cb2eab502f2" TYPE="ext4" 
/dev/sdb5: UUID="52ad0587-c741-42d3-96a0-c8b8d34e0584" TYPE="swap" 
craig@craig-desktop:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=5b6dbdda-f40c-414e-8bc8-ae103dd901aa /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=52ad0587-c741-42d3-96a0-c8b8d34e0584 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
craig@craig-desktop:~$

---

### Post by flippo on 2010-03-06
Now we need to edit your fstab to tell it how to attach your windows drive to your ubuntu install, then we need to make a place for it and set it up.  Here are the terminal commands (if you want to know what they do ask)
```
sudo cp /etc/fstab /etc/fstab_backup
sudo echo "/dev/sda1 /media/WindowsXP ntfs-3g users,defaults 0 0" >> /etc/fstab
sudo mkdir /media/WindowsXP
sudo chown craig:craig /media/WindowsXP
sudo apt-get install ntfs-3g
sudo mount -a
```

should appear on your desktop (yay)

---

### Post by toyoracer on 2010-03-06
do I type that straight in or -enter- each line

---

### Post by flippo on 2010-03-06
enter after each line, one by one.  the apt-get command may prompt you Y/n answer y.

---

### Post by toyoracer on 2010-03-06
craig@craig-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              37G   14G   21G  41% /
udev                  502M  276K  502M   1% /dev
none                  502M  348K  501M   1% /dev/shm
none                  502M  192K  502M   1% /var/run
none                  502M     0  502M   0% /var/lock
none                  502M     0  502M   0% /lib/init/rw
none                   37G   14G   21G  41% /var/lib/ureadahead/debugfs
/dev/sda1              56G   47G  9.2G  84% /media/0CC88198C88180A6
/dev/sdb3              78G  184M   74G   1% /media/_home*
craig@craig-desktop:~$ sudo blkid
/dev/sda1: UUID="0CC88198C88180A6" TYPE="ntfs" 
/dev/sdb1: UUID="5b6dbdda-f40c-414e-8bc8-ae103dd901aa" TYPE="ext4" 
/dev/sdb3: LABEL="/home*" UUID="0517fe33-f8d8-4a4f-bad5-2cb2eab502f2" TYPE="ext4" 
/dev/sdb5: UUID="52ad0587-c741-42d3-96a0-c8b8d34e0584" TYPE="swap" 
craig@craig-desktop:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=5b6dbdda-f40c-414e-8bc8-ae103dd901aa /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=52ad0587-c741-42d3-96a0-c8b8d34e0584 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
craig@craig-desktop:~$ sudo cp /etc/fstab etc/fstab_backup
cp: cannot create regular file `etc/fstab_backup': No such file or directory
craig@craig-desktop:~$ sudo echo "/dev/sda1 /media/WindowsXP ntfs-3g users,defaults 0 0" >> /etc/fstab
bash: /etc/fstab: Permission denied
craig@craig-desktop:~$ sudo mkdir /media/WindowsXP
craig@craig-desktop:~$ sudo chown craig:craig /media/WindowsXP
craig@craig-desktop:~$ sudo apt-get install ntfs-3g
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfs-3g is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
craig@craig-desktop:~$ sudo mount -a
craig@craig-desktop:~$

---

### Post by flippo on 2010-03-06
Ooops, two pretty big errors there, one on my part.  Fortunately, they cancel each other out!

the line:```
sudo cp /etc/fstab etc/fstab_backup
```
should be:```
sudo cp /etc/fstab /etc/fstab_backup
```Note the /etc after each space

That was your screw up, heres mine:
instead of sudo echo ... type:
```
sudo su
<will be prompted for password...>
echo "/dev/sda1 /media/WindowsXP ntfs-3g users,defaults 0 0" >> /etc/fstab
exit
```

So:
first do the sudo cp command
then do the sudo su, echo, exit commands

Afterwards try:
sudo mount -a

In the future if you enter a command and get an error DO NOT continue, it can do bad things.

---

### Post by toyoracer on 2010-03-06
craig@craig-desktop:~$ sudo cp /etc/fstab /etc/fstab_backup
craig@craig-desktop:~$ sudo su
root@craig-desktop:/home/craig# echo "/dev/sda1 /media/WindowsXP ntfs-3g users,defaults 0 0" >> /etc/fstab
root@craig-desktop:/home/craig# exit
exit
craig@craig-desktop:~$

---

### Post by flippo on 2010-03-06
Looks good so far now just open a terminal and type:```
sudo mount -a
```

Your XP drive should pop up on your desktop, and it will automatically pop up there every time you log on afterwards.

---

### Post by toyoracer on 2010-03-06
craig@craig-desktop:~$ sudo mount -a
craig@craig-desktop:~$

---

### Post by flippo on 2010-03-06
Did the WindowsXP directory pop up on your desktop?

If not what happens when you type:```
sudo ls -al /media/WindowsXP
```

---

### Post by toyoracer on 2010-03-06
craig@craig-desktop:~$ sudo ls -al /media/WindowsXP
total 3240607
drwx------ 1 craig craig       8192 2010-03-04 17:48 .
drwxr-xr-x 8 root  root        4096 2010-03-06 19:48 ..
-rwxrwxrwx 1 craig craig        205 2010-01-08 20:20 3pi.htm
-rwxrwxrwx 2 craig craig 2530975744 2009-05-31 21:51 7100.0.090421-1700_x86fre_client_en-us_retail_ultimate-grc1culfrer_en_dvd.iso
drwx------ 1 craig craig          0 2008-11-19 20:36 Albums
-rwxrwxrwx 1 craig craig        160 2008-12-14 16:11 AUTOEXEC.BAT
drwx------ 1 craig craig          0 2009-11-10 18:57 $AVG
drwx------ 1 craig craig       4096 2009-06-01 00:33 Boot
-rwxrwxrwx 1 craig craig        210 2008-12-18 20:24 Boot.BAK
-rwxrwxrwx 1 craig craig        381 2010-02-28 22:20 boot.ini
-rwxrwxrwx 1 craig craig     383200 2009-04-21 23:28 bootmgr
-rwxrwxrwx 1 craig craig       8192 2009-06-01 00:33 BOOTSECT.BAK
-rwxrwxrwx 1 craig craig          0 2010-02-28 22:02 CONFIG.SYS
-rwxrwxrwx 1 craig craig        212 2009-01-06 15:21 DCMRip.log
drwx------ 1 craig craig       4096 2008-12-18 16:09 Documents and Settings
drwx------ 1 craig craig      20480 2010-03-03 22:57 Downloads
drwx------ 1 craig craig       4096 2008-12-24 14:04 FlashLIB
-rwxrwxrwx 1 craig craig          0 2008-07-17 19:28 IO.SYS
-rwxrwxrwx 1 craig craig        696 2009-03-12 19:56 log_fs.log
drwx------ 1 craig craig          0 2009-12-08 21:58 Movie Converts
-rwxrwxrwx 1 craig craig          0 2008-07-17 19:28 MSDOS.SYS
drwx------ 1 craig craig       4096 2009-03-26 19:27 Music Playlist

My desktop has 60GB  and cad.desktop thats it

---

### Post by flippo on 2010-03-06
So everything works like you want?

---

### Post by toyoracer on 2010-03-06
Yes that seems to have worked. Thank you.

Any thoughts on my partitions, sizes, and types

---

### Post by flippo on 2010-03-06
It looks good, although you should notice that your /dev/sdb3 isn't being used as your home partition currently, everything is being stored on /dev/sdb1.  We can fix it now if you would like, or if your happy with how its working you can leave it at no harm (other than a linux install of reduced size and some unused harddrive space).

If you decide to leave it please mark the thread as solved.

---

### Post by toyoracer on 2010-03-06
If you have the time I will be here.

---

### Post by flippo on 2010-03-06
Sure, we just need to do some similar magic with your fstab and some file backups.

The difficult part of this is you will have to login as root for a part so your not messing with files your using.  To do this properly you will have to get rid of your GUI side and do some work without one, but I'll give you all the terminal commands you need.

To start we want to mount the directory you want to use as your home directory and copy your current one to it:
```
sudo mkdir /media/tmp
sudo mount /dev/sdb3 /media/tmp
sudo chown craig:craig /media/tmp
sudo cp -a /home/* /media/tmp/
```

The cp command may take a while (you have to copy everything over to the new drive...).  

Now, your new drive has all your home partition stuff on it! Next we need to set it to be your home partition.  First lets tell our computer how to mount it:
```
sudo su
cp /etc/fstab /etc/fstab_tmp
echo "/dev/sdb3 /home ext4 users,defaults 0 0" >> /etc/fstab_tmp
exit
```

Your fstab now knows how to mount your home directory, but we need to make sure its clear so you can get ahold of it.  Heres the tricky part:

First log out of gnome: System -> Log out
NOTE: this is the point of no return! You cannot log in once you pass this point until you are done.
Second push ctrl+alt+f1 to drop to tty1
now login as root: enter your username as root and then your password
```
mkdir /homebup
mv /home/* /homebup/
mv /etc/fstab_tmp /etc/fstab
shutdown -r now
```

If all went well your computer will now restart, then you will reboot using your home partition.  Please keep me updated as to how things go especially if anything odd happens before the part where you hit ctrl+alt+f1

Once you restart if you login and everything seems fine let me know. We'll run some checks to make sure all is well, do some cleanup, then life will be good.

You should also be warned, if things go wrong we will have to recover your system, or it may become unusable.  But all of your files are backed up, not deleted, so we should be able to deal with that without too much trouble.

---

### Post by toyoracer on 2010-03-06
craig@craig-desktop:~$ sudo mkdir /media/tmp
[sudo] password for craig: 
craig@craig-desktop:~$ sudo mount /dev/sdb3 media/tmp
mount: mount point media/tmp does not exist
craig@craig-desktop:~$ sudo chown craig:craig /media/tmp
craig@craig-desktop:~$

---

### Post by flippo on 2010-03-06
Please make sure you copy the commands EXACTLY as they are typed, you can do some real damage if you typo the wrong command, especially if you are logged in as root or if the command starts with sudo.

the command should be:
```
sudo mount /dev/sdb3 /media/tmp
```

---

### Post by patchwork on 2010-03-06
I believe he needs to sudo mkdir /media/tmp

---

### Post by flippo on 2010-03-06
He already did a mkdir, he missed the first / in /media/tmp on the mount

---

### Post by mjitkop on 2010-03-06
Is it because of Wine that you have to do all this? My Windows partition is listed in "Places" under "Computer" as "20 GB Filesystem". When I click on it, it appears on my Ubuntu desktop. :confused:

---

### Post by toyoracer on 2010-03-06
craig@craig-desktop:~$ sudo mkdir /media/tmp
mkdir: cannot create directory `/media/tmp': File exists
craig@craig-desktop:~$ sudo mount /dev/sdb3 /media/tmp
craig@craig-desktop:~$ sudo chown craig:craig /media/tmp
craig@craig-desktop:~$ cp -a /home/* /media/tmp/
craig@craig-desktop:~$ sudo su
root@craig-desktop:/home/craig# cp /etc/fstab /etc/fstab_tmp
root@craig-desktop:/home/craig# echo "/dev/sdb3 /home ext4 users,defaults 0 0" >> /etc/fstab_tmp
root@craig-desktop:/home/craig# exit
exit
craig@craig-desktop:~$

---

### Post by flippo on 2010-03-06
All right, all looks good up until this point.  Go ahead and proceed, but remember you shouldn't log back in (except as root) until your computer has restarted after typing the other commands.

---

### Post by toyoracer on 2010-03-06
I'am back

---

### Post by flippo on 2010-03-07
all right, what does ```
df -h
``` give you?

---

### Post by toyoracer on 2010-03-07
craig@craig-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              37G   14G   21G  41% /
udev                  502M  272K  502M   1% /dev
none                  502M  1.3M  501M   1% /dev/shm
none                  502M  192K  502M   1% /var/run
none                  502M     0  502M   0% /var/lock
none                  502M     0  502M   0% /lib/init/rw
/dev/sda1              56G   47G  9.2G  84% /media/WindowsXP
/dev/sdb3              78G   12G   63G  16% /home
craig@craig-desktop:~$

---

### Post by flippo on 2010-03-07
Looking good, ```
ls -l /home
ls -l /home/craig
```

---

### Post by toyoracer on 2010-03-07
craig@craig-desktop:~$ ls -l /home
total 24
drwxr-xr-x 37 craig craig  4096 2010-03-06 21:58 craig
drwxr-xr-x  2 craig craig  4096 2010-03-06 08:03 Draw
drwx------  2 root  root  16384 2010-03-04 19:47 lost+found
craig@craig-desktop:~$ ls -l /home/craig
total 36
drwxr-xr-x  2 craig craig 4096 2010-03-06 20:23 Desktop
drwxr-xr-x 17 craig craig 4096 2010-03-06 13:14 Documents
drwxr-xr-x  2 craig craig 4096 2010-03-06 09:15 Downloads
-rw-r--r--  1 craig craig  167 2010-03-04 18:35 examples.desktop
drwxr-xr-x  3 craig craig 4096 2010-03-04 18:51 Music
drwxr-xr-x 13 craig craig 4096 2010-03-04 18:53 Pictures
drwxr-xr-x  2 craig craig 4096 2010-03-04 19:03 Public
-rw-r--r--  1 craig craig    0 2010-03-04 18:38 sun through clouds,june,2008.jpg
drwxr-xr-x  2 craig craig 4096 2010-03-04 19:03 Templates
drwxr-xr-x  2 craig craig 4096 2010-03-04 19:03 Videos
craig@craig-desktop:~$

---

### Post by flippo on 2010-03-07
Okay, Everything looks great.

You now have a great deal of backed up redundant data on your computer.  There are two copies of your home drive (we kept your home drive in tact in case things went wrong).  I wouldn't delete it just yet.  Run your system for a few weeks to make sure you don't encounter any big issues.  If nothing pops up type this into a terminal:```
sudo rm -rf /homebup
```

NOTE:
be ABSOLUTELY SURE you don't typo the sudo rm command, you can destroy your entire installation beyond repair if you do it wrong!

Please mark this thread as solved now, unless there are any other problems you would like to address :)

---

### Post by toyoracer on 2010-03-07
Thank you very much. I have a lot to learn, so it is nice to have a good start. How do I mark it solved?

---

### Post by flippo on 2010-03-07
Good question, I've never done it.  I know there is a thread specifically devoted to marking threads as solved, you may search for that.

I think its in one of the drop down menus with User CP and those things...

---

### Post by patchwork on 2010-03-07
Click on thread tools, and select Mark Thread Solved

---

