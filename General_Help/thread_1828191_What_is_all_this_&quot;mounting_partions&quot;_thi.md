---
title: "What is all this &quot;mounting partions&quot; thing ?  Can't I just access them directly ?"
date: 2011-08-18
forum: General Help
---

### Post by TheLibyanPirate on 2011-08-18
Hi Everyone

First I'd like to say that I'm very happy for becoming an Ubuntu user and a new member of your great and helpful forums. I started using Ubuntu only two days ago after many months of thinking about the challenges I'm going to face in this magnificent , yet mysterious and a bit complicated ( at least to me ) , operation system.

I don't like dual-booting . I always like focusing on one OS so I removed Windows 7 completely and installed Ubuntu 11.04 on an EXT4 partition and kept my other two data storage NTFS partitions . I already started to get familiar with the new OS but I still need more time to adapt it.

Now to my question , I was surprised to the new concept of mounting Partitions ( I used to think that only ISO files are mounted , that's in Windows of course ) . At first I thought this only happens because my partitions are in NTFS file system , but even when I formatted them to EXT4 I still have to mount partitions each time I turn on my computer. So , please explain to me **, what is this "mounting " process  ? and why should partitions should mounted ?**

Thank you very much for your patience and help
Regards
Muhammad Najem

PS : Please use as simple "Ubuntu" words as possible , as I'm still afraid of seeing lots of terminal codes and Ubuntu programming commands. Nevertheless , [COLOR=Red]I'm an advanced Windows user.
[/COLOR]

---

### Post by CaptainMark on 2011-08-18
basically when a drive is plugged in it cant be accessed directly, mounting a drive means to designate a place for that drive in your filesystem, then you use that place to access the data on the drive, 

so,
just like in windows our files are arranged into a tree type structure where the root of the tree is 'my computer' then you have the trunk and main branches, these would be the drives so 'C:' or 'D:' then the branches of the tree of are the folders on your drives.

in linux the root of the tree is actually called 'root' (written as / ) the next part of the linux tree doesnt have to be your external hdd's but will be your main hdd, the mounting process means you can place your external hdd's anywhere on this tree structure. 

so your external hdd (which contains all of your music say) can be mounted at ```
/home/mark/Music
```meaning your external drive can be seamlessly blended into your music folder and programs can access it as if the music were on your pc's main hdd, 
sorry if the analagy seems patronising but to understand mounting you need to understand the linux file tree system, it can be very confusing for previous windows users, if it seems that odd that one drive is placed inside another on the filetree my best advice would be to just accept this with a pinch of salt for now and in a month it will seem all to easy to understand if not quite so easy to explain to others :P

you can completely customise where and how to mount all of your drives except your main drive which is always just 'root' /

this process does happen in windows but is just automated and you cant control it, give it time and youll definitely prefer our way

ps.  
when i refer to drives i dont just mean hdd's or even just cd drives but can refer to partitions as well, a very popular configration in linux for power users is to have your main partition containing the computers system files and a seperate partition for your personal files which mounts at /home 
1, if you need to reinstall an operating system you dont need to wipe your personal files they can remain where they are even though you completely redo the rest of the filesystem
2, this setup is considered safer against file tree corruption, if an hdd fecks up by doing too many writes and rewrites to your system files your personal data is safely on another partition

here is a snap of my partition setup as an example

---

### Post by TheLibyanPirate on 2011-08-18
I really hope that you're patient person because I still need further explanation :(

You talked about external HDD and that confused me. I don't have an external HDD. I only have a 160GB main HDD devided into 50GB for Root ( FileSystem Partition) , 50GB for my personal files ( My Stuff Partition ) , and 60GB for extra files ( Extra Partition ).

I have no problem accessing Root ( FilesSystem Partion ) but I can't access the other 2 partitons unless I mount them first , why ? 

My second question , I can't seem to be able to make/move/copy files to neither of my 2 other partitions because I don't have permissions , Can you help me with that ?

Thank you very much , Mark . :)
Waiting for your answers ....

---

