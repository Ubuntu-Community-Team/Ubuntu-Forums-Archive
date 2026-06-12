---
title: "Nokia N97 and Ubuntu"
date: 2009-08-26
forum: General Help
---

### Post by caco on 2009-08-26
Hello all, I hope we could document all the things we could do with the might Nokia N97 and our lovely Ubuntu. For your information I used ubuntu 9.04:).

Ps ... you can also add stuff done with ubuntu 9.10 ;)

Presently using Ubuntu 10.04 LTS Lucid Lynx and seems to be working with my Nokia N97

[[IMG]http://brainstorm.ubuntu.com/idea/20470/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/20470/)

---

### Post by caco on 2009-08-26
Usually updating the Nseries phone usually required a windows system and Nokia pc suite or Nokia Ovi. But the N97 packs a software updater inbuilt for most of its applications, except the phone's firmware which still requires the windows system.

Since I did away with windows as a personal & primary OS ( I have it inside virtualbox), the drama of updating with my virtual Vista began. Initially all went as planned as par downloading the updates, until the phone had to reboot and complete its update ... nothing happened. After some investigations, I found out that the enabled Nokia 0100 usb filters where not the only one the N97 uses. Hence I had to enable all usb filters and after that my N97 firmware update was successful.

In your virtualbox add and enable all usb filters, for phone update to work. Usually I think the N97 uses usb filters  0100-Nokia N97, 0281-Nokia usb Rom and 0001-Nokia BBL.

Presently running firmware v12.0.024 on the Nokia N97, virtualbox v3.0.4 r50677, and an updated Ubuntu 9.04:P

---

### Post by caco on 2009-09-02
Setting the N97 as a 3.5g modem for use with my Laptop was easy ... all I had to do was set the phone's usb connection mode to pc suite, then follow the follow the instructions that appear on the mobile broadband wizard that appears on your ubuntu's desktop.

Setting the N97 usb connection mode to mass storage allows you to mount the 32gb mass storage or the memory card in the phone, if available. Eject as usual from ubuntu to remove the mounted device.

---

### Post by caco on 2009-09-15
If you want to convert your video files to a format that the N97 would recognise easily and play try this code ```
ffmpeg -i YourMovie.avi -b 2300k -r 30 -s 640x360 N97movie.mp4

```
in the folder where YourMovie.avi or whatever is located. Copy your finished work either by plugging the N97 as a mass storage or using the your SD card.

Have fun:popcorn:

---

### Post by yuki86 on 2009-09-23
Great thanks for info, I am looking for replacement for my htc:lolflag:

---

### Post by chriswyatt on 2009-10-02
I updated my N97 but I just used the vendor ID (0421) as my filter.  Would it have needed any other vendor IDs?

Anyway, it said it failed, but when I restarted the phone it had the new software and fingers crossed everything is OK.

---

### Post by caco on 2009-10-06
I don't think so. If you want to play it safe next time enable all filters. Just waiting for the next firmware update :popcorn:

---

### Post by dudu1975 on 2009-12-09
Hi folks,

What about Evolution synchronization to contacts, calendar, tasks, notes? Anyone made it work?

Regards,
Eduardo

---

### Post by romulor3 on 2009-12-11
> **caco said:**
> If you want to convert your video files to a format that the N97 would recognise easily and play try this code ```
ffmpeg -i YourMovie.avi -b 2300k -r 30 -s 640x360 N97movie.mp4

```
in the folder where YourMovie.avi or whatever is located. Copy your finished work either by plugging the N97 as a mass storage or using the your SD card.

Have fun:popcorn:
HI everyone, thanks for the tips!
Caco, your line to convert videos to a format easily recognizable for our N97's is great. Produces larger files but that's no problem with 32GB space. So going a little further (in output filesize) I've obtained better audio results just adding the option
        -acodec copy
just before "N97movie.mp4".

---

### Post by romulor3 on 2009-12-11
> **caco said:**
> If you want to convert your video files to a format that the N97 would recognise easily and play try this code ```
ffmpeg -i YourMovie.avi -b 2300k -r 30 -s 640x360 N97movie.mp4

```
in the folder where YourMovie.avi or whatever is located. Copy your finished work either by plugging the N97 as a mass storage or using the your SD card.

Have fun:popcorn:
HI everyone, thanks for the tips!
Caco, your line to convert videos to a format easily recognizable for our N97's is great. Produces larger files but that's no problem with 32GB space. So going a little further (in output filesize) I've obtained better audio results just adding the option
        -acodec copy
just before "N97movie.mp4".

---

### Post by caco on 2009-12-11
That's nice ... I would remember that for my next projects. I guess file size here is not a threat to the N97

---

### Post by caco on 2009-12-11
Oh as for the syncs I use Nokia's ovi web/desktop app to sync my contacts

---

### Post by kapny on 2009-12-18
> **caco said:**
> Oh as for the syncs I use Nokia's ovi web/desktop app to sync my contacts
hello I`m at the moment waiting for my n97, what you mean with sync, actual bidireccional sync-ing? whith thunderbird, evolution?
and what about calendar?
thankyou everybody for this post, I`m sure it´s going to be very usuful to me once I receive my new phone.

---

### Post by caco on 2009-12-20
Bi-directional sync of contact I use the Nokia Ovi web. As an additional means for backup (bi-directional syncing) of contacts, music or others I use the Nokia Ovi desktop suite.

---

### Post by bertschollaert on 2009-12-21
hello,
Where can I find suggestions on how to sync my Nokia 6303c to Evolution? 

Neither of the suggestions on [https://help.ubuntu.com/community/NokiaEvolutionSyncing](https://help.ubuntu.com/community/NokiaEvolutionSyncing) contains my phone, also other suggestions on the forum didn't help so far. 

Thank you so much in advance for pointing me to the correct place to look.

ps: don't forget to also vote for a Linux ovi suite on [http://betalabs.nokia.com/forum/topic/3210](http://betalabs.nokia.com/forum/topic/3210)!

---

### Post by caco on 2009-12-22
Hello pal, you may have to do a little searching - I'm still working on mine when I have the time. Here a link which might help

[http://mobileyog.blogspot.com/2009/11/how-to-sync-contactscalendar-from.html]("http://mobileyog.blogspot.com/2009/11/how-to-sync-contactscalendar-from.html")

---

### Post by bertschollaert on 2009-12-22
Hey Caco,

Thanks so much for your swift reply! SyncEvolution looks very promising, but I don't understand how it can help to get my phone connected to my Ubuntu, can you explain that part? Where is your blog located or when will it be finished, you think?

Kind regards

---

### Post by audiomick on 2009-12-22
I think open sync is supposed to work between Evolution and most nokia phones. Having said that, mine isn't talking at the moment... :(

Be that as it may, here are some links.

[https://help.ubuntu.com/community/NokiaEvolutionSyncing/Opensync](https://help.ubuntu.com/community/NokiaEvolutionSyncing/Opensync)
[http://ubuntuforums.org/showthread.php?t=260676&highlight=E65](http://ubuntuforums.org/showthread.php?t=260676&highlight=E65)
[http://ubuntuforums.org/showthread.php?t=705103](http://ubuntuforums.org/showthread.php?t=705103)

---

### Post by bertschollaert on 2009-12-22
@ Caco: thanks a lot for your suggestion. I think I managed to sync my Nokia 6303c with Microsoft Exchange server, through Evolution and Ovi! 
@ Audiomick: thanks for your suggestion, but I already tried opensync, it didn't work for my situation (Exchange with Nokia 6303c).

---

### Post by kkfok1 on 2009-12-29
> **caco said:**
> Setting the N97 as a 3.5g modem for use with my Laptop was easy ... all I had to do was set the phone's usb connection mode to pc suite, then follow the follow the instructions that appear on the mobile broadband wizard that appears on your ubuntu's desktop.


Hi,

I am using hardy (8.04), but not able to connect my Nokia N97 to use as a 3g/3.5g modem. There is no mobile broadband wizard appear, is this only available in 9.04 ?

Thanks

---

### Post by caco on 2009-12-30
I plugged my N97 with a system running karmic, I'm not sure you would get the same result with hardy.
There were significant improvements in Karmic over Hardy, IMHO. Why not upgrade? Or you could hold on for a couple of months more for the next Ubuntu LTS.
:) A prosperous 2010 to all :P :)

---

### Post by HyRax on 2010-01-05
> **kkfok1 said:**
> Hi,

I am using hardy (8.04), but not able to connect my Nokia N97 to use as a 3g/3.5g modem. There is no mobile broadband wizard appear, is this only available in 9.04 ?

Thanks

You need to use Ubuntu 8.10 onwards for seamless mobile broadband, and the wizard is part of 9.04 onwards. Using 9.04 onwards will allow you to use your mobile phone as a broadband modem via Bluetooth too, once you update the Bluetooth stack. Prior to 9.04 you have to use a USB cable.

It's in your best interests to upgrade anyway, so get Ubuntu 9.10 on your machine!

I wrote a guide on how to _[hook up a Nokia N95 as a broadband modem](http://www.serenux.com/2009/08/howto-setup-your-nokia-n95-mobile-phone-as-a-mobile-broadband-device-via-bluetooth-in-ubuntu-jaunty/)_ some time ago, but the instruction equally applies to the N97 (remember to change all references of "Jaunty" to "Karmic" if you're using Ubuntu 9.10 instead of 9.04).

---

### Post by LuHe on 2010-01-07
Hello,

another application for Symbian S60-based mobile phones is [Series60-Remote]("http://series60-remote.sourceforge.net").

It offers an extensive message management (with a history browser, "chat"-function and statistics), contact management (add/edit/delete contacts) and a basic file management.

But I'm not 100% sure if it works with the N97 too - I got some reports that it works with some S60 5th Edition devices (like Nokia 5800 XpressMusic), but not with the N97 - but this should be fixed soon.

Feel free to contact me about any issues and general feedback.
Lukas

---

### Post by SagnaB on 2010-02-02
```
ffmpeg -i YourMovie.avi -b 2300k -r 30 -s 640x360 N97movie.mp4

```

Hi, i just tried this with a 140MB mpeg file, all the same except 'YourMovie.avi' is 'MyMovie.mpg' and it created an .mp4 with a size of 1.3GB. Is this normal?
Also the sync is out by nearly 2 seconds. Audio in front of video.

Is there a way to use this command to create lower file sizes, but retain quality of original file, and keep sync?

I am not familiar with ffmpeg at all nor linux for that matter.

Thanks guys. (and or girls lol)

---

### Post by caco on 2010-02-03
@SagnaB Sorry about the outcome of your conversion.
try ```
ffmpeg -i YourMovie.avi -b 2300k -r 30 -s 640x360 -acodec copy N97movie.mp4
```

If your feel up to it try ```
man ffmpeg
```

oh by the way I'm still learning like the rest of the world ... and if you don't know it, your education have already started:P.

Have a blessed day

---

### Post by pimparello on 2010-02-07
Hey there,

I may run the risk of being a bloody noob, but the N97 is the first smartphone I use and Ijust don't understand how to synch contacts or exchange pictures, etc. with Ubuntu. There is no windows-install on my computer.

I am using ubuntu 9.10, the blueetooth connection is set and running.

But what next? I just don't understand which prog I should use and how to do it. On my computer I am using evolution for contacts etc.

I appreciate every helping word!

Cheers.

---

### Post by Bharath on 2010-02-18
For Contacts transfer from Evo to Nokia S60 phones I found a easy way... posted here ->

[http://ubuntuforums.org/showthread.php?p=8844076#post8844076](http://ubuntuforums.org/showthread.php?p=8844076#post8844076)

Bharath

---

### Post by SagnaB on 2010-03-05
> **caco said:**
> @SagnaB Sorry about the outcome of your conversion.
try ```
ffmpeg -i YourMovie.avi -b 2300k -r 30 -s 640x360 -acodec copy N97movie.mp4
```If your feel up to it try ```
man ffmpeg
```oh by the way I'm still learning like the rest of the world ... and if you don't know it, your education have already started:P.

Have a blessed day

Hi, I found out the the original file was badly corrupted, it played back worse than the converted file! I have tried others since and all is good.

Bless you too

---

### Post by Andrea Tallo on 2010-03-06
Hi Caco,

I have a problem connecting my N97: the NetworkManager works perfectly, showing immediatly the device and setting everything in the right way. But when I try to connect to the brand new mobile network my phone start to quikly switch from the main page to the main menu, to the messages menu, to the phone book and then it shut down. Then Ubuntu automatically mount it as 32gb Mass Storage and the modem is no more detected (obviously! it is turned off!)...

How can I try to solve it?

---

### Post by caco on 2010-03-08
Kindly confirm if your N97 usb mode is in PC Suite, preferably set 'Ask on connection' to No.
If I may ask which firmware is your N97 using and which version of Ubuntu are you on

---

### Post by chriswyatt on 2010-05-22
Has anyone tried updating the firmware under Lucid?

Having an issue where it continuously goes round in a loop trying to install drivers for the MTP device.  Sometimes it does install successfully.  Also it installs generic Windows drivers for the MTP device but I noticed there are Nokia drivers, but these aren't detected as the correct drivers by Windows.

Managed to start the update process but when it reboots the phone it won't pick up the Nokia USB ROM device and also in the tooltip it says 'Not supported'.

Is this is due to the deprecation of usbfs in Lucid?

---

### Post by raonyguimaraes on 2011-03-22
I'm using Nokia PCSuite inside a virtualbox on Natty. 

[http://caciqueraony.blogspot.com/2011/03/como-instalar-nokia-pcsuite-usando.html](http://caciqueraony.blogspot.com/2011/03/como-instalar-nokia-pcsuite-usando.html)

---

