---
title: "move /home from SSD to HDD"
date: 2011-12-28
forum: General Help
---

### Post by toyoracer on 2011-12-28
Good day and Happy Holiday to everyone.

As the title says, I would like to move /home and any thing else not wanted, from the SSD to a new HDD using Ubuntu 11.10.

terminal says can not copy fstab ? Please help.

---

### Post by toyoracer on 2011-12-28
Sorry for not checking the forums first.

---

### Post by oldfred on 2011-12-28
I used this to move my /home. I read all three and did some mismash of them. I do not think they are really different than the link you have, but the devil is in the details and I did not throughly follow all the steps as posted.

# MoveHome.txt
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Others that really are the same with different copy commands:
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
Note: cp without -a means root takes ownership which would be a big issue
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)


But not more than 5 minutes later I realized I did not want a separate /home but just my data in a data partition. My /home still in / (root) is a little over 1GB and most of that is .wine. My hidden settings is about 250MB, but I have also moved some of the hidden folders with data like the Filrefox profiles & Thunderbird profiles, so I can use them in multiple installs.

---

### Post by toyoracer on 2011-12-28
Thank you for the links following the first It says no fstab ?

craig@craig-GA-990FXA-UD5:~$ sudo cp /etc/fstsb /etc/fstab.$(date +%Y-%m-%d)
[sudo] password for craig: 
cp: cannot stat `/etc/fstsb': No such file or directory
craig@craig-GA-990FXA-UD5:~$ 


also how to I get the box around the terminal response?

---

### Post by toyoracer on 2011-12-28
do not know what these errors are ?

craig@craig-GA-990FXA-UD5:~$ sudo cp /etc/fstsb /etc/fstab.$(date +%Y-%m-%d)
[sudo] password for craig: 
cp: cannot stat `/etc/fstsb': No such file or directory
craig@craig-GA-990FXA-UD5:~$ gksu gedit /etc/fstab

(gksu:4498): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:4498): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:4498): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:4498): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


it did open gedit and there is an error there too.


# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=2fcac174-44dd-4297-a616-b494fd6d9dc5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=70b1d739-356a-4aff-a011-ea554f571a54 none            swap    sw              0       0

---

### Post by toyoracer on 2011-12-28
I am following this guide but nothing but problems.


[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by oldfred on 2011-12-28
Typo
> sudo cp /etc/[COLOR=Red]fstsb[/COLOR] /etc/fstab.$(date +%Y-%m-%d)

This works for me which I copied from your post:

gksu gedit /etc/fstab

---

### Post by toyoracer on 2011-12-28
Thanks. this is what I am getting.


craig@craig-GA-990FXA-UD5:~$ sudo cp /etc/fstab.$(date +%Y-%m-%d)
cp: missing destination file operand after `/etc/fstab.2011-12-28'
Try `cp --help' for more information.


craig@craig-GA-990FXA-UD5:~$ gksu gedit /etc/fstab

(gksu:18300): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:18300): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:18300): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:18300): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

---

### Post by ts3 on 2011-12-28
You can safely ignore the Gtk-Warning lines when using gksudo gedit.  It happened to me a few days ago and I researched it but everyone said it was harmless.  Now I think about it it has disappeared all by itself (I used gksudo gedit earlier today with no error warnings).

As to the cp command error I've never used cp so take this with a grain or two of salt but it looks to me that you might be missing a destination.

According e.g. to this [https://help.ubuntu.com/8.04/basic-commands/C/files-directories-commands.html](https://help.ubuntu.com/8.04/basic-commands/C/files-directories-commands.html)

one needs to specify the file to be copied and a place/filename to copy to.

---

### Post by toyoracer on 2011-12-28
Yes I read the help files too. I gave up on moving it. Saved my files and did a re-install with /home/tmp on the HDD. Just finished and everything seems okay.

Thank you for your time. I will mark this solved. ;)

---

### Post by oldfred on 2011-12-28
Your first copy command had it correct except for the typo. You have to have the from /etc/fstab and a to or /etc/fstab.back or the date as you had it.

You have to have all of /home not just /home/tmp? So what is fstab showing as the mounts?

---

### Post by toyoracer on 2011-12-29
Thanks for asking I used GParted GPT to partition and align my 2TB drives and now I see fdisk dosn't  support. 
I will re-install tomorrow

---

