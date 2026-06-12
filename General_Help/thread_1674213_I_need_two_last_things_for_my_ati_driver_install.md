---
title: "I need two last things for my ati driver install"
date: 2011-01-23
forum: General Help
---

### Post by u-noob-tu on 2011-01-23
After an unbelievably long Process of trial and error, I think I have finally discovered what was making the driver not work. If I am correct, the driver had unmet dependencies and it just didn't tell me. I found the amd release notes and it listed things that must be installed. I got everything except xfree86-Mesa-libgl and xfree86-libs. I have no idea if I have them already or where to get them if I don't have them. Anybody wanna help?

---

### Post by Sylos on 2011-01-23
Hello there.
I dont have an ati card so Im just going on what I have read.
It seems you shouldnt need these packages if you install the driver package from synaptic.

Have a look here:

[http://ubuntuforums.org/archive/index.php/t-1475009.html](http://ubuntuforums.org/archive/index.php/t-1475009.html)

I apologise now if you have seen this all before.
And so far I havent found those packages....

---

### Post by u-noob-tu on 2011-01-23
> **Sylos said:**
> Hello there.
I dont have an ati card so Im just going on what I have read.
It seems you shouldnt need these packages if you install the driver package from synaptic.

Have a look here:

[http://ubuntuforums.org/archive/index.php/t-1475009.html](http://ubuntuforums.org/archive/index.php/t-1475009.html)

I apologise now if you have seen this all before.
And so far I havent found those packages....

wow, thanks for the quick reply. yeah, i have seen that thread. i tried installing through synaptic and when i rebooted everything was slow and aticonfig still couldnt find the fglrx driver (even though i had installed it and catalyst control center, it still said "no supported adapters detected). im pretty sure it has something to do the mesa driver and xfree86 libs. although i cant recall seeing either of those mentioned in any tutorials i have read.

---

### Post by tcrapper on 2011-01-23
You can try manually installing the ATI driver, instructions below. Instructions are from [here]("http://vanvalkinburgh.org/blog/3036").

Since you have an ATI 3650, you have to use 10.10, 10.8 or 10.4.

First you should remove the old driver and reboot.


```
sudo apt-get remove fglrx fglrx-amdcccle
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo rm -fr /usr/lib/fglrx
sudo rm -fr /etc/ati
sudo reboot
```

If you don&#8217;t have any ATI driver installed then skip the above.

Type ctrl alt f1, then do the below after you login. The driver version is after v.

```
wget http://kanotix.com/files/install-fglrx-debian.sh
chmod 755 install-fglrx-debian.sh
sudo ./install-fglrx-debian.sh -zv 10.10
sudo aticonfig -f --initial
sudo reboot
```

---

### Post by Sylos on 2011-01-23
Hmmmmm.....very irritating.

I have been looking around for the packages mentioned but cant seem to find them.

I think you may have a bigger issue though - Xorg is the default Ubuntu choice - if you want to use the Xfree86 packages I assume you need to install the whole Xfree86 system and remove xorg to prevent conflict. 

Have you already looked into this?

---

### Post by cottfcfan on 2011-01-23
This is the easiest walkthrough I have found for installing the ATI Driver.
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Download_the_latest_Catalyst_package](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Download_the_latest_Catalyst_package).
All the dependencies can be installed in one command.

---

### Post by u-noob-tu on 2011-01-23
> **tcrapper said:**
> You can try manually installing the ATI driver, instructions below. Instructions are from [here]("http://vanvalkinburgh.org/blog/3036").

Since you have an ATI 3650, you have to use 10.10, 10.8 or 10.4.

First you should remove the old driver and reboot.


```
sudo apt-get remove fglrx fglrx-amdcccle
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo rm -fr /usr/lib/fglrx
sudo rm -fr /etc/ati
sudo reboot
```

If you don’t have any ATI driver installed then skip the above.

Type ctrl alt f1, then do the below after you login. The driver version is after v.

```
wget http://kanotix.com/files/install-fglrx-debian.sh
chmod 755 install-fglrx-debian.sh
sudo ./install-fglrx-debian.sh -zv 10.10
sudo aticonfig -f --initial
sudo reboot
```

how would i do that but instead of using the driver listed here i would use the latest which is 10.12?

---

### Post by u-noob-tu on 2011-01-23
> **cottfcfan said:**
> This is the easiest walkthrough I have found for installing the ATI Driver.
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Download_the_latest_Catalyst_package](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Download_the_latest_Catalyst_package).
All the dependencies can be installed in one command.

i tried that tutorial twice and it always gets stuck at ati config. says no supported drivers detected every time.

---

### Post by tcrapper on 2011-01-23
run sudo ./install-fglrx-debian.sh -zv 10.10 without the v 10.10 part. or the below.

```
sudo ./install-fglrx-debian.sh -zv 10.12
```

---

### Post by tcrapper on 2011-01-23
> **u-noob-tu said:**
> i tried that tutorial twice and it always gets stuck at ati config. says no supported drivers detected every time.

Your other post says your using a ATI Radeon Mobility 3650 265mb, and if you go to AMD's site, and select 3600 series it doesn't list 10.12 as supported, the latest version is 10.10 for that card.

[http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.1&product=2.4.1.3.14&contentType=GPU+Download+Detail&ostype=Linux+x86&keywords=&items=20](http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.1&product=2.4.1.3.14&contentType=GPU+Download+Detail&ostype=Linux+x86&keywords=&items=20)

---

### Post by cottfcfan on 2011-01-23
> **u-noob-tu said:**
> i tried that tutorial twice and it always gets stuck at ati config. says no supported drivers detected every time.

Thats because you probably need to replace catalyst 10.12 with 10.10, as thats the last supported driver for your card.

---

### Post by u-noob-tu on 2011-01-23
> **tcrapper said:**
> run sudo ./install-fglrx-debian.sh -zv 10.10 without the v 10.10 part. or the below.

```
sudo ./install-fglrx-debian.sh -zv 10.12
```

this might be a stupid question, but i actually need to have the 10.12.run file for this command to work right? i have it, i just want to make sure.

---

### Post by tcrapper on 2011-01-23
That script will download it for you. And their site doesn't list the 10.12 driver for newer cards either, so I'm not sure if your card is supported in the latest driver or not.

---

### Post by u-noob-tu on 2011-01-23
> **cottfcfan said:**
> Thats because you probably need to replace catalyst 10.12 with 10.10, as thats the last supported driver for your card.

im not sure what you mean. i copy/pasted the commands from the tutorial and they all have 10-12 in the command. what do you mean last supported driver? i went to amd.com and 10.12 was the driver that i was told to use. i even double checked at dell (my laptop is a dell studio 17) and it had the same driver listed.

---

### Post by tcrapper on 2011-01-23
> **u-noob-tu said:**
> im not sure what you mean. i copy/pasted the commands from the tutorial and they all have 10-12 in the command. what do you mean last supported driver? i went to amd.com and 10.12 was the driver that i was told to use. i even double checked at dell (my laptop is a dell studio 17) and it had the same driver listed.

Your probably right then. Not sure why their site doesn't list 10.12 for me.

---

### Post by u-noob-tu on 2011-01-23
> **tcrapper said:**
> That script will download it for you. And their site doesn't list the 10.12 driver for newer cards either, so I'm not sure if your card is supported in the latest driver or not.

i went and triple checked and youre right. i dont know why i was given 10.12 so many times. that makes no sense.

---

### Post by u-noob-tu on 2011-01-23
> **cottfcfan said:**
> This is the easiest walkthrough I have found for installing the ATI Driver.
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Download_the_latest_Catalyst_package](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Download_the_latest_Catalyst_package).
All the dependencies can be installed in one command.

