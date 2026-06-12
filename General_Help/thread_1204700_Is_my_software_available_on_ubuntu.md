---
title: "Is my software available on ubuntu?"
date: 2009-07-05
forum: General Help
---

### Post by mrabm on 2009-07-05
Greetings,

I am thinking about ditching Windows and everything Microsoft and moving to Linux.

I know most of my software is available to run on ubuntu as is and that other software that will fulfill the same role are available instead.

Specifically, I need to be able to synch my sony ericson phone with my Thunderbird contacts. Can anyone confirm the existance of such a software?

Separatelly I might need to use Adobe photoshop and illustrator are these compatible with ubuntu or could they run in emulation mode?

Thanks,

Michel

---

### Post by credobyte on 2009-07-05
None of Microsoft products are compatible with Linux ! Yes, you can run some of these applications trough Wine, however, using VirtualBox would be a lot easier.
Photoshop on Wine : [http://wiki.winehq.org/AdobePhotoshop](http://wiki.winehq.org/AdobePhotoshop)

---

### Post by mrabm on 2009-07-05
Thanks,

Michel

---

### Post by j7%&lt;RmUg on 2009-07-05
Hi there,
Ok first of all Adobe dont make linux versions of any of their software that i know of. So no you definitely cant run photoshop or illustrator in ubuntu natively, this link may be of assistance in getting them to run under wine: [http://wiki.winehq.org/AdobePhotoshop](http://wiki.winehq.org/AdobePhotoshop)

I dont know about syncing your phone with thunderbird but i daresay that its possible.

Hope this helps.

---

### Post by mrabm on 2009-07-05
Thanks, I will research the phone sync issue if I don't get a specific feedback here. Any recomendation on Thunderbird Lightning? I hear it has some problems with ubuntu?

---

### Post by derekeverett on 2009-07-05
My advice...

If your used to Windows don't completely ditch it. I personally don't think virtual machines are the cats *** either - but they work well for a lot of peoples needs.

If you rely heavily on software from adobe in particular I would stick to a dual boot if you only have the one machine. Linux doesn't have anything comparable in my opinion. 

I love Ubuntu don't get me wrong. I'm just being honest.

I am Ubuntu only at home now. And starting to regret it a little.

---

### Post by mrabm on 2009-07-05
OK! Sounds like your searching your soul. I can live with openorg, Thunderbird/lightning in sync with my Sony ericson plus a good image viewer. I have adobe running on a mac. Can I give the finger to Mr. Gates and not regret it?

---

### Post by derekeverett on 2009-07-05
lol you only live once man why not!

---

### Post by FrogPrince on 2009-07-05
I ditched Windows three years ago and have never, ever regretted it! Absolutely everything I do in Linux: from editing videos to touching photos - I do nothing in Windows. If you really want to go down that road, then forget using Windows software in Linux and use the Linux equivalents - they're mostly just as good, and some are even better. The Gimp replaces Photoshop totally adequately for most people, Amarok replaces itunes, K3b Nero etc.

---

### Post by hyperdude111 on 2009-07-05
MS office 2007 runs in wine.
Adobe DO make linux versions for most of their free software (flash, air, pdf) but not for their paid software. 

Virtualbox WILL be able to run all windows software because it is a virtual machine. You will be able to synch with that. This guide will help [http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml](http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml)

I would recommend you dual boot Win and buntu until you are sure of your decision.

---

### Post by mrabm on 2009-07-05
Thank you all:

1- where can I get a full list of alternate programs.
2- I can _**only**_ make the move if I can use Thunderbird/Lightning in sync with my Sony Erickson W902

That last point is vital and I have still no tangible answers in that regards,

Michel

---

### Post by credobyte on 2009-07-05
Boot from a LiveCD and test it ! Additionally, check this post : [http://ubuntuforums.org/showpost.php?p=7241687&postcount=3](http://ubuntuforums.org/showpost.php?p=7241687&postcount=3)

---

### Post by Crunchy the Headcrab on 2009-07-05
> **mrabm said:**
> Can I give the finger to Mr. Gates and not regret it?

My suggestion:  buy another hard drive and install ubuntu on that.  Yeah you can dual boot without 2 hard drives, but I don't like to do that.

Linux can be a pain to configure if you're not really tech savvy. It is unlikely to work flawlessly out of the box (it might work well ootb, but unlikely flawlessly).  This isn't because the OS is bad (it's actually better than windows), it is because your hardware providers probably don't support Linux because the desktop user base isn't very big.

Windows software is often superior in my opinion.  Yeah, you have to pay for some of it, but it's usually worth it in my opinion.  There is also a lot of GOOD freeware for Windows, so don't buy the Linux hype that all the good freeware is on Linux.  A lot of Linux software has been brought to windows anyway.

Now, Linux is extremely fun to use if you like command line interface, contributing to a community, and solving hardware issues.

Linux also is extremely customizable.  It's like a sandbox that you can mold however you want, but that process requires knowledge.

The OS itself is in many ways superior to Windows.  A lot of issues that you have with Windows you don't need to worry about with Linux.  For example, you are unlikely to get dangerous viruses, it is unnecessary to defrag hard disk, the OS has the ability to natively burn iso images, and depending on the distro you use it can be a lot lighter/faster than Windows (although I find Vista incredibly fast anyway on my pc).

Codecs that come packaged with Windows (because you pay for them) are not available out of the box in Ubuntu.  Things like mp3 playback, mpeg video, wma/wmv, dvd (video) etc are not usable unless you buy the codecs legally or download them from the Ubuntu repositories which can be illegal depending on where you live (because these formats are protected by patents, etc).

[COLOR=Red]If you prefer graphics, games, and professional/trade software stick with Windows.  If you are having a lot of problems with Windows - it isn't working, it's slow, you just want something free, or you want to expand your horizons try Ubuntu.
[/COLOR]

---

### Post by Bigtime_Scrub on 2009-07-05
> **mrabm said:**
> Thank you all:

1- where can I get a full list of alternate programs.
2- I can _**only**_ make the move if I can use Thunderbird/Lightning in sync with my Sony Erickson W902

That last point is vital and I have still no tangible answers in that regards,

Michel


I doubt this is a full list, and no where near comprehensive, because well... there are over 20,000 programs just in Debian alone and God knows how many in Windows. It is a good start though. 
[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)

As far as your phone goes where there is a will there is a way. I have a Blackjack II that sinks well in Linux and I can even tether the 3G network and use it as a modem in a pinch! You should try to install the syncing software that came with your phone in Wine. You might be surprised.

No one can can say 100% positive you will have all the functionality of your phone's syncing options.

---

### Post by Bigtime_Scrub on 2009-07-05
> **Crunchy the Headcrab said:**
> 
Linux can be a pain to configure if you're not really tech savvy. It is unlikely to work flawlessly out of the box (it might work well ootb, but unlikely flawlessly).  This isn't because the OS is bad (it's actually better than windows), it is because your hardware providers probably don't support Linux because the desktop user base isn't very big.

Windows software is often superior in my opinion.  Yeah, you have to pay for some of it, but it's usually worth it in my opinion.  There is also a lot of GOOD freeware for Windows, so don't buy the Linux hype that all the good freeware is on Linux.  A lot of Linux software has been brought to windows anyway.


This is not really true. Try using Kismet in Windows. Have fun with that. 
Also, Linux is easy to configure, as long as you realize you arent configuring windows and you are configuring Linux.

---

### Post by mrabm on 2009-07-05
Thank you all for your opinions and helpful links. I need to figure out how to sync my phone before I take any decisions. Funny though that such an important feature that requires such limited resources has not yet been tackled by the Linux community!

Michel

---

### Post by 3rdalbum on 2009-07-05
> **mrabm said:**
> I need to figure out how to sync my phone before I take any decisions. Funny though that such an important feature that requires such limited resources has not yet been tackled by the Linux community!

Michel

1. It might not require "limited resources" if the phone's internal storage format is proprietary or encrypted.

2. You did have a suggestion: Boot up the Ubuntu live CD, connect to the Internet, use Add/Remove Applications to download Thunderbird, and try syncing your phone in the live CD environment. If it works, then you've got a green-light for installing Ubuntu for real.

---

### Post by mrabm on 2009-07-05
I am now using a freeware "My Phone Explorer" to sync my phone with Thunderbird on vista so I concluded it must be relatively simple.

---