### Post by oldfred on 2011-12-29
I prefer gpt as it is the newer better system. But Windows only works with gpt if you have UEFI. Ubuntu/grub works with gpt and either BIOS or UEFI. I have used gpt  and BIOS since 10.04 and it originally has some issue booting the Windows on another MBR drive. but they already had a workaround then.

You can use gdisk in place of fdisk for partitioning. With gpt there is no need for fdisk. Gdisk is in the repositories. The link to rodbooks is the developer of gdisk.

If you do want to convert you can with gdisk. And most software does not correctly remove the backup gpt partition table and then some software sees the backup and gets confused whether it is MBR or gpt.
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)
Multiboot install with gpt & using gdisk
[http://ubuntuforums.org/showthread.php?t=1566090](http://ubuntuforums.org/showthread.php?t=1566090)
Remove old parts of gpt
[http://ubuntuforums.org/showpost.php?p=10022223&postcount=34](http://ubuntuforums.org/showpost.php?p=10022223&postcount=34)

---

### Post by toyoracer on 2011-12-29
Thank you for those links. I have been doing lots of reading this morning and now more. :D

This is what I have - 60GB SSD for OS - Ubuntu11.10 right now.
2TB x 2 Black HDD's for /home and /tmp + what ever else, on say 550GB partition then remaining I would like LVM, I will be trying KVM, file server and basic playing around with Linux. Will have Windows on 1 vm.
2TB x2 Green for a/v files, back-ups etc.


Any comments would be helpful for how to proceed, I am quite new to linux and computers but have the time to play.

---

### Post by oldfred on 2011-12-29
I just created two 30GB / partitions for my new 60GB SSD. Then I can have two different installs and rotate them. I also have an install on every drive with a boot loader on every drive, so something should boot if a drive fails.

Arch recommends gpt unless you are also doing Windows:
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)

Some of the issues are less now, new partition tools work to correct boundaries and only a few setting in fstab are really required for SSD to minimize writes. I only have 4GB of memory so I left everything on the SSD, but link in all data from my rotating drives.

I followed this logic but have Ubuntu everywhere. I do have Knoppix on a CD or USB still, I think as it is small and boots quickly.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by toyoracer on 2011-12-29
I can follow the Arch set-up - [https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives) and make 2 partitions 30GB each for 11.10 and KVM ?

One thing it says, which is confusing /home on SSD  and /boot on HDD ?
# SSD / /home  # HDD /boot /var /media/data (and other extra partitions, etc.)


maybe the other way around. So how do I instal to get it like that?

---

### Post by oldfred on 2011-12-29
You can when installing with manual install put every system partition in different partitions on different drives. I follow the idea that if it is a system file I want it on the SSD including my hidden files & folders in /home. Why have /boot not on SSD, that would slow down booting?

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

---

### Post by toyoracer on 2012-01-09
I am back to continue my learning, We can ignore everything above as I have the /home in separate partition on the SSD. sda3
So next is to understand - bind -. Does this mean when opening my Home folder and select eg:Documents That will take me to that partition sdb5 ?

referring to Morbius1's posts /mnt/data or /mount/data . I thought /mnt was not seen, ?
[http://ubuntuforums.org/showpost.php?p=11545082&postcount=3](http://ubuntuforums.org/showpost.php?p=11545082&postcount=3)

[http://ubuntuforums.org/showpost.php?p=10899012&postcount=41](http://ubuntuforums.org/showpost.php?p=10899012&postcount=41)


If someone could help explain this. I want to see Home folder in the panel open and then open Documents, Photos or Music and be on that partition

---

### Post by oldfred on 2012-01-10
Yes if you mount in /mnt it is not in /home. I use links and they have worked for me. I originally had a few issues with programs not following links but none in the last couple of years. Morbius1 prefers bind (not bindfs now) as it works with some networking where links may not (I do not network).  I have all data in two data partitions, one older NTFS to share with my old XP and the other ext3 (I would do ext4 now). The folders in my data partitions are all the normal Linux folders like Documents, Music etc and some of the hidden folders that have data.

I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Another way to share:
Morbius1 uses bind, now:
[http://ubuntuforums.org/showthread.php?t=1896695](http://ubuntuforums.org/showthread.php?t=1896695)
kansasnoob's sharing and Morbius1 use of bindfs older
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)
Advantages of bind post 16 - Morbius1
[http://ubuntuforums.org/showthread.php?t=1896695](http://ubuntuforums.org/showthread.php?t=1896695)
HowTo: Create shared directory for local users (with bindfs). - sisco311
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472) 
With upstart script 
[http://ubuntuforums.org/showthread.php?t=1771773&page=5](http://ubuntuforums.org/showthread.php?t=1771773&page=5)

---

### Post by toyoracer on 2012-01-11
Well that was alot of reading, thank you. I read most before, now reading again helps build the brain matter. :)

So this is what I have done and then an error

```
craig@craig-GA-990FXA-UD5:~$ sudo mkdir /mnt/data
craig@craig-GA-990FXA-UD5:~$ sudo chown -R craig: /mnt/data
craig@craig-GA-990FXA-UD5:~$ sudo nano /etc/fstab
craig@craig-GA-990FXA-UD5:~$ sudo cp /etc/fstab /etc/fstab.bak
craig@craig-GA-990FXA-UD5:~$ sudo nano /etc/fstab
craig@craig-GA-990FXA-UD5:~$ sudo mkdir /mnt/data/Documents
[sudo] password for craig: 
craig@craig-GA-990FXA-UD5:~$ sudo mkdir /mnt/data/Downloads
craig@craig-GA-990FXA-UD5:~$ sudo --bind /mnt/data/Documents /home/Documents
sudo: invalid option -- '-'
usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-g groupname|#gid] [-p prompt] [-u user name|#uid]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U user name] [-u user
            name|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u user name|#uid]
            [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u user name|#uid]
            file ...
craig@craig-GA-990FXA-UD5:~$ 
  
```

 maybe mount --bind #but it was mounted already ?

maybe /home/Craig/Documents ?

I am lost with what the last invalid option --'-' results mean ?

---

### Post by toyoracer on 2012-01-11
Thinking while I slept, I need permissions on /mnt/data/Documents

chmod 766 /mnt/data/Documents #correct anything else ?

Permission on /mnt/data #okay ?

Then should be able to bind, Documents and Downloads to that partition.

---

### Post by oldfred on 2012-01-11
I did several installs as I also install the next version several times to understand it and do some testing. After typing the same commands several times, I just listed history & copied it into a bash file. I think this works because all the folders under the mount already have my owership & permissions. (Somewhere I think I included a -R.)

```
#!/bin/bash
# linkdata2home.sh
# link data partitions to /home for new install

# make mount points for other partitions
echo $USER
mkdir /mnt/cdrive
#mkdir /mnt/backup

# windows shared NTFS
mkdir /mnt/shared
chown $USER:$USER /mnt/shared
chmod 777 /mnt/shared
mkdir /mnt/data
chown $USER:$USER /mnt/data
chmod 777 /mnt/data
#The big "X" will also not make files executable unless they were executable to begin with.Morbius1
#sudo chmod -R a+rwX /mnt/data

```

I also backup & add entries to fstab and some other setup things for NFS. Overtime I keep adding to my script to automate more & more. I have a second script to install all my apps also.

---

### Post by toyoracer on 2012-01-14
I have no idea why it seems so complicated but I finally understand and have it solved.

Following your post, I have linked to HDD and that is what I needed.

[http://ubuntuforums.org/showpost.php?p=11081384&postcount=4](http://ubuntuforums.org/showpost.php?p=11081384&postcount=4)


Note:- I believe a sticky thread should be made for users with SSD and HDD's for setting up their /home/storage on a second drive. This would ease the frustrations of new users, making for a better overall impression of Ubuntu.
This could show complete set-up of "link" & "bind" solutions as more systems are coming with SSD / HDD configurations.

Thank you very much _oldfred_ for sticking with me until it finally sunk in. :D

---

### Post by oldfred on 2012-01-14
Glad you got it working. :)

First time can be a difficult task. Second is easier, but 4th or 5th, it becomes why am I typing the same commands over & over and you start looking at bash and find out you can just copy history to a bash file and rerun it.

---

### Post by toyoracer on 2012-01-14
Good to know about the bash script.

I have 4 partitions so that would need 4 scripts?

---

### Post by oldfred on 2012-01-14
No, if you go into terminal and type history, what do you get. It should show the last 500 commands you typed.

I just copied the history of what I was doing into a bash file. I had to do a lot editing as I had many errors even having done it several times already. So houseclean bad commands and save to a file. Add a bash header and make executeable. See my example above.

---