im going to try this one more time, seeing as i was given the wrong driver. fingers crossed.

---

### Post by cottfcfan on 2011-01-23
If your Card is a ati3650 (ref post 4) then I think you need to use the 10.10 driver. use the same commands as in my 1st post but replace 10.12 with 10.10, and see if that works.

---

### Post by u-noob-tu on 2011-01-23
> **cottfcfan said:**
> If your Card is a ati3650 (ref post 4) then I think you need to use the 10.10 driver. use the same commands as in my 1st post but replace 10.12 with 10.10, and see if that works.

i am still getting the no supported adapters error. i just dont get it...

---

### Post by cottfcfan on 2011-01-23
What exactly is yours graphics card id?

---

### Post by u-noob-tu on 2011-01-23
> **cottfcfan said:**
> What exactly is yours graphics card id?

this is what dell says it is:

256MB ATI®  Mobility Radeon HD 3650

i havent been able to find that through settings or using the terminal.

---

### Post by cottfcfan on 2011-01-23
OK. Download the 10.10 driver to your desktop from here:
[http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.1&product=2.4.1.3.14&contentType=GPU+Download+Detail&ostype=Linux+x86&keywords=&items=20](http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.1&product=2.4.1.3.14&contentType=GPU+Download+Detail&ostype=Linux+x86&keywords=&items=20)
Then:
```
cd Desktop
```
```
cd catalyst*
```
```
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0
```
```
sudo apt-get remove --purge xserver-xorg-video-radeon
```
```
sh ati-driver-installer-10-10-x86.x86_64.run --buildpkg Ubuntu/maverick
```
```
sudo dpkg -i fglrx*.deb
```
```
sudo aticonfig --initial -f
```
That should do it.
Just make sure you have the Medibuntu repo enabled in case some of the dependencies come from there.

---

### Post by u-noob-tu on 2011-01-23
> **cottfcfan said:**
> OK. Download the 10.10 driver to your desktop from here:
[http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.1&product=2.4.1.3.14&contentType=GPU+Download+Detail&ostype=Linux+x86&keywords=&items=20](http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.1&product=2.4.1.3.14&contentType=GPU+Download+Detail&ostype=Linux+x86&keywords=&items=20)
Then:
```
cd Desktop
```
```
cd catalyst*
```
```
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0
```
```
sudo apt-get remove --purge xserver-xorg-video-radeon
```
```
sh ati-driver-installer-10-10-x86.x86_64.run --buildpkg Ubuntu/maverick
```
```
sudo dpkg -i fglrx*.deb
```
```
sudo aticonfig --initial -f
```
That should do it.
Just make sure you have the Medibuntu repo enabled in case some of the dependencies come from there.

so wait, i understand cd desktop, but what about cd catalyst? are you referring to the folder that was made when i used that tutorial? should i clear it out then?

---

### Post by u-noob-tu on 2011-01-23
AAAAAAAAAAAAAAAAAAAAARRRRRRGHHHHHH!!!!!!!!! NO SUPPORTED ADAPTERS DETECTED AGAIN!!!!! what is going wrong???????? :confused::confused::frown::frown::frown::x

---

### Post by u-noob-tu on 2011-01-23
im just thinking out loud, but do you think that i could get a slightly older driver to work? maybe the 10.10 is just "too new" for my card?

EDIT i just checked the release notes at amd for the 10.10 driver and the 10.8 driver, and they both say my card is compatible.

---

### Post by cottfcfan on 2011-01-23
Sorry i'm out of ideas.
Maybe someone else can help.

---

### Post by Timmer1240 on 2011-01-23
This has been a real battle hang in there!maybe try the older drivers maybe the legacy driver will work 9.3

---

