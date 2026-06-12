---
title: "some small problems ! please read"
date: 2006-05-02
forum: General Help
---

### Post by medya on 2006-05-02
Hey having ubuntu for two weeks, I am enjoying it too much  I just need to sovle some tiny problems to delete my windows XP forever.

1- when I play a music , I can not hear any other sound (like Clock Alarm, or GAIM's Ding or any music...) is there any way to make it like windows ? 
to hear sound from many sources... 

2-
I have installed gxine , but it doenst have an Icon ,
and I have added it to my panel , each time that I boot ubuntu , 
it gives this ugly , Windows Like Error , at Start up :
> Failed to load image gxine-logo.png
Details: Icon not found


3-
when I start ubuntu, it doesnt automaticly  Activate my Eth connection
I have to actiave it in netwrok setting eacht time.

this problem started since this day :
[http://ubuntuforums.org/showthread.php?t=163317](http://ubuntuforums.org/showthread.php?t=163317)

can u just tell me how I can force ubuntu to autoamticly activate my eth connection at start up (like before)


4- I have a TV TUNER , the ubuntu knows it,but I still have problem in watching TV, 
the TV watch programs like TV TIME or ZAPPNIG dont have my country's Frequencies (they have just some famous countries in their list)
and when I tried to do a Search , it never worked ,it seems for some reason the search channels wont work. I need a TV Program that let me Enter tne Frequesies by hand .


5-I have two hard disks one is 4 GB the other is 40 GB .
I have installed ubuntu on the 4 GB had disk and I have 200 MB swap drive.
I am running out of space.
my 40 GB hard disk have two parttions, one is 10GB for windows and the other 30 GB for music , download files and...

or I wish I could move ubuntu from the 4 GB Hadr Disk to the First Partition (10GB)  of the Second Hard Disk (the one that windows is there now) , so I could give my old  4GB hard disk or give it to poor windows. is it possible to do that, without loosing anything on my currect ubuntu ?

or if it is not possible , I am gonna resize the 10 GB Widnows Partition to 5 GIG (by partion magic)
so I will make 5 FREE SPACE on my second hard disk , how I could I give this 5 GIG to ubuntu so it doenst go out of space ?


If I can solve these problems I can kick out windows out of my life ,
recently Windows XP is keeping calling me "dear user you are a dirty theif , shame on you...." I wanna switch to ubuntu forever and stop being called a theif.

---

### Post by jazzmuzik on 2006-05-02
1. Try System, Preferences, Sound

2. Right click on the launcher, select Properties (or Select Custom Icon), search for the icon (browse for it etc)

3. Try System, Administration, Networking

4. Isn't there a setup option to change tv regions/frequencies? Tvtime is a good program, otherwise you could try xawtv.

5. 4 gig is a small space for Ubuntu. I would think 6 gig is minimum. I believe it is possible to create new partitions on another drive, copy files over and respecify the new drives in /etc/fstab. I'm thinking though that since your installation is fairly new and you don't have too much invested in it as this short a time you might be better just reinstalling the OS on the larger drive. You might first save/backup your /home directory and restore it after the new installation is in place.

---

### Post by medya on 2006-05-02
1. > Try System, Preferences, Sound
what then ?
2. Thanks Solved
3. > Try System, Administration, Networking
that where I always go after each ubuntu start up to actiavte my Eh connection, I want ubuntu to do it everytime I start , autoamaticly.


4. is there any way to back up everything on ubuntu (like the installed packages , desktop appeance , codecs...blah blah) and restore it in a new installation ?

---

### Post by jazzmuzik on 2006-05-02
[QUOTE=medya]1. what then ?[/quote]

Check off "Enable sound server" and "Sounds for events". Then test sounds on the "Sound Events" tab. If you can hear sounds it should work. You can double click the little speaker icon on toolbar and adjust volume or unmute if it's muted.

> 3. that where I always go after each ubuntu start up to actiavte my Eh connection, I want ubuntu to do it everytime I start , autoamaticly.

Not sure about this. Some have also expressed this problem. I don't use DHCP and some apparently have problems using it. Is "Enable the connection" checked?

> 4. is there any way to back up everything on ubuntu (like the installed packages , desktop appeance , codecs...blah blah) and restore it in a new installation ?

I don't think I would try this. I would just back up /home and any other items that are important like databases. Then I would reinstall Ubuntu, then reinstall the programs, then reinstall the /home dir backup and anything else backed up (databases, etc.)

To copy everything... I would consider that a very advanced task and I've never tried it. You might be able to use dd to copy current partitions to the new drive. I think it would go like this:

dd if=/dev/hda1 of=/dev/hdb1
dd if=/dev/hda5 of=/dev/hdb5
etc. 

and do that for every mount, assumming hda is your first drive and hdb is your second EMPTY drive. I would NOT do this unless hdb is empty though and you know the consequences of mistyping something. But I believe dd does a bit for bit copy from source to destination. Be careful. I wouldn't attempt it.

---

### Post by medya on 2006-05-02
ok I am convinced that I better reinstall ubuntu , this time I will install ubuntu on my 10 GB partition ,

but I dont know how to do the partiioning section ,
 I have a 40 GB hard disk ,
one is NTFS 10 GB 
the other is 30 GB Fat32

when I setup Ubuntu, how I can tell it to delete NTFs one and replace it with a Linux partition without touching my 30 GB partition .

my 30 GB partition is so so so so so so IMPORTANT !  I will do nothing Risky please give me a very secure way to do my partitioning . thanks.

---

### Post by jazzmuzik on 2006-05-02
10 gig is a good size.

During the install, when you get to the partitioning section, triple and quadruple check that you don't accidently format the wrong drive. So know your partition names, like hda, hdb, sga, etc and which is which. You can use System, Administration, Disks to gather this info, or at the command line: sudo fdisk -l 

At this point you should know beforehand which partition you want to format.

When you locate the 10 gig partition during the partition phase of the installation, I recommed setting up three partitions: root (/), /home and the swap file.

Swap size: I have 512meg of RAM so I set my swap drive to twice that, 1 gig. This rule may not hold up for larger amounts of RAM though.

How big you make your /home partition is up to you. If you need space for ripping a CD, make it at least 800 meg. It's up to you. I specified 3.5 gig on mine.

My root partition with lots of programs installed uses 3.5 gig. So I would set root to 6 or 7 gigs total space. That will give plenty of room to expand.

So, this is just a suggestion:

/ (root) : 7 gig
/home : 2 gig
swap : 1 gig

This might be good too:

/ (root) : 6 gig
/home : 3 gig
swap : 1 gig

It just depends on how much space you need for you home directory.

Adjust as you see fit.

---

### Post by medya on 2006-05-02
my 10 GIGA NTFS Hard drive is hdb1
when I install ubuntu, should I select that and order ot delete it ?

the last time that I installed ubuntu, I think I had to choose between Hard Disks to delete there wasnt a way to tell it delete the hdb1 and not delete hdb5.

my ram is 250 MB , and my currect swap is 200MB , and I dont see much trouble... do you think If I make a 1 GIG swap, my PC would be faster?

---

### Post by medya on 2006-05-02
by the way I think I better re-install ubuntu when I the next ubuntu comes... when the new ubuntu will be released?

---

### Post by jazzmuzik on 2006-05-02
[QUOTE=medya]my 10 GIGA NTFS Hard drive is hdb1
when I install ubuntu, should I select that and order ot delete it ?[/quote]

If hdb1 is the 10 gig partition, that's the one you want linux to reside in. And you will split that 10 gig partition into three other partitions: swap, root and home.

> the last time that I installed ubuntu, I think I had to choose between Hard Disks to delete there wasnt a way to tell it delete the hdb1 and not delete hdb5.

There's an option during installation to manually partition. I can't remember exactly how it is worded, but it allows you to set up your partitions. Just remember to avoid the drive you want to preserve. Mistakes are easy to make.

> my ram is 250 MB , and my currect swap is 200MB , and I dont see much trouble... do you think If I make a 1 GIG swap, my PC would be faster?

In that case I would make a 500 meg swap. Twice your RAM. You would have lots better performance with another RAM bank of 250.

The next Ubuntu release is "Dapper Drake" and is tenatively scheduled for a June release. But it could be pushed back if they still need to work on it.

---