### Post by akand074 on 2011-08-18
In Windows it would automatically mount it when you plug something in, and when you click "safely remove drive" it will unmount it. Partitions already on your hard drive in Windows mount when you boot. In Ubuntu, that's not the case. Basically, when you boot into Ubuntu, only the drives flagged to mount (on a normal install just /, but people who have a separate home parition /home mounts as well etc). All other drives remain unmounted. 

The benefit of this is 
1) doesn't slow down boot time mounting drives you aren't necessarily going to be using, especially when one is your Windows OS partition. 
2) it's safer, because if somehow managed to run a bad command or do something that destroyed your entire Ubuntu partition, all your other drives are not accessible, and thus are not affected. There was once a command moving around these forums that people used unknowingly that deleted permanently all the files in "/". All mounted drives go to "/media" so they would be deleted as well.

In your case, the only partitions you have are data partitions, so you can actually just set them to mount automatically on boot if you'd like. Take a quick google search on how to do that I haven't actually done it in a long time I can't remember how.

For your second question. Go to /media where all your partitions are being mounted and right click the folders and press properties and change the permissions as you like.

---

### Post by pjd99 on 2011-08-18
If you want write access to the drives you mount manually, you'll need to specify the correct options when mounting.

Do you want these partitions mounted on startup? If so, you'll need to get a little down and dirty with the terminal and post the output of a few commands and create new entries in fstab.

Can you give the output of the following three commands:
```

cat /etc/fstab
sudo fdisk -l
ls -la /dev/disk/by-uuid/

```

---

### Post by TheLibyanPirate on 2011-08-18
Thank you very much [akand074]("http://ubuntuforums.org/member.php?u=840786") and [jd99]("http://ubuntuforums.org/member.php?u=1322931") .I really appreciate it.

After knowing the benefits of not mounting partitions automatically especially that I'm still new user and I might make a mistake like deleting the root or something. I decided to mount the partitions I need whenever I need them . After all , it doesn't take much to mount / unmount partition 

> 
For your second question. Go to /media where all your partitions are  being mounted and right click the folders and press properties and  change the permissions as you like.

I followed your steps but when I get to permissions tab it says that the owner is the root and that I'm not the owner so I can't change permissions . Could you please explain this to me ?

------------

> If you want write access to the drives you mount manually, you'll need to specify the correct options when mounting.

How ? I only right-click on a partition and click "Mount" . I don't use the terminal . Where do I find the options ?

> 
Do you want these partitions mounted on startup? If so, you'll need to  get a little down and dirty with the terminal and post the output of a  few commands and create new entries in fstab.

Can you give the output of the following three commands: 

I ran each command separately and these are result of each : 

```

muhanajem@BlackPearl:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda2       none            swap    sw              0       0
```

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x755046db

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4499    36131840   83  Linux
/dev/sda2            4499        5094     4784128   82  Linux swap / Solaris
/dev/sda3            5094       12276    57687040   83  Linux
/dev/sda4           12276       19458    57686016   83  Linux


```


```

total 0
drwxr-xr-x 2 root root 120 2011-08-19 03:17 .
drwxr-xr-x 6 root root 120 2011-08-19 03:17 ..
lrwxrwxrwx 1 root root  10 2011-08-19 03:18 01377a8f-880e-4052-9b92-03217babe45e -> ../../sda4
lrwxrwxrwx 1 root root  10 2011-08-19 03:18 6a369c22-3ef1-481a-8cc8-d5fc5cb2b211 -> ../../sda2
lrwxrwxrwx 1 root root  10 2011-08-19 03:18 6abc8d42-fba6-40da-b66b-7b093fc50111 -> ../../sda3
lrwxrwxrwx 1 root root  10 2011-08-19 03:18 af26696d-5b37-4d0f-bc51-2fb3da29201f -> ../../sda1

