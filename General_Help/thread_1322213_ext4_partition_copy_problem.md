---
title: "ext4 partition copy problem?"
date: 2009-11-10
forum: General Help
---

### Post by Limeni on 2009-11-10
Hi there, 

I just installed ubuntu, i started live cd, then start gparted and created ext4 hda1 for / hda2 for linux-swap, and  ext4 for my documents.

Now the problem is I cant copy my documents from external drive on hda3, it joust dosent show paste option when i right click on it :/

What is this? I dont have permision or something like that? 
I can only thinkg of going back to NTFS but I would like to stay with ex3?
How can i solve this, please be quick :D

---

### Post by Limeni on 2009-11-10
I joust noticed I can copy from external HDD on hda1, but cant on hda3 where my documents should be :/ 

Is it premission problem? How can I solve this? :D

---

### Post by Limeni on 2009-11-10
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826   83  Linux
/dev/sda2            2612        3133     4192965   82  Linux swap / Solaris
/dev/sda3            3134       30401   219030210   83  Linux

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf30dcc6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

```This is how my partitions look like. Now I want to copy my data from external HDD to sda3 and i cant! When i right click and copy and then right click ond sda3 there is paste option but it is grey and I cant click on it.

Now i first formated partitions with ubuntu live cd, and then installed my Ubuntu, but when installing and setting up partitions in installation, i formated sda1 again and set it as root, but didnt touch sda3, so maybe the problem is Ubuntu thinks this is not "home" drive and... I dont know what to think :(

I must go to bed now :( But I would be very happy if someone could give me a solution to this problme and explain me why cant I copy on my own HDD? Is it permission or what?

---

### Post by ranch hand on 2009-11-10
Go to synaptic and install "nautilus-gksu".

When you have that.  Got to your file manager and go to the files you want.  Right click on a file.  Select the option "open as administrator".  You will be asked for your password.

You are now in "god" mode and shold be careful.  On the other hand you should have no trouble copying files.

---

### Post by Limeni on 2009-11-10
Thanks :)

But where did I go wrong? Is there a way I can copy files without a root privilages?

I would like to have a partition with only my data, joust that, and i would like to be able to copy files on it and delete. 

If i when installing Ubuntu created that partition as /home then it would save my user settings there right? Is there a way I can make it /data and then joust copy my files there, I would like to have a clean partition for my data, not the /home becuse Ubuntu writes his stuff there, you know what i want :)

Is there a way to do that?

---

### Post by Limeni on 2009-11-10
Ok I see now, when I mount that partition that should be clean and contain only my documents, it mounts it on /media ... so Ubuntu looks at it like at a removable drive. 

Can i mount it as /data? Did I miss that while installing ubuntu? does /data exist or I read somwhere wrong :D

Sorry for all this posts, but i really want to solve this and understand Ubuntu :D

---

### Post by ranch hand on 2009-11-10
You can have as many partitions as you want and use them as you want.

Your information is a little strange.  What is a Ntfs partition doing on a box that seems to be MS free?  Seems a weird format for a storage partition under Linux.

---

### Post by Limeni on 2009-11-10
sdb1 is my friends external HDD, i dont use it, only for backup.

Is there a /data mount point? like there is /home, /media... but /data would use only for /data files?

---

### Post by jaythespacehound on 2009-11-10
Yes you can.
Make the /data directory (you will have to be root to do that) give it the appropriate permissions, and then edit your /etc/fstab file.

you're looking for a line that probably looks a bit like:
/dev/sdb1 /media/sbd1 ntfs defaults 0 0

try changing it to something like
/dev/sdb1 /data ntfs auto,user,rw 0 0

this will auto mount your external hdd to /data when you connect it.
Jay

---

### Post by Limeni on 2009-11-10
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826   83  Linux
/dev/sda2            2612        3133     4192965   82  Linux swap / Solaris
/dev/sda3            3134       30401   219030210   83  Linux

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf30dcc6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS
```

This is how my partitions look like, I joust want to understand why cant i copy files from sdb1 to sda3? And I can copy from sdb1 to sda1? Why is that?

---

### Post by jaythespacehound on 2009-11-10
Can you post up the results of a 
df -h

This will (hopefully) tell us where everything is mounted.
You can then do an ls -l on that mount point to see if you have permissions issues (which is likely)

---

### Post by ranch hand on 2009-11-10
I thought you were talking about partitions here.  /media is where all file systems show up unless you label them.

If you want it to be something other than the generic "media".  Fire up gparted, unmount the partition, label it Data.  This should take it out of /media.

---

### Post by Limeni on 2009-11-10
> **ranch hand said:**
> I thought you were talking about partitions here.  /media is where all file systems show up unless you label them.

If you want it to be something other than the generic "media".  Fire up gparted, unmount the partition, label it Data.  This should take it out of /media.

