---
title: "Imgburn No Devices Detected"
date: 2011-04-23
forum: General Help
---

### Post by Kyzyks9001 on 2011-04-23
I have installed Imgburn and it wont detect my cd drive, I configured wine and everything and no matter what I can't get it to recognise my driver, what am I to do?

---

### Post by Quackers on 2011-04-23
Can I ask what it is you want to do with it?

---

### Post by gandaran on 2011-04-23
> **Kyzyks9001 said:**
> I have installed Imgburn and it wont detect my cd drive, I configured wine and everything and no matter what I can't get it to recognise my driver, what am I to do?
programs installed in wine don't work with the hardware, the wine C drive is a virtual file system.
why do you want to use imgburn when there are native linux apps for burning disks?

---

### Post by Kyzyks9001 on 2011-04-23
> **gandaran said:**
> programs installed in wine don't work with the hardware, the wine C drive is a virtual file system.
why do you want to use imgburn when there are native linux apps for burning disks?

Well what are some of these said programs?

---

### Post by augustuen on 2011-04-23
I use Brasero on my laptop, I think it's good.

---

### Post by Quackers on 2011-04-23
Brasero or you can install k3b, which seems to be more successful for me.

---

### Post by gandaran on 2011-04-23
> **Kyzyks9001 said:**
> Well what are some of these said programs?
brasero is already installed and is the default gnome tool for disk burnning, if you don't like brasero try installing gnomebaker.
then there is k3b which is a KDE based app but can work in gnome desktop environment too.

---

### Post by embeddeddeveloper on 2011-04-24
None of those programs work as well as imgburn unfortunately.

Imgburn has a few ways to detect the cd drive but it is really based on the wine configuration and which 'drive' is mapped to the cdrom device.

I have the same problem in 10.10 on my laptop so I am also searching for a solution. 

IMHO Brasero blows chunks and has created more coasters for me than I know what to do with. k3b is ok but is way less advanced as Imgburn.

 :popcorn:

---

### Post by embeddeddeveloper on 2011-04-25
Ok I just got it to work.

I downloaded the latest Imgburn 
[http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)

Then from a console I listed the dvd drive:

```

clee@clee-laptop:~$ ll /dev |grep dvd
lrwxrwxrwx   1 root root           3 2011-04-24 23:30 dvd -> sr0
lrwxrwxrwx   1 root root           3 2011-04-24 23:30 dvdrw -> sr0
drwxr-xr-x   2 root root          60 2011-04-24 19:29 pktcdvd/
clee@clee-laptop:~$ 

```


Then in the wine configuration in the "Drives" tab I set the drive to point to /dev/sr0 and clicked the advanced button to select "CD-ROM" for the drive type.

Then in Imgburn go to tools and select the "Device" tab. There are selections for how you want to interact with the drive, so select "ASPI"

That's all it took for me, I hope it works for you. Good Luck!

---

### Post by frank604 on 2011-04-25
Easiest way without touching winecfg is to start imgburn.  Go to Tool-> Settings -> I/O -> Change interface to ASPI.  Click done, restart imgburn if needed. 

Your log should look like this:
I 20:10:26 ImgBurn Version 2.5.5.0 started!
I 20:10:26 Microsoft Windows NT Workstation 4.0 (4.0, Build 1381 : Service Pack 6a)
I 20:10:26 Total Physical Memory: 3,992,516 KB  -  Available: 2,879,684 KB
I 20:10:26 Initialising SPTI...
I 20:10:26 Searching for SCSI / ATAPI devices...
W 20:10:26 No devices detected!
W 20:10:44 I/O Interface has been changed!
I 20:10:44 Shutting down SPTI...
I 20:10:44 Initialising ASPI...
I 20:10:44 Searching for SCSI / ATAPI devices...
I 20:10:48 -> Drive 1 - Info: ATAPI DVD A  DH16AASH SA15
I 20:10:48 Found 1 DVD±RW/RAM!

:D Enjoy