```

Please note that I don't understand most what is in these codes and I really would like to learn . Also please consider explaining some "ubuntu" terms that a new user ( like me ) can't understand. 

Thanks again guys . You're really great.
Regards
Muhammad Najem

---

### Post by TheLibyanPirate on 2011-08-18
Hey guys, I attached two photos below. One displays the partitions and the other displays the permissions tab of one of my data partitions. 

I would be very grateful if you help me gain write access to the partition . Also I would like to understand the meaning of the word "SDA" and the meaning of the different numbers next to them ? for example why there are not in order and they are missing numbers ? 

All thanks and appreciation for those who have helped and those who will help or even try to help . :o

---

### Post by TheLibyanPirate on 2011-08-19
I have found the solution for not being able to make/paste files to my data partitions. It very simple . First mount the partition/partitions and then open the terminal and type :
[FONT=monospace]
[/FONT]**sudo nautilus **
[FONT=monospace]
[/FONT]After that open each partition's properties and from the permissions tab change the owner to your user name ! YES it's a simple as that !

As for my original question about the benefits of mounting partitions it's answered by [akand074]("http://ubuntuforums.org/member.php?u=840786") in reply #4.

Thanks for everyone !

---

### Post by CaptainMark on 2011-08-19
your additional partitions are being mounted read only, this can happen quite a lot with secondary partitions, there is a file /etc/fstab which deals with the automatic mounting of partitons, if your willing to spend a little time googling you could find out the info you need to edit it safely, [try this link for starters]("http://www.tuxfiles.org/linuxhelp/fstab.html") or wait for one of the other guys to help you with it more, ive never had to deal with it so its not come up for me before, a tip for if you ever reinstall in the future, during ubuntu install when it asks about your hard drive setup always click 'something else' your given the chance to use a graphical menu to decide where your partitions mount and it edits fstab for you, easy peasy.

when you use sudo nautilus you are opening a file browser as 'root' (the superuser or admin, not the / directory) which gives you access to any mounted files, but you are better to use ```
gksu nautilus
``` the reasons why are complex but graphical applications that need root permissions should be run with gksu not sudo

---

### Post by TheLibyanPirate on 2011-08-19
> **CaptainMark said:**
> your additional partitions are being mounted read only, this can happen quite a lot with secondary partitions, there is a file /etc/fstab which deals with the automatic mounting of partitons, if your willing to spend a little time googling you could find out the info you need to edit it safely, [try this link for starters]("http://www.tuxfiles.org/linuxhelp/fstab.html") or wait for one of the other guys to help you with it more, ive never had to deal with it so its not come up for me before, a tip for if you ever reinstall in the future, during ubuntu install when it asks about your hard drive setup always click 'something else' your given the chance to use a graphical menu to decide where your partitions mount and it edits fstab for you, easy peasy.

when you use sudo nautilus you are opening a file browser as 'root' (the superuser or admin, not the / directory) which gives you access to any mounted files, but you are better to use ```
gksu nautilus
``` the reasons why are complex but graphical applications that need root permissions should be run with gksu not sudo

Very interesting !. Thank you very much Mark , you've been a great help :D

---

### Post by BHEJU on 2011-08-19
There is a GUI for fstab called PYSDAM. You might want to look into it.

[http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)

Cheers,

---

### Post by oldfred on 2011-08-19
It looks like you converted your NTFS partitions to ext linux format. With NTFS you have to mount it initially with default permissions & ownership as NTFS does not support permissions & ownership which are part of why Linux is more secure than windows. With Linux formats you can control permissions and ownership by file, folder and groups since Linux is a multiuser system by default. You do not need groups and really just need defaults set to your user for your two additional partitions. Best not to do as root. Using gksudo nautilus means you are at root and then have given yourself permission to delete or move anything which if you still are not sure what you are doing can damage system.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Above link was this post before:
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

only after you have reviewed above would I follow  BHEJU's suggestion on using pysdm. You can download it directly from synaptic or Ubuntu software center as it is in the repository. Even though it is a gui to simplify the process it is best to understand a bit more about permissions and ownership before just doing it.

But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm](http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm)
Storage Device Manager - Worry-Free Fstab Configuration
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

---

### Post by CaptainMark on 2011-08-20
+1 good advice oldfred

---

