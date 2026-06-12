---
title: "To run iTune software on Linux"
date: 2009-11-15
forum: General Help
---

### Post by satimis on 2009-11-15
Hi folks,


Recently I purchased an "iPhone 3G S".  I don't have Windows box.  I started googling around for solution to run iTune software on Linux with;

1)
iTunes Linux Project for HOW To's for running iTunes on Linux

and

2)
itune ubuntu

It returned dozens of solution, some of them already out off date.  I'm not very clear which of them shall I follow.  Please shed me some light.

TIA


B.R.
satimis

---

### Post by bbneo on 2009-11-15
I looked into this myself just recently, and from what I could tell, iTunes used to work pretty well in WINE with version 8.0 or such, but when iTunes evolved to 9, the WINE compatibility broke...

The answer... will likely be... Android and Google OS...  Then Apple will really start having to play ball with Linux to stay in the game.

---

### Post by arnab_das on 2009-11-15
you could try banshee. its almost itunes in its functionality and if u want the itunes interface, go for songbird.

---

### Post by satimis on 2009-11-15
> **arnab_das said:**
> you could try banshee. its almost itunes in its functionality and if u want the itunes interface, go for songbird.

Hi arnab_das,

Thanks for your advice.

I suppose you meant following software;

[http://banshee-project.org/](http://banshee-project.org/)
[http://getsongbird.com/](http://getsongbird.com/)

What will be their difference in function?  TIA


B.R.
satimis

---

### Post by arnab_das on 2009-11-15
> **satimis said:**
> Hi arnab_das,

Thanks for your advice.

I suppose you meant following software;

[http://banshee-project.org/](http://banshee-project.org/)
[http://getsongbird.com/](http://getsongbird.com/)

What will be their difference in function?  TIA


B.R.
satimis

yup those are the ones.
banshee has ipod compatibility unlike any other multimedia player on ubuntu. to install it, type "banshee" in the ubuntu software center.
as for songbird, its a mozilla project. not in the ubuntu repos, so you'll have to take the trouble of downloading it and unzipping it. however it only emulates the look of itunes. no ipod compatibility AFAIK.

---

### Post by satimis on 2009-11-15
> **bbneo said:**
> I looked into this myself just recently, and from what I could tell, iTunes used to work pretty well in WINE with version 8.0 or such, but when iTunes evolved to 9, the WINE compatibility broke...

The answer... will likely be... Android and Google OS...  Then Apple will really start having to play ball with Linux to stay in the game.
Hi bbneo,

Thanks for your advice.

Whether you meant follows;

Android (operating system)
[http://en.wikipedia.org/wiki/Android_(operating_system](http://en.wikipedia.org/wiki/Android_(operating_system))


Google Chrome Operating System
[http://googlesystem.blogspot.com/2009/07/google-chrome-operating-system.html](http://googlesystem.blogspot.com/2009/07/google-chrome-operating-system.html)


B.R.
satimis

---

### Post by krendar on 2009-11-15
> **arnab_das said:**
> 
as for songbird, its a mozilla project. not in the ubuntu repos, so you'll have to take the trouble of downloading it and unzipping it. however it only emulates the look of itunes. no ipod compatibility AFAIK.

You can add the getdeb repository however. Then its just "sudo apt-get install songbird":

[http://www.getdeb.net/updates/#how_to_install](http://www.getdeb.net/updates/#how_to_install)

---

### Post by Zorael on 2009-11-15
Those programs are both good media managers in terms of managing your audio selection.

As for syncing iPhones (or iPod Touches), that's really difficult, with no thanks to Apple who purposedly tries to break compatibility with each firmware upgrade.

[The wiki page](https://help.ubuntu.com/community/PortableDevices/iPhone) have all the different available options detailed. The easiest one would be to actually use iTunes in a virtual machine running XP. The difficult one needs you to have a pre-3.0 firmware, jailbreak your phone, install an SSH server into it, and then use the ipod-convenience package to mount the phone over a WLAN and then sync wirelessly. Jailbreaking voids warranty and Apple will hunt you down and eat you, so I'd advise you to try the virtual machine approach.

Really, this is not a flaw in Linux, but rather Apple refusing to hand out information about how to communicate with the device, and then [threatening with legal action](http://www.guardian.co.uk/technology/blog/2008/nov/28/apple-ipod) when people try to figure it out in the spirit of interoperability. Their claim was later withdrawn, but in subsequent updates (3.0) they changed the database type, after which people were back at square one. With no iTunes in Linux, and no Linux alternatives that work, the only alternative is to use iTunes where it does exist; in Windows and on MacOS.

Apple are as evil (or moreso) than Microsoft, but with greater charisma. Genious marketing; people *need* to use their product (iTunes) to use their devices, but it screws over the customers who can't or don't want to.

edit: There seems to be light at the end of the tunnel though, and perhaps sometime in the future it will even be easy. See [this blog post](http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux/) (and [its followup](http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/) for a more concrete guide).

---

### Post by satimis on 2009-11-15
> **Zorael said:**
> Those programs are both good media managers in terms of managing your audio selection.

As for syncing iPhones (or iPod Touches), that's really difficult, with no thanks to Apple who purposedly tries to break compatibility with each firmware upgrade.

[The wiki page](https://help.ubuntu.com/community/PortableDevices/iPhone) have all the different available options detailed. The easiest one would be to actually use iTunes in a virtual machine running XP. The difficult one needs you to have a pre-3.0 firmware, jailbreak your phone, install an SSH server into it, and then use the ipod-convenience package to mount the phone over a WLAN and then sync wirelessly. Jailbreaking voids warranty and Apple will hunt you down and eat you, so I'd advise you to try the virtual machine approach.

Really, this is not a flaw in Linux, but rather Apple refusing to hand out information about how to communicate with the device, and then [threatening with legal action](http://www.guardian.co.uk/technology/blog/2008/nov/28/apple-ipod) when people try to figure it out in the spirit of interoperability. Their claim was later withdrawn, but in subsequent updates (3.0) they changed the database type, after which people were back at square one. With no iTunes in Linux, and no Linux alternatives that work, the only alternative is to use iTunes where it does exist; in Windows and on MacOS.

Apple are as evil (or moreso) than Microsoft, but with greater charisma. Genious marketing; people *need* to use their product (iTunes) to use their devices, but it screws over the customers who can't or don't want to.

edit: There seems to be light at the end of the tunnel though, and perhaps sometime in the future it will even be easy. See [this blog post](http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux/) (and [its followup](http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/) for a more concrete guide).

Hi Zorael,


Lot of thanks for your detail info.  If I understand it correctly, it would be better to forget iTune software turning to their alternatives on Linux.

I read following thread before;
PortableDevicesiPhone
[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

Unless I get a Windows licence.  Otherwise I have to follow all sections on;```

Syncing Music on Firmware Versions 1.x

Syncing iPhones and iPods Touch w/ Firmware 2.x

Syncing via Cable

Copying photos to the iPhone or iPod Touch

Syncing contacts calendar notes

```

There will be tedious work taking lengthy time to complete.  In the circumstances it would be better for me using the compatible software available on Linux and forget iTune software.

If I'm wrong please correct me.

Thanks

B.R.
satimis

---

### Post by satimis on 2009-11-15
> **krendar said:**
> You can add the getdeb repository however. Then its just "sudo apt-get install songbird":

[http://www.getdeb.net/updates/#how_to_install](http://www.getdeb.net/updates/#how_to_install)
Hi krendar,

Thanks for your advice.

satimis

---

### Post by Zorael on 2009-11-16
> **satimis said:**
> Lot of thanks for your detail info.  If I understand it correctly, it would be better to forget iTune software turning to their alternatives on Linux.
The problem is that currently the only way to sync a non-jailbroken iPhone, or to copy music to it in any form, is to do it using iTunes. iTunes doesn't exist for Linux, and it likely never will. The alternatives suggested here (Banshee, Songbird etc) will sync nicely with other iPods (exception being iPod Touch, maybe other newer models), but not with an iPhone. *Unless* yours is jailbroken and you install an SSH server to it. Having done that, you could mount it and sync your music over WLAN. That would void your warranty.

As evident in that blog post linked at the end of my earlier post, it seems real progress is being made to be able to just connect an iPhone with the normal USB cable and then sync with said alternatives (Banshee, Amarok, ...), but it's not quite there yet. I have an iPhone myself and this has sparked my curiosity, but I haven't yet had time to try it out, so I don't know to what extent it works. Perhaps it is still 6 months away from being usable.

I don't know what to recommend you. As it is right now, you need iTunes to sync with a non-jailbroken iPhone, especially a new one like the 3G S which will have the new 3.0 firmware. If you don't have a Windows license to install Windows in a virtual machine, and then install and run iTunes from there, I'm not sure there is an alternative.

---

### Post by satimis on 2009-11-16
> **Zorael said:**
> The problem is that currently the only way to sync a non-jailbroken iPhone, or to copy music to it in any form, is to do it using iTunes. iTunes doesn't exist for Linux, and it likely never will. The alternatives suggested here (Banshee, Songbird etc) will sync nicely with other iPods (exception being iPod Touch, maybe other newer models), but not with an iPhone. *Unless* yours is jailbroken and you install an SSH server to it. Having done that, you could mount it and sync your music over WLAN. That would void your warranty.

As evident in that blog post linked at the end of my earlier post, it seems real progress is being made to be able to just connect an iPhone with the normal USB cable and then sync with said alternatives (Banshee, Amarok, ...), but it's not quite there yet. I have an iPhone myself and this has sparked my curiosity, but I haven't yet had time to try it out, so I don't know to what extent it works. Perhaps it is still 6 months away from being usable.

I don't know what to recommend you. As it is right now, you need iTunes to sync with a non-jailbroken iPhone, especially a new one like the 3G S which will have the new 3.0 firmware. If you don't have a Windows license to install Windows in a virtual machine, and then install and run iTunes from there, I'm not sure there is an alternative.

Hi Zorael,


I suppose you meant following URLs;

iPhone syncing on Linux
[http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux/](http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux/)
Software:-
libusb-1.0
usbmuxd
libiphone
iFuse and gvfs-backend-afc
libgpod 


iPhone syncing on Linux, part 2
[http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/](http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/)


usbmuxd
[http://marcansoft.com/blog/iphonelinux/usbmuxd/](http://marcansoft.com/blog/iphonelinux/usbmuxd/)


Mailing List
Iphone-linux-dev --
[http://lists.mattcolyer.com/listinfo.cgi/iphone-linux-dev-mattcolyer.com](http://lists.mattcolyer.com/listinfo.cgi/iphone-linux-dev-mattcolyer.com)


That will be sufficient for me starting the test here on my IPhone 3G (S).  I'll try finding time to do the test and post the outcome and/or test result here.


Before start I expect clarifying following points.

1)
Do I need install all software;
libusb-1.0
usbmuxd
libiphone
iFuse and gvfs-backend-afc
libgpod
?

2)
I don't have a spare PC for this test.  Can I do it on a VM?

Remark:
I have a PC running KVM on Debian 5.0(host).  I have 5 VMs running Ubuntu 9 as Guest.

I'll perform the test on a VM.  But another thought coming on mind is how can I connect the IPhone to a VM?

Any advice and/or comment?  TIA


B.R.
satimis

---

### Post by timcredible on 2009-11-16
the iphone uses an encrypted connection, you won't get it to work with linux unless you jailbreak it.  if you've had the phone less than 30 days, return it, get something that's not made by a company that wants to lock everything down.  that means no microsoft products and no apple products.  the droid does everything the iphone does plus more - 2 of my friend have droids, they're same as iphones - small linux computers, but they aren't locked down by a money-crazed company.

---

### Post by Sin@Sin-Sacrifice on 2009-11-16
+100000000 for Android. The G1 is great and I hear the MyTouch and others are pretty awesome too.

---

### Post by zaphod777 on 2009-11-17
I love the HTC Magic (MYTOUCH but I live in Japan so it is the Magic). 

It connects to the PC like a usb drive which I use SongBird to sync playlists to it. It works great I love it.

However if I lived in the US I think I would try and pick up the newer droid since it has more memory and bigger screen, exchange support, navi, etc. 

I just love how well goggle integrates everything. On top of that it plays well with linux. 

That and with all of the addons and theam's it is pretty snazy much faster than itunes. 

it even gets all the album art via the web and sends it to my Android phone.

---

### Post by satimis on 2009-11-17
Hi folks,

Following is my new discovery.

Using the USB cable to connect IPhone and PC;

Virtual Box
Host - Debian 5.0
VM - Ubuntu 9.0


Following window popup automaticall on PC
```

Camera Import
A camera has been detected
There are photos on the camera.  Would you like to add these pitures to your album?
[Ignore] [Import Photos]

```

IPhone switched on automatically and off after a while.

Clicking [Import Photos] tab starts following window;

```

Import Photos
Destination [Home   ]
(I can browse here)
[ ] Delete imported images from the camera
[ ] Keep original filenames
[x] Rotate images physically
[Cancel] [Import]

```

Clicking [Import]

Photos download to a directory created automatically with "date" and "time" as its name.  Then following window started

```

gThumb 2.10.8
An image viewer and browser for GNOME.

```


Wonderful all photos on the IPhone are download without additional package installed on the PC.  It solves my problem on downloading photos.  I won't upload photos from PC to IPhone.

---

### Post by satimis on 2009-11-18
Hi Zorael and folks,

It seems to me I can use my new IPhone without much problem.  It is a jailbroken iphone.

Now I can browse Internet and send/receive web mails.  Incoming Yahoo mails can be dropped to IPhone directly.  I can connect YouTube, enjoying movie/ World Map/Weather reports/etc.  I can take photo and movie and can download them to PC.

What other functions do I need?  Music?  Advice would be appreciated.

The said IPhone is a gift from my relative.  He gave me a prepaid voucher for an IPhone.  I can't make other selection.


B.R.
satimis

---

### Post by Cheesemill on 2009-11-19
How do you know that your phone is jailbroken? Did you do it?

If not and it's a new model (firmware v3) then

[SIZE=2]***There is no way to transfer your music onto it!!***[/SIZE]
(unless you run a Windows VM but you say this isn't an option)

All the other features will work (photos etc) because these are simply stored as normal files. However, the music database is encrypted and Apple wont tell anyone how they've done it.

---

### Post by satimis on 2009-11-21
Hi folks,

I found following thread;
How to connect iPhone/iPod Touch (Using USB) in Karmic/Jaunty/Intrepid/Hardy
[http://www.ubuntugeek.com/how-to-connect-iphoneipod-touch-using-usbin-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/how-to-connect-iphoneipod-touch-using-usbin-karmicjauntyintrepidhardy.html)

I'm now testing it.  Unfortunately I don't have a spare PC for this testing.  Therefore I install iFuse on a VM of the Virtual Machine which runs Debian5.0 on host and Ubuntu 9.04 on VM.  The installation is completed, no problem encounted.  However after connection via the USB cord IPhone can be detected by the host.  Photos and Video on the IPhone can be detected and download to the host without problem.  But IPhone can't be detected by the VM.  Neither can I find the mountpoint of the IPhone on the host.  I'm still struggling to sort out this problem.  Where is the mountpoint.  If without result I have to find a spare PC for this test.

Have you got any idea?  TIA

B.R.
satimis

---

### Post by satimis on 2009-11-22
Hi folks,

I install iFuse on an Ubunutu 8.04 desktop according to following articles;

Ubuntu Linux Tutorials,Howtos,Tips & News | Intrepid,Jaunty,Karmic 
[How to connect iPhone/iPod Touch (Using USB) in Karmic/Jaunty/Intrepid/Hardy|Ubuntu Geek](http://www.ubuntugeek.com/how-to-connect-iphoneipod-touch-using-usbin-karmicjauntyintrepidhardy.html)

Plugin the IPhone 3GS via USB cord.

satimis@vz0:~$ sudo usbmuxd
satimis@vz0:~$ sudo ifuse /media/iphone/

Now it mounts the IPhone 3GS.


satimis@vz0:~$ ls /media/iphone/```

com.apple.itdbprep.postprocess.lock  Downloads       Podcasts
com.apple.itunes.lock_sync           iTunes_Control  Purchases
DCIM                                 Photos          Recordings

```

satimis@vz0:~$ ls /media/iphone/DCIM/```

100APPLE
```

satimis@vz0:~$ ls /media/iphone/DCIM/100APPLE/```

IMG_0002.JPG  IMG_0003.JPG  IMG_0005.MOV  IMG_0006.JPG

```

satimis@vz0:~$ ls /media/iphone/Downloads/
No output


satimis@vz0:~$ ls /media/iphone/iTunes_Control/```

iTunes  Music  Ringtones

```

satimis@vz0:~$ ls /media/iphone/iTunes_Control/iTunes/```

IC-Info.sidv         iTunesLock         ShowLicense
iTunesControl        iTunesPrefs        ShowMarketing
iTunes Library.itlp  iTunesPrefs.plist  ShowRegistration
```

satimis@vz0:~$ ls /media/iphone/iTunes_Control/iTunes/iTunes\ Library.itlp/```

DBTemp        Extras.itdb   Locations.itdb
Dynamic.itdb  Library.itdb  Locations.itdb.cbk
satimis@vz0:~$ ls /media/iphone/iTunes_Control/iTunes/iTunes\ Library.itlp/DBTemp/
Backup  ddd.itdbm
```

satimis@vz0:~$ ls /media/iphone/iTunes_Control/iTunes/iTunes\ Library.itlp/DBTemp/Backup/```

iTunes_Control
```

satimis@vz0:~$ ls /media/iphone/iTunes_Control/iTunes/iTunes\ Library.itlp/DBTemp/Backup/iTunes_Control/```

iTunes
```

satimis@vz0:~$ ls /media/iphone/iTunes_Control/iTunes/iTunes\ Library.itlp/DBTemp/Backup/iTunes_Control/iTunes/```

iTunes Library.itlp

```

satimis@vz0:~$ ls /media/iphone/iTunes_Control/Music/```

F00  F04  F08  F12  F16  F20  F24  F28  F32  F36  F40  F44  F48
F01  F05  F09  F13  F17  F21  F25  F29  F33  F37  F41  F45  F49
F02  F06  F10  F14  F18  F22  F26  F30  F34  F38  F42  F46
F03  F07  F11  F15  F19  F23  F27  F31  F35  F39  F43  F47
```
All of them are directories/folders

satimis@vz0:~$ ls /media/iphone/iTunes_Control/Music/F00/
satimis@vz0:~$ ls /media/iphone/iTunes_Control/Music/F01/
satimis@vz0:~$ ls /media/iphone/iTunes_Control/Music/F02/
satimis@vz0:~$ ls /media/iphone/iTunes_Control/Music/F03/
satimis@vz0:~$ ls /media/iphone/iTunes_Control/Music/F48/
satimis@vz0:~$ ls /media/iphone/iTunes_Control/Music/F49/
I suppose all of them are empty directories


satimis@vz0:~$ ls /media/iphone/Photos/
satimis@vz0:~$ ls /media/iphone/Podcasts/
satimis@vz0:~$ ls /media/iphone/Purchases/
All of them without output


satimis@vz0:~$ ls /media/iphone/Recordings/```

Recordings.db
```


satimis@vz0:~$ ls /media/iphone/iTunes_Control/Ringtones/
No output


No GUI.  I think I can upload music/photo files on the IPhone.  

What shall I do next?  To copy music files to the IPhone on Console?  .mp3 file?  Or other file format?

Please advise.  TIA

B.R.
satimis

---

### Post by Cheesemill on 2009-11-23
> **Cheesemill said:**
> How do you know that your phone is jailbroken? Did you do it?

If not and it's a new model (firmware v3) then

[SIZE=2]***There is no way to transfer your music onto it!!***[/SIZE]
(unless you run a Windows VM but you say this isn't an option)

All the other features will work (photos etc) because these are simply stored as normal files. However, the music database is encrypted and Apple wont tell anyone how they've done it.

Did you read this satimis?

There is no way to get your iPhone to recognise any music that you put on it until someone breaks Apples encryption, unless you run a Windows VM.

---

### Post by goodrench on 2009-11-24
> **Cheesemill said:**
> There is no way to get your iPhone to recognise any music that you put on it until someone breaks Apples encryption, unless you run a Windows VM.

I am currently using iFuse and usbmuxd on my ipod touch 3rd gen with 3.1.2 firmware (no Jailbreak) synking over usb and it woks perfectly.
As for transfering music and podcasts, I have found that only gtkpod will work.
It updates the apple database without complaint.
The only concern I have is that usbmuxd package is not available for 64bit. You need to compile it yourself.

---

### Post by windowsfree on 2009-11-24
I really like SongBird, but you should know I have a very old IPOD shuffle.

---

### Post by satimis on 2009-11-24
> **goodrench said:**
> I am currently using iFuse and usbmuxd on my ipod touch 3rd gen with 3.1.2 firmware (no Jailbreak) synking over usb and it woks perfectly.

Hi goodrench,

With usbmuxd and iFuse, on console I can now copy mp3 files to /media/iphone/iTunes_Control/Music/F00/.  The file copied can be viewed on console.  But it can't be read on IPhone after switching it on.  Whether I have to copy the music file .mp3 on /media/iphone/Podcasts/ then I can read the same on IPhone.  How to find the firmware version and to check whether the IPhone is jailbroken

> 
As for transfering music and podcasts, I have found that only gtkpod will work.
It updates the apple database without complaint.

I'll install gtkpod to test it later.

> 
The only concern I have is that usbmuxd package is not available for 64bit. You need to compile it yourself.
This is an old PC running 32 bit Ubuntu 8.04.


B.R.
satimis

---

### Post by chickenpatty878 on 2009-11-26
Eh, quick question. I have installed iTunes with Wine, work great, but it doesn't recognize my iPhone. I probably sound silly, but how do i get iTunes to mount it? I think i skipped a step somewhere, but which one? I have mounted it before on a different system using ubuntu, i just forget how and can't find a solution.

Edit -  Never mind, figured out what I did. Sucsk that you cant transfer with firmware v.3

---

### Post by satimis on 2009-11-26
> **chickenpatty878 said:**
> 
Edit -  Never mind, figured out what I did. Sucsk that you cant transfer with firmware v.3
Hi chickenpatty878,

Could you please explain in more detail how to do it?  TIA.

Which version of iTunes, 8 OR 9, you installed?

Can the music files upload to IPhone work?  .mp3, .wav, etc.

How to find out the version of firmware running on IPhone?

Thanks


B.R.
satimis

---

