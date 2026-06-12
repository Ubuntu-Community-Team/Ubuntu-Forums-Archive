---
title: "Best way to auto mount?"
date: 2010-10-27
forum: General Help
---

### Post by epos85 on 2010-10-27
Hello
After installing Ubuntu I have some ext4 partitions (500GB and 480GB). These are not mounted at boot. I see that they are mounted on use, ex with Nautilus accessing them. How do I mount these partitions at boot?

I also have some dirs at those disks i want to mountbind to my dirs in ex. /home/myuser/.
How and where do I get that script running at boot, after mounting those partitions?

Some examples would have been nice.
Excuse my English. 
Thanks in advance.

---

### Post by WorMzy on 2010-10-27
Take a look at /etc/fstab and ```
man fstab
```

You can mount file systems and bind specific directories with it. e.g.

```
/dev/sda3 /media/store ext4 defaults,auto 0 2
```

will automatically mount the ext4 partition "sda3" onto /media/store when you boot up. And

```
/media/store/mywork /home/user/Documents/work none bind 0 0
```

will mount --bind the mywork folder on the sda3 partition (assuming it's been mounted) onto user's Documents/work folder.

You can edit fstab with the following command:
```
gksu gedit /etc/fstab
```

Obviously the examples in my post will not work for you as is, you will need to modify them/create your own. One tip I have is to use UUIDs for specifying partitions, rather than the /dev/sd** method I have used above. UUIDs are much more reliable, since /dev nodes may change between boot sessions. To find out UUIDs run
```
sudo blkid -c /dev/null
``` and to use them in fstab write
```
UUID=ABCDEFGH-IJKL-MNOP-QRST-UVWXYZ123456 /media/store ext4 defaults,auto 0 2
```

---

### Post by epos85 on 2010-10-27
Thanks a lot. Been looking for this solution some time :-)

ext4 defaults,auto 0 2

Standard for mounting ext4?

---

### Post by baddnady23 on 2010-10-27
> **epos85 said:**
> Thanks a lot. Been looking for this solution some time :-)

ext4 defaults,auto 0 2

Standard for mounting ext4?

That looks like a pretty typical line for ext4 in fstab if you want it mounted at start up. Just don't forget to put in there which disk you want mounted and  its respective mount point.  For example,

```
[COLOR="Red"]UUID=794c6ff5-df36-462e-a2db-6184f8f50618[/COLOR] [COLOR="Blue"]/home[/COLOR]           ext4    defaults        0       2
```or```
[COLOR="Red"]/dev/sda2[/COLOR] [COLOR="Blue"]/home[/COLOR]           ext4    defaults        0       2
```

Just make sure what is in red and blue is system specific to you.

---

### Post by WorMzy on 2010-10-27
Yes. You don't really need the auto though, that's set by the "defaults" option already. I just added it so you'd see that options are separated by commas rather than whitespace.

---

### Post by baddnady23 on 2010-10-27
The Ubuntu Community Documentation has a great section on fstab options.

[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

---

### Post by epos85 on 2010-10-27
Thanks a lot. Ive used linux for a while, but I made a script insted of using fstab. Didnt know where to start, but that problem is solved now. :-) Much to learn :-)

---

### Post by epos85 on 2010-10-31
I did as in post #2. Rebooting first time, all devices and folders was mounted. After that, only disk were mounted, not folders. Where to look for errors? I don't know what log to check. And i don't know whats happening.

---

### Post by WorMzy on 2010-10-31
Open a terminal and run
```
sudo mount -a
```
And watch for error messages.

If you post your fstab here (in [CODE[COLOR="Black"]][[/COLOR]/CODE] tags), we may be able to spot a problem.

---

### Post by epos85 on 2010-10-31
I get no error messages. None of the folders are binded either. 
```

user@computer:~$ sudo mount -a
[sudo] password for user: 
user@computer:~$ 

```/etc/fstab
```

# 500GB Disk
UUID=uuid1 /media/uuid1     ext4  rw,nosuid,nodev,uhelper=udisks 0 2
# 468GB Disk
UUID=uuid2 /media/uuid2     ext4  rw,nosuid,nodev,uhelper=udisks 0 2
# Mountbinds
/media/uuid1/home/user/Pictures /home/user/Pictures none bind 0 0
/media/uuid1/home/user/Documents /home/user/Documents none bind 0 0
/media/uuid1/home/user/Music /home/user/Music none bind 0 0
/media/uuid1/home/user/Downloads /home/user/Downloads none bind 0 0
/media/uuid1/home/user/Public /home/user/Public none bind 0 0
/media/uuid1/home/user/Video /home/user/Video none bind 0 0
/media/uuid2/home/user/Downloads_2 /home/user/Downloads_2 none bind 0 0
```