EDIT:  Also run it as win nt 4.0 (I picked up these tips from the interwebs but don't have links to the original posts, special thanks to whoever wrote it though.  It saved my life with imgburn, the greatest burning software out there!)

---

### Post by d3v1150m471c on 2011-04-25
it's a royal pain and the solution is not so simple
```

winecfg # crack this open

```

go to the drives tab and add the following new drives
/media
/media/cdrom1
/media/cdrom2

for each of those drives make them set as CD-ROM and not autodetected with the advanced options.
You may also need to set wine to run as windows nt4.0 or nt3.5. Do that and it'll probably work.

---

### Post by tomski on 2011-10-17
to expand on what others have said it may well be prudent to actually create a wine prefix for this. Reason for this is that i (& maybe others) have multiple games & apps installed & those which require anything different from the default wine setup i use a prefix so it will not affect other app's stability

here is what i did for Imgburn & dvd decrypter:

1) make the prefix directory
$ mkdir /home/<username>/.local/share/wineprefixes/dvd

2) make the wine prefix itself:
$ env WINEPREFIX="/home/<username>/.local/share/wineprefixes/dvd" wineboot -u

3) set the version to windows NT3.5 & add the dvd drive
$ env WINEPREFIX="/home/<username>/.local/share/wineprefixes/dvd" winecfg
  A) in the gui goto applications tab & change version to NT 3.5
  B) in the gui click on Drives Tab & add the dvd drive as per d3v1150m471c instruction in post above this :)

4) install ImgBurn (repeat for dvd decrypter &/or daemon tools)
$ env WINEPREFIX="/home/<username>/.local/share/wineprefixes/dvd" wine /path/to/setup/installer/exe/or/msi

now you should be able to run these without affecting other app's in wine also use the basis of this to create prefixes (bottles) of wine for each app that needs specific setting in wine to run, this can also help with some copy protection solution which look for a harddisk volume name for the c drive.

One more point worthy of mentioning is that if you have winetricks installed you should be able to now use that to select this prefix & adjust settings further :)

---

### Post by khalnayak123 on 2012-03-11
I have found others facing the same, if you want then you can try the solution that has been mentioned [here ]("http://www.futurehardware.com/pc-softwares-applications/843.htm")and see if it is helping.

---

### Post by frank604 on 2012-03-11
> **tomski said:**
> to expand on what others have said it may well be prudent to actually create a wine prefix for this. Reason for this is that i (& maybe others) have multiple games & apps installed & those which require anything different from the default wine setup i use a prefix so it will not affect other app's stability

here is what i did for Imgburn & dvd decrypter:

1) make the prefix directory
$ mkdir /home/<username>/.local/share/wineprefixes/dvd

2) make the wine prefix itself:
$ env WINEPREFIX="/home/<username>/.local/share/wineprefixes/dvd" wineboot -u

3) set the version to windows NT3.5 & add the dvd drive
$ env WINEPREFIX="/home/<username>/.local/share/wineprefixes/dvd" winecfg
  A) in the gui goto applications tab & change version to NT 3.5
  B) in the gui click on Drives Tab & add the dvd drive as per d3v1150m471c instruction in post above this :)

4) install ImgBurn (repeat for dvd decrypter &/or daemon tools)
$ env WINEPREFIX="/home/<username>/.local/share/wineprefixes/dvd" wine /path/to/setup/installer/exe/or/msi

now you should be able to run these without affecting other app's in wine also use the basis of this to create prefixes (bottles) of wine for each app that needs specific setting in wine to run, this can also help with some copy protection solution which look for a harddisk volume name for the c drive.

One more point worthy of mentioning is that if you have winetricks installed you should be able to now use that to select this prefix & adjust settings further :)

An alternative method would be to use PlayOnLinux.  It is a wine bottle management.  You can also use different versions of wine between applications.  

But what I want to ask is, has anyone tried the solution I posted awhile back?  It was pretty painless and just a few clicks.  I'm wondering if it resolved others' issues as well.

---

