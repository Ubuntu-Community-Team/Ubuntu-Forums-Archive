---
title: "Can someone please tel me how to install my webcam and bluetooth?"
date: 2009-10-23
forum: General Help
---

### Post by Man-O-Leisure on 2009-10-23
Hi, i have read through other threats and am not able to get my webcam to function. Can someone please tell me how you do this in Linux? I am new to all this.

My equipment is:
Ubuntu:        9.04
Laptop:         Toshiba Tecra A9
Webcam:      Genius Look 320S
Dongle:         Dlink DBT-122 
Headset:       Plantronics 320

i ran that lsusb command and my webcam shows up as:

Bus 002 Device 003: ID 0458:7029 KYE Systems Corp. (Mouse Systems)

And bluetooth dongle shows as:

Bus 003 Device 002: ID 2001:f111 D-Link Corp. [hex] DBT-122 Bluetooth adapter

The dongle seems to install as the Bluetooth icon appears up the top bar near the time. I can also pair my headset with the bluetooth adapter, and it shows up in the bluetooth devices, i just cant see how to get it to work beyond that. So the problem is getting my Plantronics 320 to work... how do i do that? 

After searching a little i found that Cheese program, but it just doesnt find my cam at all..

I REALLY appreciate any help you all can offer..

---

### Post by P4man on 2009-10-23
Im not sure, but this link:
[http://cateee.net/lkddb/web-lkddb/USB_GSPCA_SN9C20X.html](http://cateee.net/lkddb/web-lkddb/USB_GSPCA_SN9C20X.html)

Seems to indicate your webcam is supported since kernel 2.6.31 .
Thats the kernel used by karmic (ubuntu 9.10) which due to be released next week (the release candidate is already available if you want to try)

As for bluetooth audio.. well, it aint that simple, in so far it works at all. Im not sure if its improved in Karmic, but you planned to use a bluetooth headset for skype, your in for a very rough ride.  have a glance here:

[https://help.ubuntu.com/community/BluetoothAudio](https://help.ubuntu.com/community/BluetoothAudio)

---

### Post by Man-O-Leisure on 2009-10-23
> **P4man said:**
> Im not sure, but this link:
[http://cateee.net/lkddb/web-lkddb/USB_GSPCA_SN9C20X.html](http://cateee.net/lkddb/web-lkddb/USB_GSPCA_SN9C20X.html)

Seems to indicate your webcam is supported since kernel 2.6.31 .
Thats the kernel used by karmic (ubuntu 9.10) which due to be released next week (the release candidate is already available if you want to try)

As for bluetooth audio.. well, it aint that simple, in so far it works at all. Im not sure if its improved in Karmic, but you planned to use a bluetooth headset for skype, your in for a very rough ride.  have a glance here:

[https://help.ubuntu.com/community/BluetoothAudio](https://help.ubuntu.com/community/BluetoothAudio)

Thanks for the fast reply!  Can i upgrade to that new kernal version ? I saw that the beta for Karmic was available, but was unsure about installing it..

Yeah, using the headset with Skype is the outcome i am after, i am back in Australia for 6 months now, girlfriend stillback in Brazil.. Would be good to get these 2 items working, i dont want to have to go back to Windows

---

### Post by P4man on 2009-10-23
> **Man-O-Leisure said:**
> Thanks for the fast reply!  Can i upgrade to that new kernal version ? I saw that the beta for Karmic was available, but was unsure about installing it..

Its possible to upgrade just the kernel, though it may or may not work with jaunty. I would not recommend it for a new user. Id try out Karmic RC. You can test it from the livecd and if it seems to work, may as well install it. Just keep in mind its not officially released yet and may have some rough edges around it (which will probably remain true for a few weeks after release as well). If you install the RC now, just doing all the updates you will end up with the release version. There is no need to download and install it again next week.

> 
Yeah, using the headset with Skype is the outcome i am after, i am back in Australia for 6 months now, girlfriend stillback in Brazil.. Would be good to get these 2 items working, i dont want to have to go back to Windows


Skype has recently released a new beta which supposedly fixes problems with bluetooth audio (its the version they propose currently on their download page). I havent tried it yet with BT, I did try the previous version 2 years ago and gave up.

 Still Id recommend you keep a a traditional headset at hand while you experiment with ubuntu in general and BT audio. I really cant promise you you'll get it working easily if at all, but Ill help where I can if you decide to try.

---

### Post by Man-O-Leisure on 2009-10-23
Thanks, I might upgrade to Karmic, and then see how it goes.  Might have to purchase a normal headset, but i will see how things go with the cam after the upgrade, and then come back here if i need more help with the Bluetooth.. Thanks so much for being so helpful, its great!

---