I joust did that and its not working :( But thank you veeery much for help!

---

### Post by Limeni on 2009-11-10
> **jaythespacehound said:**
> Can you post up the results of a 
df -h

This will (hopefully) tell us where everything is mounted.
You can then do an ls -l on that mount point to see if you have permissions issues (which is likely)

df -h gives me this: 

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              20G  2.8G   16G  15% /
udev                 1007M  352K 1006M   1% /dev
none                 1007M  1.2M 1006M   1% /dev/shm
none                 1007M  192K 1007M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
/dev/sdb1             233G  188G   45G  81% /media/Transcend
/dev/sda3             206G  188M  195G   1% /media/Data
```

now did you mean to type: ls -l /dev/sda3? That gives me this: 

```
limeni@limeni-laptop:~$ ls -l /dev/sda3
brw-rw---- 1 root disk 8, 3 2009-11-11 03:56 /dev/sda3
```

I dont know is that what you mean by ls -l 

Guys thank you alot, both of you, im a noob right now, its 4am where I live and i cant go to sleep until i sort this out :D

It joust im a windows user, EX windows user and there you would install win on c drive and d drive would be there for documents. I would like to have same thing here. 3 partitions, first for /, secund for swap, and third for data. 

I had 3 partitions like i said, and when installing in part where you partition your HDD, i selected the 20gb partition for / and used ext4, then i used secund partition 4gb big for linux-swap, and i didnt touch third partition, third is ext4 with all space thats left. Did I had to do something with third partition while installing? Thats what i tought while asking about /data, i tought maybe i need to create mounting point on that partition. 

I hope I will sort this out, and I know Im pain in the *** right now, I want something and dont know even how to express my self beacuse I dont understand linux very vell and all the terms, but I hope you will be able to help me...

Thanks again.

---

### Post by Limeni on 2009-11-10
My fstab file looks like this: 

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=363b20c0-7bae-4160-9f6a-762b92b775aa /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=a0a338c7-ffe6-42d1-ba24-fc0bd192c205 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

There is no my third partition, it looks to me (noob) like that. So when I mount my third partition it acts like i inserted some external HDD... i dont know, but i hope you will have enaugh informations to figure this out.

---

### Post by jaythespacehound on 2009-11-10
Sorry, sort of,
Your harddrive /dev/sda3 is mounted on /media/data
do an:
ls -l /media

My guess is that root owns the /media/data directory at the moment which is why you can't write to it. We can figure out moving it (if you want to) once we know what the write problem is.

---

### Post by Limeni on 2009-11-11
Thanks again guys, no need for you to say sorry, you are helping me alot.

ls -l /media gives me this: 
```

lrwxrwxrwx 1 root   root      6 2009-11-11 00:07 cdrom -> cdrom0
drwxr-xr-x 2 root   root   4096 2009-11-11 00:07 cdrom0
drwx------ 1 limeni limeni 4096 2009-11-10 22:01 Transcend
```

So what should I do when fresh installing Ubuntu, first partition is marked for /, secund for swap, and third i left alone, didnt touch third partition, but it was marked somethink like "don not use this partition" maybe while installing ubuntu I should "use" that partition on some way?

The only thing i want is to have one clean partition, where ubuntu wont write user data. Is there a way of doing this while installing, i was thinking to mark that partition while partitioning HDD in installation? 

If I use NTFS partition its all ok, but wit ex4 i cant write on it.

Huh i must go now to collage, then drive g/f on some fking hill near Zagreb to see snow :/ 

But later im here, with a warm coffe and my ubuntu, and you great guys from forum so we will deal this :)

I will clean install ubuntu againg so what would be the best way to partition HDD if i wont to have one clean ext4 partition? first as /, secund as swap, and how should i mount third? You know when installing you can chose mount points? Shoud I use one of them for third partition?

---

### Post by Limeni on 2009-11-11
Huh guys, I still havent find my "Perfect" partitioning scheme for ubuntu. 

When using Windows i had c:/ drive with system and d:/ drive with my data. So i would like the same thing here + swap. So i created 1 20gb partition for /, 1 4gb partition for swap and one 200gb partition /home. On /home i moved all of my stuff, movies, pictures, everything 100gb of files.

I used to move my data from c:/ with windows beacuse of all the bugs and system fails. So if my system gets corrupted I can save my files that are on d:/ drive. So I tried to dome something like that on Ubuntu, but I wasnt thinkig at all :D Ubuntu already seperates / from /home :D

Uh oh... can someone joust tell me where do you keep your pictures, music, movies, pdf books... do you keep it on /home partition, is /home made for that?

---

### Post by ranch hand on 2009-11-11
Yup.  / is for the system.  /home is for you.

---

### Post by Limeni on 2009-11-12
> **ranch hand said:**
> Yup.  / is for the system.  /home is for you.

Thanks man :) The whole this topic is pointless, thanks for patiance. Its joust Im still thinking win way, and trying to protect my files from win failiure but they are seperated from the start :D 

Great :)

---

### Post by Limeni on 2009-11-29
OK I found solution to my problem. The topic was not pointless after all. 

What I wanted is to have hda1 for /, hda2 for linux-swap, and clean hda3, not /home, but CLEAN partition for my Data. 

The problem was when I was installing Ubuntu, I created 3 partitions, hda1 for /, hda2 for linux swap and hda3 for my Data, but when installing i didnt touch hda3, i used hda1 for /, hda2 for linux-swap and I left hda3 alone. 

And when I installed Ubuntu i could mount hda3 partition labeled as Data but couldnt write anything to it. So it was useless right?

This means you dont have Permission to write on your partition and its really simple to deal with this.

Hit ALT + F2 and type gksu nautilus, this will pop your "file manager" the Nautilus but as a root so watch out. Now navigate to File System/media/ and there find your partition, if it has label Data you will se folder named Data, right click on that folder -> Properties -> Permissions and there set yourself as a owner and give yourself folder access as Create and Delete files and thats it.

I couldnt find anywhere guide to do this, all I wanted is clean partition, not /home where user files and preferences are stored, I wanted clean ex4 partition, and this is how you can get it :D And its really simple, no need to type in terminal. And I even think you can after you start nautilus as root, simply right click your partition if its mounted and go to propertis and gave yoursef permissions without going to media where all external hdd are loaded... 

anyway I hope this is helpful :D

---

