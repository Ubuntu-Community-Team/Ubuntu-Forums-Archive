---
title: "Partition Help"
date: 2010-01-11
forum: General Help
---

### Post by whitetimer on 2010-01-11
Hi All

I have just run a fdisk -l and i have this result

>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29271   235119276   83  Linux
/dev/sda2           29272       30401     9076725    5  Extended
/dev/sda5           29272       30401     9076693+  82  Linux swap / Solaris

I have no idea what the /dev/sda2 partition is and i am missing about 20gb on my HDD ... 

Any thoughts ?

Many thanks

Whitetimer

---

### Post by Bucky Ball on 2010-01-11
You have made a primary boot partition, sda1, and an extended partition, sda2, which contains only a swap file, sda5. An extended partition is intended to have logical drives (partitions) inside. You can only have four primary partitions but the number is many more inside an extended partition.

Try System->Administration->Partition Editor for a better look. The 20Gb might show up as free space. Do you do this yourself with manual partitioning or it was auto? What release are you using?

---

### Post by whitetimer on 2010-01-11
> **Bucky Ball said:**
> You have made a primary boot partition, sda1, and an extended partition, sda2, which contains only a swap file, sda5. An extended partition is intended to have logical drives (partitions) inside. You can only have four primary partitions but the number is many more inside an extended partition.

Try System->Administration->Partition Editor for a better look. The 20Gb might show up as free space. Do you do this yourself with manual partitioning or it was auto? What release are you using?

This install was a cli from the alternate cd Ubuntu 9.10 as my main OS and it was automatic partitioning on the whole drive ... The lost 20gb happened at an earlier time when i was trying to install ubuntu normally to try out. 

So the sda2 extended may be left over from then perhaps.  is this something i can delete then.

---

### Post by howefield on 2010-01-11
You probably don't want to delete your swap partition.

As Bucky Ball suggests, open up GParted from the System > Administration menu, you might need to install it if you haven't already or boot up from a live cd which will include it.

Post a screen shot of your disk.

---

### Post by Bucky Ball on 2010-01-11
Open Partition Editor as described in my first post. It should be delete-able.

> You probably don't want to delete your swap partition.

As Bucky Ball suggests, open up GParted from the System > Administration menu, you might need to install it if you haven't already or boot up from a live cd which will include it.

Post a screen shot of your disk.You can stop the swap and that should be fine if you have enough ram but you probably won't need to. You can shrink and extend the partition with the Partition Editor BUT, and this is a big but, if you are going to resize the partition Ubuntu is actually running from you need to do it with the LiveCD or by booting from the Gparted disk. You can download the ISO and make a CD from it here:

[http://sourceforge.net/projects/gparted/files/](http://sourceforge.net/projects/gparted/files/)

... 'Download Now'. Make CD and boot from it. You can also delete partition with it.

Have a look at things in the Partition Editor now and see how it has all panned out and report back before you make a plan. You don't want to kill the extended partition, you want to stretch it into space you make by shrinking sda1 probably.

---

### Post by whitetimer on 2010-01-11
> **Bucky Ball said:**
> Open Partition Editor as described in my first post. It should be delete-able.

You can stop the swap and that should be fine if you have enough ram but you probably won't need to. You can shrink and extend the partition with the Partition Editor BUT, and this is a big but, if you are going to resize the partition Ubuntu is actually running from you need to do it with the LiveCD or by booting from the Gparted disk. You can download the ISO and make a CD from it here:

[http://sourceforge.net/projects/gparted/files/](http://sourceforge.net/projects/gparted/files/)

... 'Download Now'. Make CD and boot from it. You can also delete partition with it.

Have a look at things in the Partition Editor now and see how it has all panned out and report back before you make a plan. You don't want to kill the extended partition, you want to stretch it into space you make by shrinking sda1 probably.

Ok .. i have just tried booting from gparted and it just shows one partition 233gb and nothing else ...

So i really dont know where the missing 20gb has gone to.  The bios is showing the full sized disk, but when i go to clean install anything, it just shows 233GB ...
:(:(:(

---

### Post by whitetimer on 2010-01-11
> **howefield said:**
> You probably don't want to delete your swap partition.

As Bucky Ball suggests, open up GParted from the System > Administration menu, you might need to install it if you haven't already or boot up from a live cd which will include it.

Post a screen shot of your disk.

[IMG]http://i831.photobucket.com/albums/zz232/whitetimer/Screenshot.png[/IMG]

Although i have a 250GB HDD, this only shows 233GB ... I'm really confused ................

---

### Post by Ordes on 2010-01-11
You are not missing anything. Its totaly normal and is because of the definition of a a byte.

The HDD holds 250,000,000,000 bytes, which is 250GB in METRIC. This is the format the hdd companies print on.

Binary (which the PC uses) don't work like that.
A kilobyte is 1024 bytes
A megabyte is 1024 kilobytes which is 1048576 bytes
....

so your HDD real capacity is 232.8GB

a 320gb shows up as roughly 290gb and so on...

in general you always loose around ~7% when converting from metric to binary. 
----
this is not linux specific... same will happen to you on other OSs

---

### Post by whitetimer on 2010-01-11
> **Ordes said:**
> You are not missing anything. Its totaly normal and is because of the definition of a a byte.

The HDD holds 250,000,000,000 bytes, which is 250GB in METRIC. This is the format the hdd companies print on.

Binary (which the PC uses) don't work like that.
A kilobyte is 1024 bytes
A megabyte is 1024 kilobytes which is 1048576 bytes
....

so your HDD real capacity is 232.8GB

a 320gb shows up as roughly 290gb and so on...

in general you always loose around ~7% when converting from metric to binary. 
----
this is not linux specific... same will happen to you on other OSs

Hi .. Ok thats interesting. So how come when i have done clean installs of Windows in the past, when i go to install the HDD reads 250GB, but lately its only showing 233GB whether i install Windows or Linux ( have tried both just to test )

---

### Post by J V on 2010-01-11
On installation or device manager it may say 250 GB, because thats what it officially is, but in actual space its not...

In my disk utility it shows 250GB / 233GB / 250,059,350,016 bytes

---

### Post by Ordes on 2010-01-11
exactly.. on install it can read the full drive in metric.. which will change to binary after the format.... 

thats why when u install u see the 250gb... and after u only have 230 to use...

---

### Post by whitetimer on 2010-01-11
Thats great, thanks for the info ... Learn something new each day and i'm just loving Ubuntu and have kissed Windows goodbye :D

The next thing is to do a manual partition on a custom cli install ...

If i put the /Home on a separate partition, when it comes time to do a clean install again ie. when Lucid is released, how do i keep my old /Home to use in the new install ?

One week into using Linux/Ubuntu and i love it !!!!!!!

---

### Post by akakingess on 2010-01-11
> **whitetimer said:**
> Thats great, thanks for the info ... Learn something new each day and i'm just loving Ubuntu and have kissed Windows goodbye :D

The next thing is to do a manual partition on a custom cli install ...

If i put the /Home on a separate partition, when it comes time to do a clean install again ie. when Lucid is released, how do i keep my old /Home to use in the new install ?

One week into using Linux/Ubuntu and i love it !!!!!!!

The other thing to look at is what you format the partitions as, such as ext2, ext3, or ext4, because in my limited knowledge I have learned that at least ext4 takes about 5 or 10% (can't remember which it is, to use for indexing and such, which is one of the "bonuses" of the ext-style formatting, indexing is supposed to assist in access time I believe, so if you have say a 200GB partition and format it as ext4, you may only have say 190GB or 180GB that is actually usable as the 5 or 10% is used for indexing purposes, I hope someone will correct me if I am mistaken, but that has been my experience using the more "advanced" ext-formatting file systems.

---

### Post by Ordes on 2010-01-11
you dont neet to do a fresh install.. u can also upgrade.. than make a LiveISO using remastersys, (excluding /home) as its probably pretty big... and than use this live ISO to reinstall your ubu with all your current apps and configs.. u could also do this for your current ubu if you want to separate / & /home.. might be even better to do this now.. and your /home will be much smaller than later.. if its just the case of separating "/" and "/home" on two par, than there are also other ways than fresh install... here is for the new installation way: 

using the default iso or remastersysISO wont change the process of installing.. 

1. load up live. create a partition for /home.. and format it to the filesystem u r using...  [for the sys 15gb should be more than enough]

2. mount the created partition and copy your "/home" over....also rename it to "old-home"  

3. go into the installer, when it comes to the partitioner choose manual.. for par1 choose "/" plus format... for par2 choose "/home"  [DO NOT FORMAT PAR2 -  THATS WHY WE FORMATTED IT BEFORE WE COPIED THE FILES OVER]

4. finish install, its probably the best if you use the same username...but not nessecary

5. go into your home, you should have
/home/username
/home/old-home/username
check your paths, depending on how u copied the files they might be different

--> If you usign remastersys, and want to get your previous configs, profiles, etc back than 
6. $ sudo rm -R /home/username   [deleting folder]
   $ sudo mv /home/old-home/username /home/username   [moving old to new]

   check ownerships ls -l  (its a small L)
   they should be username:username
   if not: $ sudo chown -R username:username /home/username

7. log out and back in ....should have your old home and old settings...

--> if you had a complete fresh install, and just need to copy some file folders (no configs, profiles, etc)
6. copy the need folders into your /home/username, when done
   $ sudo rm -R /home/old-home   [deleting old home]

7. done


but perhaps u open a second thread for that.. and check this solved...as its a different topic

---

### Post by Bucky Ball on 2010-01-12
Your concept is fine but there is a much easier way, Ordes. If you do a fresh install and don't reformat the existing /home the new install will use that as /home by default. Just don't format the old partition with the other new partitions you are creating.

White, with the existing setup and the gparted disk you should be able to shrink sda1 which will leave free space, kill the swap partition making more free space then away you go. Make whatever partitions you like.

But yes, reinstalling with /home as a separate partition makes a lot of sense. It also allows you to do what I have described above if you move to a new release without losing your /home partition.

---

### Post by whitetimer on 2010-01-13
> **Bucky Ball said:**
> Your concept is fine but there is a much easier way, Ordes. If you do a fresh install and don't reformat the existing /home the new install will use that as /home by default. Just don't format the old partition with the other new partitions you are creating.

White, with the existing setup and the gparted disk you should be able to shrink sda1 which will leave free space, kill the swap partition making more free space then away you go. Make whatever partitions you like.

But yes, reinstalling with /home as a separate partition makes a lot of sense. It also allows you to do what I have described above if you move to a new release without losing your /home partition.

Hi Bucky Ball

So if thats the case, when i install the next release, i would just format the / and the /swap, is that the case ?

could you elaborate a little more so i can better understand the process for a cli ?

Many thanks

---

### Post by Ordes on 2010-01-13
Nah he is not formatting it...If you format it, /home  is gone. Because your /home right now exists in "/", which is located on sda1.

You basiclly want to create a new partition during installation and assign it as "/home".. Finish install.. Than copy over the files from /sda1/home.. to sdaNEW/home...And than shrink sda1.. 

The beginning process is different. The end process from point 5, where you copy the files is the same...

However if you want to do it, i would do it before your sda1 used space is more than free space. 

If you also want to keep your installed apps. You need to back them up extra. By copying /home, u just save your files, folders and settings.
Apps backup either by
1. Remastersys
2. Aptoncd 
3. Other ways to backup installed apps ( mostly by terminal, lots of tutorials out there)
But if you only have like a few installed apps it might be also more convenient to just reinstall them after the install. Depends on you...

---

### Post by whitetimer on 2010-01-15
> **Ordes said:**
> Nah he is not formatting it...If you format it, /home  is gone. Because your /home right now exists in "/", which is located on sda1.

You basiclly want to create a new partition during installation and assign it as "/home".. Finish install.. Than copy over the files from /sda1/home.. to sdaNEW/home...And than shrink sda1.. 

The beginning process is different. The end process from point 5, where you copy the files is the same...

However if you want to do it, i would do it before your sda1 used space is more than free space. 

If you also want to keep your installed apps. You need to back them up extra. By copying /home, u just save your files, folders and settings.
Apps backup either by
1. Remastersys
2. Aptoncd 
3. Other ways to backup installed apps ( mostly by terminal, lots of tutorials out there)
But if you only have like a few installed apps it might be also more convenient to just reinstall them after the install. Depends on you...

Hi Ordes

Thanks for that.  I created seperate partitions as per suggested, so my /home is now its own space.  So when lucid comes out, i will be clean installing and i am currently trying to put together an installation script for the apps that i use ...

So all is well ... I'M JUST LOVING UBUNTU & LINUX :D

---

### Post by Ordes on 2010-01-15
welcome...  just wondering why u want to keep waiting so hardly for lucid to come out. u know that you can upgrade a running system without the need of a fresh install...

in my case i would make the fresh install now.. as the running system is still young... and not much stuff had been added or modified....

---

### Post by whitetimer on 2010-01-15
> **Ordes said:**
> welcome...  just wondering why u want to keep waiting so hardly for lucid to come out. u know that you can upgrade a running system without the need of a fresh install...

in my case i would make the fresh install now.. as the running system is still young... and not much stuff had been added or modified....

Its just a preference doing a fresh install instead of an upgrade (well hated that in windows anyway), something i have always done, but may try and upgrade when Lucid comes out ... Plus i'm still very much learning about Unix/Linux/Ubuntu, so clean installs are fun :D

But thanks for your help ... Just love the community spirit to !!!!!

---

### Post by Bucky Ball on 2010-01-17
Glad you're loving it and enjoying the learning curve. 

Upgrading to a newer release on a running system can be problematic and can also take ages. Fresh installs are the only way I change over, but that is personal choice. I only use LTS releases anyhow so I don't upgrade very often at all!

That has changed as of about half an hour ago as I have just installed Crunchbang based on 9.04 on an old HP ze4300 someone generously gave me last night and it is rocking the house so far! XP was so clagged they thought there was something wrong with the machine. I wiped xp, installed Crunchbang and good as new! 

I have a new toy. I can diddle around with this one as it does not have to be production machine or stable. Just a tweaky learning thing. Cool!!!

Keep learning and loving it and welcome to the open-source world of Linux distros. ;)

---

### Post by whitetimer on 2010-01-19
I much prefer clean installs, they just make so much more sense, well i think anyway :D

I have another question though.  When doing a clean install, with an already partitioned /home directory, what happens about all the old hidden files in that directory ?

What other debian distros do you recommend ?

Is there a more efficient way to install applications that you use after doing a clean install ?

many thanks :P

---

