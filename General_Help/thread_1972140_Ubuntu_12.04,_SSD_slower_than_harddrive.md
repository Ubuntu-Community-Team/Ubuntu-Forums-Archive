---
title: "Ubuntu 12.04, SSD slower than harddrive"
date: 2012-05-03
forum: General Help
---

### Post by Athius on 2012-05-03
Hello everybody, 

With the release of ubuntu 12.04 I have upgraded both my computers from 10.04 to 12.04. My first computer is a desktop, and that upgrade went flawless. I have, however, encountered a strange problem with my second computer: a Asus eee pc 1015PEM netbook. 

I know that netbook is not a powerhouse, but with extra ram (2 gb total) and a 60gb Vertex 2 SSD,  my netbook used to be very fast. 
When I was running 10.04 opening folders (containing 12 sub directories with a total of 1200 pdf files in them) took less than a second. 
With 12.04 installed however, this is no longer the case. Opening that same folder now takes around 5 seconds, and it is not only that folder that is slow: all my folders now take multiple seconds to open. In fact, my desktop with a 7200 rpm harddrive is faster than my SSD. 
And it is not only nautilus that is slower on my netbook: on my desktop opening my dash and searching for programs and files goes very fast (I hit the button and the dash opens) on my netbook there is a multiple second delay. 

Now, I know this does not sound like a severe problem (although the fact that a SSD is preforming slower than a harddrive should raise some eyebrows) but this means that I have to constantly wait for my computer. Using 10.04 with gnome do my netbook was lightning fast and could keep up with me. Opening folders, launching programs and browsing sub directories containing hundreds of files, all was done lighting fast and I didnt have to wait. 
Now however, Iam constantly waiting for my computer to catch up with me. As impressive as 12.04 looks on my netbook (and it really looks good) Iam not getting the same functionality out of it as I did with 10.04. 

I looked at my system monitor, but my cpu is performing normally, so it does not look like 12.04 is causing extra cpu usage. 

Judging by the fact that my desktop with its 7200rpm harddrive is peforming better than my SSD equipped netbook I suspect that the problem lies with the SSD (or the way ubuntu 12.04 controls my SSD)

Does anybody have a idea what the problem could be? And perhaps how to solve it? 




Many thanks in advance

Jasper

---

### Post by dcstar on 2012-05-03
> **Athius said:**
> 
.........
Does anybody have a idea what the problem could be? And perhaps how to solve it? 


Unless you used TRIM supported kernels in 10.04 with the discard option in the fstab file or manually used the wiper.sh command regularly, then chances are your SSD has run out of spare blocks which cripples performance.

[https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing](https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing)
[http://tinyapps.org/docs/wipe_drives_hdparm.html](http://tinyapps.org/docs/wipe_drives_hdparm.html)

---

### Post by oldfred on 2012-05-03
I did not enable discard right away on my SSD, so I ran this and set discard in fstab:

Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)
fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed

---

### Post by makitso on 2012-05-03
Do a sudo fdisk -l and look to see if the SSD uses 4096 byte partitions.  If so, note if you do not have the correct alignment.

---

### Post by Athius on 2012-05-04
Thanks for all your help, 

I followed the advice you all gave me but in the end it did not solve my problems. (Although I managed to trim a huge amount of data from my ssd and I've learned to enable trim)

I've decided to install xubuntu 12.04 on my netbook and its working perfectly so far. (With trim enabled this time) Now I've the advantages of ubuntu's 12.04's newer software center en kernel, while retaining the speed I enjoyed before. 

Thanks again for all your help, although I did not manege to solve my problem with ubuntu 12.04, it helped me setup a SSD friendly install of Xubuntu 12.04 and probably prolong my ssd's life. 

Jasper

---

### Post by techvish81 on 2012-05-04
you could have tried a fresh installation of ubuntu 12.04 rather than upgrade. i've installed it on my hp mini with just 1gb ram and 5400 rpm 160gb hdd. it is not as fast as 10.04 but still manageable and good enough for routine work.

---

### Post by tomtom12 on 2012-05-18
With a fresh install and a new SDD ( with fstab changes), Nautilus is slower than on my HDD before.  Other than that all is much faster.  To me it seems a problem in Nautilus.  Switching off preview & side pane (F9) helps... but on the HDD I did not have to do that.

Strange: even an external HDD connected with USB 2.0 is faster with nautilus !!!!   I think to list this as a[ bug]("https://bugs.launchpad.net/ubuntu/+bug/1001578"), because it is in my opinion...

---

### Post by tomtom12 on 2012-05-28
Seems solved for me :) This is what I did:

1 -  rename   ~/.gnome2 to  .gnome2.bak  
2 -  rename ~/.gconf/apps/nautilus  to nautilus.bak

Restart Nautlius .... fast ! ))

Not sure which one of the renames (actually deletion of of the folder) solved it, but it worked. Maybe, when upgrading from former HDD install we need to delete these? Just and idea...

---

### Post by dcstar on 2012-05-28
> **tomtom12 said:**
> Seems solved for me :) This is what I did:

1 -  rename   ~/.gnome2 to  .gnome2.bak  
2 -  rename ~/.gconf/apps/nautilus  to nautilus.bak

Restart Nautlius .... fast ! ))

Not sure which one of the renames (actually deletion of of the folder) solved it, but it worked. Maybe, when upgrading from former HDD install we need to delete these? Just and idea...

Any "upgrade" is going to have many, many more issues than a fresh install - especially when all the various conversions between the different Gnome environments is taken into account. It is virtually impossible to allow for all the potential changes in configuration files and structures - the job is just so big that it would take years to test before releasing the new version.

Issues like this are why people should get involved in the development phase purely for pre-release testing, the more that do then the better future releases will be. Issues like this also show why it is always a mistake to use a new release until at least a couple of months have passed.

---

