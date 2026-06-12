---
title: "Adjust the 'region setting' in DVD Drive"
date: 2009-11-15
forum: General Help
---

### Post by jono2009 on 2009-11-15
I'm wanting to play rented movies and as far as I can tell from searching my problem here on this forum, I have to adjust the 'region setting' in my DVD Drive, (I've also installed all other necessary items)  

I can use the terminal with copy and paste, can the forum help me please..:D

---

### Post by rukiaEnix on 2009-11-15
What is the problem exactly? -.-

---

### Post by RedSingularity on 2009-11-15
First you need a media player.  I recommend VLC.  

Then you need to install the needed packages.  Do this in terminal. 

```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update
```

Then............

```
sudo apt-get install libdvdcss2
```

After this try playing your dvds.

---

### Post by jono2009 on 2009-11-15
I can't play not rented movies on my note book.:confused:

---

### Post by jono2009 on 2009-11-15
> **RedSingularity said:**
> First you need a media player.  I recommend VLC.  

Then you need to install the needed packages.  Do this in terminal. 

```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update
```

Then............

```
sudo apt-get install libdvdcss2
```

After this try playing your dvds.

I have done these, but to be sure I do again, then I get back with a reply

---

### Post by jono2009 on 2009-11-15
> **RedSingularity said:**
> First you need a media player.  I recommend VLC.  

Then you need to install the needed packages.  Do this in terminal. 

```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update
```

Then............

```
sudo apt-get install libdvdcss2
```

After this try playing your dvds.



Yes completed the above, also VLC installed....

---

### Post by rukiaEnix on 2009-11-15
downlaod the dvd player Ogle it works fine for me:

[http://www.dtek.chalmers.se/groups/dvd/](http://www.dtek.chalmers.se/groups/dvd/)

---

### Post by 23dornot23d on 2009-11-15
[B]Maybe not a good idea ... for me to add the key here ... carry on ....
[/B]

---

### Post by jono2009 on 2009-11-15
> **rukiaEnix said:**
> downlaod the dvd player Ogle it works fine for me:

[http://www.dtek.chalmers.se/groups/dvd/](http://www.dtek.chalmers.se/groups/dvd/)

Thanks I download and give this a try...:popcorn:

---

### Post by jono2009 on 2009-11-15
> **23dornot23d said:**
> [B]Maybe not a good idea ... for me to add the key here ... carry on ....
[/B]


OK I was try this but canceled as well...

---

### Post by jono2009 on 2009-11-15
Can this info help me, anyone...

          :~$ sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: ST9320320AS
       vendor: Seagate
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 0303
       serial: 5SX4BVH5
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=97646c29
  *-cdrom
       description: DVD-RAM writer
       product: CDDVDW TS-L633A
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: AS00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       size: 3830MiB (4016MB)
       capabilities: partitioned partitioned:dos
jono@jono-laptop:~$

---

### Post by Rhubarb on 2009-11-15
I'm not sure I can help you much with playing DVDs, I was going to suggest medibuntu and intsalling libdvdcss2 - but this has already been suggested.

If you've got different region DVDs that you're trying to play, some DVD players need to be forced to play other regions in order to play them (be mindful that you can only change you DVD players firmware (that resides in your DVD drive) 5 times before it gets locked on to the last region that was set.

There's a nice command line utility called regionset that'll let you change this:
```
sudo aptitude install regionset
```

To run it, pop a DVD in the drive that contains the region you wish to change it to, then run regionset:
```
sudo regionset
```
- I'm not sure if you need administrative privileges to run this, but I assume it's needed.

Then just follow the prompts and you're done.

---

### Post by jono2009 on 2009-11-15
> **Rhubarb said:**
> I'm not sure I can help you much with playing DVDs, I was going to suggest medibuntu and intsalling libdvdcss2 - but this has already been suggested.

If you've got different region DVDs that you're trying to play, some DVD players need to be forced to play other regions in order to play them (be mindful that you can only change you DVD players firmware (that resides in your DVD drive) 5 times before it gets locked on to the last region that was set.

There's a nice command line utility called regionset that'll let you change this:
```
sudo aptitude install regionset
```

To run it, pop a DVD in the drive that contains the region you wish to change it to, then run regionset:
```
sudo regionset
```
- I'm not sure if you need administrative privileges to run this, but I assume it's needed.

Then just follow the prompts and you're done.



I'll been able to do this, been able to set my region 4 thanks mate for the help on this.... SOLVED

---

