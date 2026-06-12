---
title: "Can we expect to see some mobile phone support anytime soon?"
date: 2006-06-01
forum: General Help
---

### Post by SlugO on 2006-06-01
Now that Ubuntu (and Linux in general) has a fairly good mp3 player support it would be nice if someone gave a bit attention to mobile phones in Linux. More and more people are using them as mp3 players, cameras and all around mobile "computers" with all kinds of programs so not being able to connect your mobile phone to a computer is not acceptable anymore. It just loses half of its usability without the connection.

Based on what I have searched it seems that support for mobile phones in Linux is very limited. There are some guides about connecting with Bluetooth here (what about USB?) and some mentions that gnokii might work if you're lucky. I tried it. Awful interface, froze every time ](*,)

So are there any improvements for mobile phone support in sight?
The situation at the moment is lousy to say the least.
As long as Linux can't communicate with mobile phones, Windows is a necessity.

---

### Post by Kuprin on 2006-06-01
He's right, that needs to start happening now.

---

### Post by onesojourner on 2006-06-01
I agree. I would also like to connect my dell axim x50v... there is always vmware though for that. phones/pdas need to standardize some stuff and it will be much easier.

---

### Post by spiritraveller on 2006-06-01
[My phone](http://www.nokiausa.com/phones/9300/0,7747,,00.html?cpid=ILC-2001-106) (Nokia 9300) interfaces very well with Linux.

Most of the Symbian phones from Nokia will run [Putty for SSH](http://s2putty.sourceforge.net/), allowing you to login to your computer over GPRS/EDGE and execute commands, check your email, etc.

Another solution is to run your own syncml server (if your phone supports syncml).  The [funambol](http://www.funambol.com/opensource/) project (formerly known as sync4j) provides a syncml server that you can use to sync your contacts and calendar entries over the air.  And it really does work.

Bluetooth is a pain in Linux (though I think it's come farther in KDE).  So my solution is to use GPRS or EDGE instead.

---

### Post by blakamin on 2006-06-01
geez, I'd still like a working serial port in WINE... that said, I'd like my old sony ericsson to talk to my Ir port!

---

### Post by onesojourner on 2006-06-01
[QUOTE=spiritraveller][My phone](http://www.nokiausa.com/phones/9300/0,7747,,00.html?cpid=ILC-2001-106) (Nokia 9300) interfaces very well with Linux.
[/QUOTE]

(warning off topic)
I was just looking at that phone. how do you like it?

---

### Post by diebels on 2006-06-01
[QUOTE=spiritraveller][My phone](http://www.nokiausa.com/phones/9300/0,7747,,00.html?cpid=ILC-2001-106) (Nokia 9300) interfaces very well with Linux.

Most of the Symbian phones from Nokia will run [Putty for SSH](http://s2putty.sourceforge.net/), allowing you to login to your computer over GPRS/EDGE and execute commands, check your email, etc.

Another solution is to run your own syncml server (if your phone supports syncml).  The [funambol](http://www.funambol.com/opensource/) project (formerly known as sync4j) provides a syncml server that you can use to sync your contacts and calendar entries over the air.  And it really does work.

Bluetooth is a pain in Linux (though I think it's come farther in KDE).  So my solution is to use GPRS or EDGE instead.[/QUOTE]How many people have GPRS/EDGE in their computer? The focus should be on fixing bluetooth.

---

### Post by spiritraveller on 2006-06-01
> Originally Posted by **onesojourner**
I was just looking at that phone. how do you like it?

I like it a lot.  The qwerty keyboard is the best I've seen.

> Originally Posted by **diebels**
How many people have GPRS/EDGE in their computer?

GPRS is a way for your phone (a GSM phone) to get online.  Non-GSM phones can also get online using different technology, but the same technique applies.

Your computer does not need to "have GPRS" for your phone to connect with it.  The way it works is that your phone connects to your computer via the internet.

---

### Post by ketsugi on 2006-06-02
GPRS syncing would be great; all I'd need to do is have my phone sync directly with Google Calendar for events and maybe Plaxo (?) for contacts...

---

### Post by Rizado on 2006-06-02
I have a K700i and with kubuntu it works great. I can browse it in konqueror, send things really easy by right clicking on a file and choose send and when I send something from the phone a dialog pops up. Kbluetoothd handles it perfectly and I never need to use hcitool. Also after some fiddeling around I can connect through gprs and remotecontrol my computer. There's a app called KMobileTools. With it I can read and send sms's and call people (I have to talk through the phone though.) I haven't tested but I think I can sync with kde address book. I can see Signall and battery level and I get small notices about important things like low battery level, incomming call and sms's. Plus a lot more I haven't figured out yet.

---

### Post by stimpsonjcat on 2006-06-02
gnome-bluetooth works very well with my nokia 6230 (series 40). I agree it would be nice to have some usable contact sync support.

---

### Post by ketsugi on 2006-06-02
stimpsonjcat: yes, I like having the bluetooth file transfer active, as well as the sms sending. But I would really like to have proper calendar and contact (and to-do) syncing soon. I just bought a Nokia 6280 and it pains me to have to boot into Windows just to backup my phone every now and then. Although admittedly I have to do that for my iPaq anyway. :(

---

### Post by SlugO on 2006-06-02
Has anyone got their USB connection to work with a mobile phone? I have that because of the better connection speed.

And yes, GPRS/EDGE might work with some light stuff like syncing information but what about if you want to transfer hundreds of megabytes of mp3's? Do you know the cost of GPRS data transfers?! Even with a fixed price there's usually a limit of a few dozen megabytes. So GPRS is just too expensive to be really useful with a computer.

---

### Post by simplyw00x on 2006-06-02
I managed to get my Motorola V635 talking to my computer over USB in a past install of Dapper, but only to use moto4lin - I couldn't get multisyns or similar working.

---

### Post by SlugO on 2006-06-02
Seeing as how many people have a cell phone that can be connected to a computer I find it suprising how neglected their support in Linux actually is... :-k

---

### Post by SynapseR on 2006-06-02
Can anyone point me to a guide that explains how to use a cellphone as a GPRS modem via Bluetooth or USB Cable ? I use this alot with XP on my other notebook and would love to have this functionality on my Ubuntu Notebook.

Thanks
[http://digitalife.wordpress.com](http://digitalife.wordpress.com)

---

### Post by Jammy_Stuff on 2006-06-02
I'm getting a Samsung D600 in a few days and I'll post to let you know how well that interfaces.

---

### Post by spiritraveller on 2006-06-02
For people with phones that speak SyncML, the best solution may be to use [Funambol](http://www.funambol.com/) over bluetooth or a usb cable.  It is licensed under the GPL, and is very versatile.  The only drawbacks are that it depends on Java, and it's not a simple program.

Since it uses an IP connection, the only thing we would have to figure out is how to create an IP connection over bluetooth or USB cable.  This has already been done, and there are some how-to for various phones on the web.

With my 9300, I've gotten it to work with funambol via GPRS before.  Admittedly, that is not the most efficient connection, but it demonstrates that funambol will work at syncing contacts and calendar with a SyncML phone.

---

### Post by Skye on 2006-06-02
Quite a few mobile phones and PDAs now run Windows Mobile 5, and unfortunately, WM5 support in linux is lousy.  I too would like to be able to sync my Axim x51 (WM5) to my ubuntu PC- as of now, it needs to be used in conjunction with a windows PC.

I think the synce project is working to address this, but I don't know how stable or effective it is.

---

### Post by diebels on 2006-06-02
[QUOTE=spiritraveller]
Your computer does not need to "have GPRS" for your phone to connect with it.  The way it works is that your phone connects to your computer via the internet.[/QUOTE]
Oh, I thought your computer had an GPRS pcmcia card. But what you're saying is that you connect your computer to internet(somehow), then you connect your phone to the internet via GPRS. Now they can communicate over the internet.

Works fine when you have another internet connection for your computer. Not so fine when you want to connect the computer to the internet with the phone over bluetooth, if bluetooth is not functioning proplerly.

---

### Post by msak007 on 2006-06-07
I agree with needing more phone support. I've had a hell of a time trying to get anything onto my Nokia 6682. It's a Symbian phone, so I would like to be able to transfer MP3 ringers and .SIS files (program installers) to install apps. Currently, the USB cable doesn't work. I can pair it with my Bluetooth dongle, but when I try to send files using the OBEX Push Client it goes to a default directory on the phone's internal memory, and always errors out about not having enough space. I can't find an option anywhere in the OBEX client to change the default path or be able to browse the phone or send files to my memory card. In windoze, I used the Nokia app to send files / ringers and install apps just by double-clicking on them. At this point I'd just be glad to be able to see my phone as a device that I can browse and send files to / from it, preferably using the USB cable.

---

### Post by techstop on 2006-06-07
I sent an email off to Nokia "suggesting" that they look into providing a Linux client for their PC Suite software. This is the confused response I got;

> With regard to your enquiry, please be advised that Nokia currently does not have any software or drivers compatible with Linux. We do apologise for the inconveniences caused.

The Nokia PC Suite software that enables the phone to connect to computers is designed to be compatible with the Windows Operating system. Your best option at this point in time is to get in touch with Linux. Please enquire if they have software that facilitates connection and synchronization between a Nokia mobile phone and a Linux operating system.

Should you have any further enquiries, or if we can be of any assistance, please do not hesitate to contact the Nokia Careline and speak to any one of our friendly Technical Support Executives.....BLAH, BLAH, BLAH

Note, I should be "getting in touch with Linux" to see if they have software available. ](*,)  What next from here? I might email them again...

---

### Post by handy on 2006-06-07
The ability to consistantly interface with **windoze CE** devices is a most desirable ability for Ubuntu, for **ALL** of the obviouse reasons. 

(I read the first page & skipped to here, hope I'm not duplicating? :rolleyes:)

---

### Post by viciouslime on 2006-06-07
You're not an yes I have a nokia 6680 and a dell axim x30 pocket pc. Neither of which sync with linux. I have managed to get the axim to sort of sync. But it's not very practical and it certainly isn't something for beginners.

I think this feature of ubuntu really needs looking at as it would make the transition for businesses a lot easier. They want to plug their device in and have it sync automatically; no configuration.

---

### Post by Beej on 2006-06-07
I had trouble getting my Motorola L7 to sync with gnomes tools by USB, but the no problems with the svn version of kmobiletools which seems to be miles ahead of the game. I had copied my address book to a file and imported into evoultion within about 2 mins of having it install, and was typing text messages on my keyboard. I seriously reccommend having a go.

[http://kmobiletools.org/svn](http://kmobiletools.org/svn)

---

### Post by techstop on 2006-06-07
It's not really up to Ubuntu though is it? I mean, the hardware manufacturers would have to release their specs so that the software can be written? Or, they can write the software themselves? I'm waiting for some phone company to lead by example here. I base other hardware purchasing decisions based on linux compatibility (hello? ati?), so its a shame that there aren't mobile phone manufacturers who are setting an example...

---

### Post by bluenova on 2006-06-07
I don't see what the big problem is? I use both Gnome and KDE bluetooth and phone tools, and they work fine. Sure it takes a bit of time to get pairing sorted out, but I'm sure that will be sorted once and for all in the near future.

---

### Post by handy on 2006-06-07
[QUOTE=bluenova]I don't see what the big problem is? I use both Gnome and KDE bluetooth and phone tools, and they work fine. Sure it takes a bit of time to get pairing sorted out, but I'm sure that will be sorted once and for all in the near future.[/QUOTE]

When things work for us, we never see the problem, it is only when things don't work for us that we see the problem!!!

That is one of the first lessons of life my friend... :KS

[Edit:]  Sorry, don't read that as a put down, because that is not how it was intended.

---

### Post by ckempo on 2006-06-07
My Sony K750i works perfectly via the usb cable that comes with it... can upload/download mp3s, photos, themes, all sorts to/from it. Only thing I miss is something as powerful as FMA on Windows for backing up the inbox etc.

---

### Post by techstop on 2006-06-07
Unfortunately, connecting my Nokia 6280 hangs Nautilus. It's a no-go zone at this point.

---

### Post by jon_benge on 2006-06-07
[QUOTE=ckempo]My Sony K750i works perfectly via the usb cable that comes with it... can upload/download mp3s, photos, themes, all sorts to/from it. [/QUOTE]

The Sony w800i walkman phone is compatible with (k)ubuntu if anybody cares. It mounts automatically like a USB disk. I've had no problems whatsoever.

Not sure about the ability so sync the address book as I haven't tried to yet.

---

### Post by msak007 on 2006-06-07
What do the Sony USB cables look like? The problem with the Nokias I think (mine anyway) is it's the DKU-2 USB cable, which has a proprietary adapter / end that plugs into the phone (see picture attached). From what I've read the computer doesn't really detect it as a USB device, and hence it's not mounted as a USB device that is browseable. If it was I wouldn't be complaining...

P.S. I agree that this isn't an Ubuntu specific problem, as I've had the same problem with other distros. It is a problem with phone manufacturers in general neglecting Linux users for both hardware and software support. I think Nokia's generic B.S. response demonstrates their ignorance ("get in touch with Linux?") Their copout is to suggest looking to someone else for help rather than trying to work with the OSS community to provide the information needed to get devices working and software developed? We should be used to it by now because that's pretty much the response you get from any company you contact for Linux support, but it still sucks. As much as I love Nokias, if Sonys do really interface well with Linux then Nokia just lost a customer *adds Nokia to the sh!t list with ATI*

---

### Post by SlugO on 2006-06-07
I sure would like to read some HOWTO's or program suggestions from the ppl in this thread who got their USB connection to work (especially with Nokia's). There's hardly any information about that in the forums, especially when it comes to file transfers.

I agree that mobile phone manufacturers need to start supporting Linux. Nokia seems to have more and more double standards. It has that portable Linux tablet thing and is calling for open source developers to do stuff for it but on the other hand they try to force software patents into Europe and don't support Linux one bit.

Maybe they'd start to notice the benefits of supporting Linux if we reminded them how much it affects our buying decisions, how much they'd get good PR with open source ppl and how for example NVIDIA is the choice of just about every person who knows he'll be using Linux on the computer. Maybe...

---

### Post by ketsugi on 2006-06-07
[QUOTE=techstop]Unfortunately, connecting my Nokia 6280 hangs Nautilus. It's a no-go zone at this point.[/QUOTE]

By the USB cable or by Bluetooth?

FWIW both have been working fine for me, with my Nokia 6280.

---

### Post by techstop on 2006-06-08
By cable....What connection mode do you select on the phone? And then what happens, do you get to browse the phone and mini-sd card with Nautilus? Transfer mp3's, photos, ringtones etc? I'd also like to be able to sync with Evolution, that would be awesome.

Also, what firmware do you have on your phone? Mine is 3.40, which is known to buggy in general, but seems to be fine in all other aspects for me (ie, no blank screens, crashes, turning off etc). I'd like to get this working....

---

### Post by ketsugi on 2006-06-08
Data storage mode. I haven't tried the other two modes with Dapper yet.
Using this mode for the phone gives me full access to the mini-SD card (but not the phone's internal memory). Syncing is a whole other matter (ie, don't count on getting THAT working anytime soon).

Remember to eject the device properly as often data doesn't actually get written until you do so.

How do I check my firmware version?

---

### Post by techstop on 2006-06-08
To check the f/w, press these buttons on your phone;

*#0000#

EDIT: Just tried data mode, the phone shows up in Nautilus, but it doesn't mount. I get the following error when I double-click on the phone icon in Nautilus;

> Unable to mount the selected volume.

mount: /dev/sdb: can't read superblock

error: could not execute pmount

---

### Post by ketsugi on 2006-06-09
```
Nokia 6280
V 03.60
10-02-06
RM-78
(c) Nokia
```

---

### Post by techstop on 2006-06-09
So you have v3.60 firmware. Any pointers on how to solve the mounting issue I have?

---

### Post by ketsugi on 2006-06-09
No idea, given that it just completely worked out of the box for me. Maybe you could try bringing your phone down to a Nokia care centre and having it flashed with new firmware? I haven't had any problems with the 3.60 firmware so far.

---

### Post by SlugO on 2006-06-09
Wow :eek: My Nokia 6131 actually worked perfectly as a USB drive with data transfer mode :D Guess I should have checked out all the modes before complaining..

It only lets me browse the microSD card and transfer files but that's okay cos I have no need for anything else. Have to remember to unmount it properly to upload the stuff though. Too bad Ubuntu seems to always freeze after unmounting... But I guess that's cos of my Dapper that I updated from Breezy, it does funny stuff sometimes.

---

### Post by jon_benge on 2006-06-11
[QUOTE=msak007]What do the Sony USB cables look like? The problem with the Nokias I think (mine anyway) is it's the DKU-2 USB cable, which has a proprietary adapter / end that plugs into the phone (see picture attached).[/QUOTE]

I used to have a Nokia with one of those cables. I had trouble getting it to work with Windows, let alone Linux :( The DKU-2 cable needs special drivers as it's not seen as a normal USB cable.

The sony cable looks similar to the DKU-2, but it acts like a normal USB cable so it doesn't need special drivers.

[quote=techstop]EDIT: Just tried data mode, the phone shows up in Nautilus, but it doesn't mount. I get the following error when I double-click on the phone icon in Nautilus; [/quote]

Have you tried putting a static entry in FSTAB?

Try this:

```
sudo mkdir /media/phone
```

```
sudo nano /etc/fstab
```

Add the following into the file:

```
/dev/sdb /media/phone fat utf8,umask=007,gid=46,user,rw,noauto 0 0
```

Press 'Ctrl+X', followed by 'Y' and 'Enter'.
 
Then mount it with:

```
mount /media/phone
```

---

### Post by techstop on 2006-06-11
Thanks for the suggestion, but still no go. I had to change "fat" to "vfat" in the fstab line you provided, then I remounted the phone. It didn't complain about not being able to mount, just that it "can't read superblock". Here are my mounted devices below (1 x 250GB NTFS, 1 x 80GB ext3, 1 x 2GB FAT ; the phone sd-card, and 1 x 256MB FAT32 USB memory stick)

```
barney@ubunutu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9351    75111876   83  Linux
/dev/hda2            9352        9729     3036285    5  Extended
/dev/hda5            9352        9729     3036253+  82  Linux swap / Solaris

Disk /dev/sdc: 262 MB, 262012928 bytes
16 heads, 32 sectors/track, 999 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         999      255728    b  W95 FAT32
Note: sector size is 1024 (not 512)

Disk /dev/sdb: 2042 MB, 2042102784 bytes
63 heads, 62 sectors/track, 510 cylinders
Units = cylinders of 3906 * 1024 = 3999744 bytes

   Device Boot      Start         End      Blocks   Id  System
barney@ubunutu:~$

```

Interesting that there are no filesystem block details for the phone listed...

Anyway, enough of the off-topic, I will try to sort this out...

---

### Post by ketsugi on 2006-06-11
Just wondering if it's worth trying to reformat the miniSD card? Maybe there's a problem with the filesystem on the card itself.

---

### Post by techstop on 2006-06-12
The card is fine under Windows....

---

### Post by knubbe on 2006-06-13
I have a Nokia 6280. It worked fine using USB cable + data storage mode - then i used it in windows and not it doesnt work in my kubuntu anymore. 

Error message (freely translated):

Could not mount the unit
mount: can't find /dev/sdb in /etc/fstab or /etc/mtab

It still works in windows thought.

---

### Post by knubbe on 2006-06-13
By the way, anyone knows how to use a mobile phone as a (broadband) modem?

---

### Post by marcw on 2006-06-13
[QUOTE=knubbe]By the way, anyone knows how to use a mobile phone as a (broadband) modem?[/QUOTE]

There's several threads here about just that topic.  Search for GPRS or Bluetooth cell modem or some such thing and I'm sure you'll find them.  I got my little Dapper Thinkpad X21 to use use my RAZR as a modem using a Bluetooth dongle.  Definitely not broadband.  It was roughly the same speed as my old dial up days.  It made me wish I had a phone that did EDGE.

---

### Post by ketsugi on 2006-06-14
[QUOTE=knubbe]I have a Nokia 6280. It worked fine using USB cable + data storage mode - then i used it in windows and not it doesnt work in my kubuntu anymore. 

Error message (freely translated):

Could not mount the unit
mount: can't find /dev/sdb in /etc/fstab or /etc/mtab

It still works in windows thought.[/QUOTE]

So it seems that Windows is the weak link here? I've never mounted my phone in Windows using data storage mode, only the normal mode for phone syncing.

---

### Post by Christmas on 2006-06-14
I have this Samsung Z500 mobile phone and I couldn't transfer the pictures from it to my computer. There are only two apps in the repositories, and both are not for transferring data, something like zulu or whatever and another one. After I plugged in the USB cable the phone was detected, it appeared in the Devices panel, but I couldn't make it transfer my pictures. And on the Samsung CDs that came with the phone is just Windows software, I hate them for not supporting Linux too! I guess I'll wait and make my job on a Windows machine, as the installation of the Windows software using Wine failed.

---

### Post by bman on 2006-06-15
I haven't really had time to read this thread, but I have a Motorola Razr, is there drivers, or has someone got this to work with ubuntu?

I have been using programs with windows for awhile, any ideas?

---

### Post by shinygerbil on 2006-06-16
[QUOTE=jon_benge]The Sony w800i walkman phone is compatible with (k)ubuntu if anybody cares. It mounts automatically like a USB disk. I've had no problems whatsoever.

Not sure about the ability so sync the address book as I haven't tried to yet.[/QUOTE]

I've just bought a W810i; no such luck for me. Can you give me any more details? Which mode do you run it in? I'd love to be able to do this :/

---

### Post by seuaniu on 2006-06-16
Bluetooth connections were something I wanted to tackle a couple of months ago, and have gotten it working pretty well :p 

The short answer to the original poster is that, yes, you can have bluetooth syncing with linux.  The long answer is that it'll take a little work.

First thing to do, as you should be doing with all hardware purchases, is do a little research.  After looking around for a bit, I settled on a Sony Erricson Z520a telephone.  It has all the nifty modern features, and supports syncml.  For those who don't know what that is, syncml is for syncing data, and its a published standard.  Published standards are good because somebody with an itch to scratch and some programming skills can write a connector (and they did!).  

I also looked around and settled on a bluetooth dongle (can't remember the brand, and i'm not at home to look) that had linux support.

There is a syncml client that runs on gnome.  What you do is set up the pairing, which took me a bit of futzing around with the pin file, etc. 

 After thats set up, you set up a connector with Evolution to sync your contacts, calendar, etc. and you're good to go.

I don't use the file transfer so much, but there is good documentation about the gnome-obex-push program around on the internet.  

  Whenever I walk into my apartment, if I left my computer with me logged in, my phone does a  little ring, and syncs my calendar and contacts.  Very nifty.

Anyway, while the setup process isn't so slick, it is doable, without too much effort.  Perhaps as time goes on, somebody will make a nice gui that'll handle all the setup, PIN, discovery, sync issues, etc.

Perhaps I'll write a howto in the near future.  For now, here's some links:

[http://www.cnpbagwell.com/Z520a/HomePage]("http://www.cnpbagwell.com/Z520a/HomePage")
This one is fedora specific, and there are some differences with Ubuntu, but it gave me just about everything I need.

[http://sourceforge.net/projects/sync4jevolution]("http://sourceforge.net/projects/sync4jevolution")
This is a syncml plugin for evolution.

As an aside, once you get the file transfer worked out, on a z520a phone like mine (cingular is my carrier), you can use audacity to cut out and downsample portions of your music collection, upload them to your phone, and use them as ringtones!  total time waster, but I hate that the service providers try to charge you $3 to rent a ringtone for a couple months, so I cut them out of the loop.

---

### Post by jon_benge on 2006-06-17
[QUOTE=shinygerbil]I've just bought a W810i; no such luck for me. Can you give me any more details? Which mode do you run it in? I'd love to be able to do this :/[/QUOTE]

There's no black magic to it. ;)  I simply plugged in my phone to the USB port and both my Kubuntu and Ubuntu machines detected it. An icon appeared on the desktop and it mounted automatically.

The w810i is basically the same as the w800i, so it does work. Which version of (X/K)ubuntu are you using? I am using Dapper

---

### Post by shinygerbil on 2006-06-17
> **jon_benge]There's no black magic to it.  said:**
> 

I'm on Kubuntu Dapper, although it was originally a Hoary Ubuntu installation which has survived two dist-upgrades, and had most of Gnome chopped out. (I know, I'm lucky ;) )

What happens for me is two Konqueror windows open up, and try to mount the phone. I then get two errors:

[quote=Konqueror]Could not mount device.

The reported error was:

mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

And exactly the same in the other window but sdb1 instead of sda1. (amaroK also pipes up wanting to control the devices.) If I then go to media:// I find two unmounted devices - PHONE and PHONE CARD. I'm guessing these are the ones ;)

How are they mounted on your system?

Thanks

Steve

EDIT: After googling for 'w810i filesystem' I am led to a Swedish Slackware forum, in which, as far as I can tell, someone else has the same problem as me. Luckily there is a solution :) It's a VFAT filesystem. But before I go ruining my phone (as often happens when using my mp3 player in Linux) can you confirm that? Thanks :)

---

### Post by jon_benge on 2006-06-18
It appears as '491M Removable Media'. Filesystem is vfat.

I think the upgrades from Hoary might be the reason for it not working. The automount system in Breezy wasn't very good. Infact, it completely failed on me. Perhaps a clean install of Dapper will sort it?

*Copied from an earlier post*

Have you tried putting a static entry in FSTAB?

Try this:

```
sudo mkdir /media/phone
```

```
sudo nano /etc/fstab
```

Add the following into the file:

```
/dev/sda1 /media/phone vfat utf8,umask=007,gid=46,user,rw,noauto 0 0
```

Press 'Ctrl+X', followed by 'Y' and 'Enter'.
 
Then mount it with:

```
mount /media/phone
```

---

### Post by shinygerbil on 2006-06-18
Hi,

Forgot to post about my success! Too busy putting stuff on my phone ;) I fiddled with fstab last night until it worked the way I want it, so all is good! Thanks very much for your help anyway :)

Steve

---

### Post by MattToner on 2006-06-18
3.65 is the latest for generic handsets and 3.70 for handsets on the 3 network. (i work for a CNSp) :P

but at the moment we have loads of questions regarding sync'ing in linux, i have asked our BDE's but no one has any answers on when this will happen :(

---

### Post by Bost on 2006-06-18
[QUOTE=ckempo]My Sony K750i works perfectly via the usb cable that comes with it... can upload/download mp3s, photos, themes, all sorts to/from it. Only thing I miss is something as powerful as FMA on Windows for backing up the inbox etc.[/QUOTE]

And what about the bluetooth connection? I cant get any. I searched I bit around ([http://www.watkissonline.co.uk/linuxbluenet.html](http://www.watkissonline.co.uk/linuxbluenet.html) seems to be usefull) and I found that there must be something wrong with the interface. 
hciconfig shows me nothing :( could you tell me how is it on your system? thx

---

### Post by FelixNZ on 2006-06-26
I just got my 6680 and I can't find this connection mode - data storage thing you guys are talking about, its not in the manual anywhere?

---

### Post by techstop on 2006-06-26
[QUOTE=FelixNZ]I just got my 6680 and I can't find this connection mode - data storage thing you guys are talking about, its not in the manual anywhere?[/QUOTE]

We've been talking about the 6280, not sure if the 6680 is the same. Anyway, when you plug the phone cable into a USB port, the phone comes up with a prompt asking for the connection mode. If it doesn't come up on your 6680 and it's not in the manual, I'd say it's not part of the 6680.

---

### Post by Jussi Kukkonen on 2006-07-05
[QUOTE=Christmas]I have this Samsung Z500 mobile phone and I couldn't transfer the pictures from it to my computer. There are only two apps in the repositories, and both are not for transferring data, something like zulu or whatever and another one. After I plugged in the USB cable the phone was detected, it appeared in the Devices panel, but I couldn't make it transfer my pictures.[/QUOTE]

I haven't tested this, but if I understand the device info correctly the internal memory is not a usb mass storage device, but any added memory chips will be shown as USB mass storage devices. So, if you buy a microSD  memory card, it should be automounted when you plug in usb...

---

### Post by KaridaSerious on 2006-07-05
Have you tried obexftp yet? Does it suit your needs?

[http://packages.ubuntulinux.org/dapper/comm/obexftp](http://packages.ubuntulinux.org/dapper/comm/obexftp)

Until I get home, I will give this program a try. I have a Nokia N70

- KDS

---

### Post by hiro.durden on 2006-07-15
People... I have a Motorola v360 but I just can't mount the SD card (at ubuntu 6.06). Initially, when I plug it things work fine:

[COLOR="Blue"][17186022.708000] usb 2-1: USB disconnect, address 2
[17186033.848000] usb 2-1: new full speed USB device using ohci_hcd and address 3
[17186034.072000] usb 2-1: configuration #1 chosen from 2 choices
[17186034.084000] scsi2 : SCSI emulation for USB Mass Storage devices
[17186034.084000] usb-storage: device found at 3
[17186034.084000] usb-storage: waiting for device to settle before scanning
[17186039.172000]   Vendor: Motorola  Model: Motorola Phone    Rev: 2.31
[17186039.172000]   Type:   Direct-Access                      ANSI SCSI revisio n: 02
[17186039.196000] SCSI device sda: 246017 512-byte hdwr sectors (126 MB)
[17186039.208000] sda: Write Protect is off
[17186039.208000] sda: Mode Sense: 0b 00 00 08
[17186039.208000] sda: assuming drive cache: write through
[17186039.256000] SCSI device sda: 246017 512-byte hdwr sectors (126 MB)
[17186039.268000] sda: Write Protect is off
[17186039.268000] sda: Mode Sense: 0b 00 00 08
[17186039.268000] sda: assuming drive cache: write through
[17186039.268000]  sda: sda1
[17186039.320000] sd 2:0:0:0: Attached scsi removable disk sda
[17186039.320000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17186039.320000] usb-storage: device scan completer
[/COLOR]
But when I double click it at Nautilus I got this:

[COLOR="Blue"]mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
[/COLOR]
Looking at dmesg I've got things like this:

[COLOR="Blue"]sd 2:0:0:0: SCSI error: return code = 0x8000002
end_request: I/O error, dev sda, sector 0[/COLOR]

I saw somebody talking about incompatibility between windows and linux way of I/O'ing the FS... but, nobody have other things to say!?

Thanks.

---

### Post by skwashd on 2006-07-15
I have a Nokia 6280 (firmware v3.81).  I have been playing with opensync (opensync.org) to get sync working without luck.  I can dump from my phone to my laptop, but as soon as data goes the other way the phone reboots ... grrr!  The usb mass storage works but is frustrating as vcards/icals aren't recognised/read by the phone.

I am planning to test funambol when i have some spare time.

My last phone SE v600i (aka k600i/k608i) allowed me to use obexftp (latest compiled from source) to copy music, vcards etc from my laptop to my phone which worked well.  The phone didn't show up as a usb mass storage device tho.

I will report back with more news as it comes to hand :)

---

### Post by fragmented_user on 2006-07-21
Mobile phone support has arrived, in the form of a download that includes Serial to USB support and documentation, and information about using your phone via Bluetooth or for Dial up networking. 

check out [http://ubuntuforums.org/showthread.php?t=221364](http://ubuntuforums.org/showthread.php?t=221364)

---

### Post by fragmented_user on 2006-07-21
mods delete this post.

---