---

### Post by WorMzy on 2010-10-31
Okay, what is the output of
```
mount
```
I want to check whether it thinks it's mounted the folders or not.

---

### Post by epos85 on 2010-11-02
Here is something from 'mount'. 

```

/media/uuid1/home/user/Pictures on /home/user/Pictures type none (rw,bind,commit=0)
/media/uuid1/home/user/Documents on /home/user/Documents type none (rw,bind,commit=0)
/media/uuid1/home/user/Music on /home/user/Music type none (rw,bind,commit=0)
/media/uuid1/home/user/Downloads on /home/user/Downloads type none (rw,bind,commit=0)
/media/uuid1/home/user/Public on /home/user/Public type none (rw,bind,commit=0)
/media/uuid1/home/user/Video on /home/user/Video type none (rw,bind,commit=0)
/media/uuid2/home/user/Downloads_2 on /home/user/Downloads_2 type none (rw,bind,commit=0)

```

---

### Post by WorMzy on 2010-11-02
Ah, I think I see what the problem is. uuid1 and uuid2 haven't been mounted because you haven't set the auto option (or the defaults option). So the binds can't bind the directories because they don't exist. You'll need to set the partitions to automount if you want the binds to work too.

---

### Post by epos85 on 2010-11-02
Uhm, i forgot to post disks from 'mount'. Disks are mounted.

---

### Post by epos85 on 2010-11-02
```
UUID1 on /media/uuid1 type ext4 (rw,nosuid,nodev,uhelper=udisks)
UUID1 on /media/uuid2 type ext4 (rw,nosuid,nodev,uhelper=udisks,commit=0)

/media/uuid1/home/user/Pictures on /home/user/Pictures type none (rw,bind,commit=0)
/media/uuid1/home/user/Documents on /home/user/Documents type none (rw,bind,commit=0)
/media/uuid1/home/user/Music on /home/user/Music type none (rw,bind,commit=0)
/media/uuid1/home/user/Downloads on /home/user/Downloads type none (rw,bind,commit=0)
/media/uuid1/home/user/Public on /home/user/Public type none (rw,bind,commit=0)
/media/uuid1/home/user/Video on /home/user/Video type none (rw,bind,commit=0)
/media/uuid2/home/user/Downloads_2 on /home/user/Downloads_2 type none (rw,bind,commit=0)
```PS, what does commit=0 mean?

Some example of how I can do this easier? Maybe different options? Options used are options Ubuntu use when I access disks..

Could it be because /home/ are encrypted?

---

### Post by oldfred on 2010-11-02
I do it a different way, do not know what way is considered 'better'.

I mount the /data partition elsewhere (not /media and not in /home) so it does not have duplicate entries in the left panel of Nautilus.

I then link all the folders into /home.

I am in the process of changing my next install to mount as /data rather than my current /usr/local/fred/data as that would be slightly better, but my example still uses my old version.

sudo mkdir /usr/local/fred
sudo mkdir /usr/local/fred/data

sudo chmod -R 777 /usr/local/fred/data
sudo chown -R fred:fred /usr/local/fred/data

My fstab:
# Entry for /dev/sda7 :
UUID=defec4d7-3e36-4938-b5de-b2016b2dee27  /usr/local/fred/data    ext3         auto,users,rw,relatime               0  2  

Used to do this (after deleting empty folders in /home/fred:
ln -s /usr/local/fred/data/Music
ln -s /usr/local/fred/data/Documents
ln -s /usr/local/fred/data/Pictures
ln -s /usr/local/fred/data/Videos
etc for every folder
But this does it all (must run from home as that is default where link is created to:
for i in `echo /usr/local/fred/data/*`;do ln -s $i; done

---

### Post by epos85 on 2010-11-02
Good solution. I want to have the disks in left panel (not getting any duplicates), and have them automounted at boot. When disks are mounted, folders in /home/user/ should be mounted to folders at the disks. (Cause I really dont want to save things to /home/ partition).

-Edit-

I did as you said, just with some changes. I used:
for i in `echo /usr/local/fred/data/*`;do ln -s $i; done

Thanks :-)

---

