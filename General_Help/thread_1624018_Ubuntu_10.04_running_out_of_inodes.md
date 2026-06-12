---
title: "Ubuntu 10.04 running out of inodes"
date: 2010-11-17
forum: General Help
---

### Post by asus701user on 2010-11-17
Several people have said that those of us who are having problems with Ubuntu (10.04) should ask some specific questions. Here is on below which I cannot get an answer to and never happens in Windows. Can any Ubuntu expert answer it for me? Would really restore my faith in Ubuntu (and go onto the other problems I have with it). Many thanks.

--------------------------------
I think I am running out of inodes on my eeepc701. It has happened  before when I was using Xandros but now I am using Ubuntu 10.04.

I get the following output:

```
df -i
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sda1             230144  213725   16419   93% /
none                   61531     765   60766    2% /dev
none                   62587       5   62582    1% /dev/shm
none                   62587      70   62517    1% /var/run
none                   62587       1   62586    1% /var/lock
none                   62587       3   62584    1% /lib/init/rw
/dev/sdb1                  0       0       0    -  /media/ALAN
```

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.5G  3.1G  250M  93% /
none                  241M  292K  241M   1% /dev
none                  245M  164K  245M   1% /dev/shm
none                  245M  528K  244M   1% /var/run
none                  245M     0  245M   0% /var/lock
none                  245M     0  245M   0% /lib/init/rw
/dev/sdb1              30M  279K   30M   1% /media/ALAN[FONT=Verdana]
```

[/FONT][FONT=Verdana]The number of inodes has been going down over several months and I think that 
running Update Manager does not help. There seem to be very many small files 
(like tty to ttyS3) in dev and its subdirectories and all the files seem to have todays date.

When using Xandros the following worked to free up the inodes:
[/FONT]
```
$ su
[enter password at prompt]
# mkdir -pv /mnt/sda2
# mount /dev/sda2 /mnt/sda2
# find /mnt/sda2 -iname '.wh*' -delete
[wait a long-ish while, then check your new IFree count:]
# df -i
[don't forget to clean up:]
# umount /dev/sda2
# exit
```

[FONT=Verdana]Will that work with Ubuntu? And do I use sda1 rather than sda2? 
I don't seem to have an sda2 now (or I can't see it).

Can anyone answer this please?

[/FONT]

---

### Post by CharlesA on 2010-11-17
The only difference is you would need to use sudo for each command instead of using su to switch to root.

You would probably need to run it off a livecd, since sda is your root partition.

---

### Post by asus701user on 2010-11-17
Thanks for that suggestion. I don't have a CD that can be attached. I installed 10.04 from a USB drive. I do have 10.10 on a USB (I am currently reluctant to upgrade to 10.10 because of all the problems). But I will try booting into 10.10 and then I'll see if I can access sda1 - although I guess it won't be called that if I boot from a USB drive. Oh dear.

I;ll give it a go.

---

### Post by CharlesA on 2010-11-17
You can probably just boot off the liveusb then. The thing is that you need sda1 unmounted, so you can mount it and clean it up.

---

### Post by oldfred on 2010-11-17
I do not know about inodes, but your system is also 93% full. Anytime your system gets that full it raises issues. Since you only have 3.5Gb to work with you will have to be agressive on housecleaning and should have lighterweight applications. You can remove openoffice and firefox and use chromium and any of the smaller word processor/spreadsheets.

HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does more?
sudo apt-get dist-upgrade  #updates dependancies

 How To: Disk Full? - Check Your Trash 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

# remove log files if no issues
cd /var/log
sudo rm -f messages.*
sudo rm -v /var/log/*.gz

See grubcleanup for removing old kernels
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

---

### Post by asus701user on 2010-11-18
Thanks for the suggestions. My attempt to clear the inodes didn't work. The find and remove command seemed to work but it was still out of inodes.

Instead I have installed Ubuntu 10.10. Now the space used is  only 74% and inodes use is 58%. 

My problem now is that I can't see/mount my NAS directories. These are sitting on an Iomega drive (running Linux I presume!). But I cannot connect to them rapidly. In 10.04 I used autofs to connect - but it was horrendous trying to get autofs to work. I have the same problem now. I have set up auto.master and a map file auto.nasstorage but it doesn't work. Last time it took me days to sort out and I don't knwo quite what worked. 

Also the user interface in 10.10 is really bad.

---

### Post by asmoore82 on 2010-11-18
I don't understand this "running out of inodes" issue.

Are you getting specific error messages about "out of inodes" as opposed to "out of disk space"?
AFAIK it is impossible to run out of inodes before running out of space.

---

### Post by CharlesA on 2010-11-18
> **asmoore82 said:**
> I don't understand this "running out of inodes" issue.

Are you getting specific error messages about "out of inodes" as opposed to "out of disk space"?
AFAIK it is impossible to run out of inodes before running out of space.
I'm not quite sure about it either.

@OP: You are installing Ubuntu on a 3.5 gig hard drive, wouldn't it be easier to swap it out for a larger one?

EDIT: I don't know if that "hard drive" is an SDcard or a really tiny HDD, since it is an eeePC 701. The only real info I found is that they are super tiny portables with 8GB hard drives.

---

### Post by cbraxton on 2010-11-18
> **asmoore82 said:**
> 
AFAIK it is impossible to run out of inodes before running out of space.

Actually it is quite possible for this to happen, especially if you have a very large number of small files.

The ext2, ext3, and ext4 filesystems are based on traditional Unix filesystems where inodes are allocated statically when the filesystem is created.  Create too few and you can run out before disk space is exhausted, create too many and you waste disk space that could otherwise be used for data. You can optionally set the number of inodes when the filesystem is created but it cannot be changed afterwards, save by deleting and recreating the filesystem.

See the chapter entitled "The File System" in the Unix-Haters Handbook ([http://simson.net/ref/ugh.pdf](http://simson.net/ref/ugh.pdf)) for details. ;-)

---

### Post by asus701user on 2010-11-19
I have got around the problem of lack of space and inodes by installing 10.10 which doesn't use anywhere near the space of 10.04 even though I cleared out a lot of apps from 10.04 - including old kernels. So I think the Ubuntu update process is not very good leaving lots of redundant or empty files. So I have a reasonable amount of space. 

Now I have the same problem I had with 10.04 - it won't see my NAS shares or Windows machine properly. I have installed smbfs and smbclient and autofs but it is hellish trying to configure it. My Windows machine sees the Ubuntu shares immediately (without any configuration on the Windows machine!) and access is really fast. I wish Ubuntu would be as good as W7 in networking. I'll make a new post for that problem.

Many thanks

---

