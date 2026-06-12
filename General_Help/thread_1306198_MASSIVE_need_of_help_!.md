---
title: "MASSIVE need of help !"
date: 2009-10-30
forum: General Help
---

### Post by Turk4n on 2009-10-30
So, basically. I have wanted to install Ubuntu 9.10 since the promise of better support and etc.
Indeed ubuntu 9.10 is a quite leap ahead.Installing worked flawless however somethings are wrong and seems to not work !

#1. I can't hear anything from my laptop speakers and audio jackets.
#2. The restricted drivers for ATI cards messes up totally !
I can't see anything,just constantly flashes...like **** and GDM won't start...
#3. My wireless connection sucks !
I can't be connected for more than 5 min then I lose contact and have trouble auto connect or reconnect again.

What to do?
As in win7 everything above works flawless, and I want that at least equally for Ubuntu. 

Specs and laptop brand.

HP Pavilion dv6 1110eo
AMD Turion™ X2 Dual-Core Mobile-processor RM-74 2,2 GHz
4096 MB (2 x 2048 MB)
500 GB SATA-harddrive 5400 rpm
Lightscribe Super Multi DVD-burner(+/-R +/-RW)
Integrated 10/100/1000 Gigabit Ethernet LAN - Realtek GBE Family controller
802,11a/b/g/n WLAN - Atheros ar928x/AR5009
WirelessBluetooth® - network connection - HP WBT
ATI Mobility Radeon HD 4650
Up till 2303 MB graphic memory totally with 1024 dedicated MB
16-bits Sound Blaster Pro-compatible sound.
(in ubuntu)
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #

Hope this will help !

P.S - I had sound in 9.04 after some tricks, now they don't work but no go with video drivers.

---

### Post by prem1er on 2009-10-30
For your wireless connection issue...

1. Are you using a restricted driver to get it to work?
2. Are you using the default Network Manager or WICD?

---

### Post by Turk4n on 2009-10-30
> **prem1er said:**
> For your wireless connection issue...

1. Are you using a restricted driver to get it to work?
2. Are you using the default Network Manager or WICD?

Nope, no restricted drivers to my wireless. Using the default network manager.

---

### Post by prem1er on 2009-10-30
I have the same wifi card as you in my ASUS. I also have problems with connection in 9.10, but it is much better than it was in 9.04. Do you lose connection when downloading larger files, or just randomly? I have had much better luck removing the Network Manager and installing WICD. It just seems to work better. Here is a good tutorial.

[http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html](http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html)

edit: make sure your wired connection works before you uninstall the network manager!

---

### Post by Turk4n on 2009-10-30
> **prem1er said:**
> I have the same wifi card as you in my ASUS. I also have problems with connection in 9.10, but it is much better than it was in 9.04. Do you lose connection when downloading larger files, or just randomly? I have had much better luck removing the Network Manager and installing WICD. It just seems to work better. Here is a good tutorial.

[http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html](http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html)

Yeah !
I have the same problem !
While downloading things it just drops !

---

### Post by prem1er on 2009-10-30
Yes, it is most likely a driver issue deeper than the network manager, but for some reason WICD works better with it. I would try that solution.

---

### Post by Turk4n on 2009-10-30
> **prem1er said:**
> Yes, it is most likely a driver issue deeper than the network manager, but for some reason WICD works better with it. I would try that solution.

So, I will have a "living" network connection or will it drop to sometime?

---

### Post by Giblet5 on 2009-10-30
> What to do?
As in win7 everything above works flawless, and I want that at least equally for Ubuntu.

It won't happen until the hardware vendors start providing similar tools for Linux as they do for Windows.

The best thing you can do is contact HP and ask them why they don't provide a set of easily installed Linux support options for their laptops.

The squeaky wheel strategy works well with HP, Dell, and IBM (Lenovo).

This is the second-to-last hurdle for Ubuntu. The last is to get game vendors to write for native Linux.

--------------

As for sound, [this]("http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html#more-1301") has helped other Pavilion DV6 users.

I can't help with the ATI issue, except to suggest that switching to the text console via CtrlAltF1, logging in, then moving any xorg.conf out of the way, might help a little: ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo /etc/init.d/gdm restart
```

The WiFi issue may be due to network-manager. I prefer WiCD on my laptops. It has a much better interface and it just works.

```
sudo apt-get install wicd
sudo apt-get remove network-manager --purge
```

Remove the nm-applet network noodle (what IS that icon???) from the panel and start WiCD via the Applications -> Internet menu icon.

---

### Post by P4man on 2009-10-30
As for your sound try editing /etc/modprobe.d/alsa-base.conf 

add or modify this line:
```
options snd-hda-intel index=0 model=hp-dv5 enable_msi=1
```
(make a backup first)
Inspired by:
[http://article.gmane.org/gmane.linux.alsa.devel/66781](http://article.gmane.org/gmane.linux.alsa.devel/66781)

---

### Post by Turk4n on 2009-10-30
> **Giblet5 said:**
> It won't happen until the hardware vendors start providing similar tools for Linux as they do for Windows.

The best thing you can do is contact HP and ask them why they don't provide a set of easily installed Linux support options for their laptops.

The squeaky wheel strategy works well with HP, Dell, and IBM (Lenovo).

This is the second-to-last hurdle for Ubuntu. The last is to get game vendors to write for native Linux.

--------------

As for sound, [this]("http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html#more-1301") has helped other Pavilion DV6 users.

I can't help with the ATI issue, except to suggest that switching to the text console via CtrlAltF1, logging in, then moving any xorg.conf out of the way, might help a little: ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo /etc/init.d/gdm restart
```

The WiFi issue may be due to network-manager. I prefer WiCD on my laptops. It has a much better interface and it just works.

```
sudo apt-get install wicd
sudo apt-get remove network-manager --purge
```

Remove the nm-applet network noodle (what IS that icon???) from the panel and start WiCD via the Applications -> Internet menu icon.

Sadly, I doubt they will even bother giving out proper drivers for GNU/Linux; however I did the xorg.conf, didn't work... so next step will be reinstalling the whole thing then step by step do this :)
Also... I have tried out that sound trick you posted about, didn't work for my laptop.
I have posted a solution that works under 9.04. However seem to not work properly in 9.10.

---

### Post by danastasio on 2009-10-30
I've got an HP dv6700t, so i know your sound worries well. i havent found a solution for the issue, but if you run
```
sudo alsa force-reload
```
after your computer starts, you'll have sound for that session.
i'll post back if i find any good solutions.

---

### Post by Turk4n on 2009-10-30
> **P4man said:**
> As for your sound try editing /etc/modprobe.d/alsa-base.conf 

add or modify this line:
```
options snd-hda-intel index=0 model=hp-dv5 enable_msi=1
```
(make a backup first)
Inspired by:
[http://article.gmane.org/gmane.linux.alsa.devel/66781](http://article.gmane.org/gmane.linux.alsa.devel/66781)

Tried that, got messed sound errors...
I got both sound from front and headphones. Which resulted to give me a horrible scratch sound from time to time...
Thanks anyways !

---

### Post by Turk4n on 2009-10-30
I will try that mate !
Did this for my 9.04 experience, however it backfires at 9.10 :(
[http://ubuntuforums.org/showpost.php?p=7790194&postcount=64](http://ubuntuforums.org/showpost.php?p=7790194&postcount=64)

---

### Post by Turk4n on 2009-10-30
Okay, re-installed and everything set....
However still no sound, wireless works, doesn't drop which is kinda cool, also like the interface now :)
So wondering...
Why doesn't my keys save, I mean password for network and when authentication once... do I have to do it twice, since I didn't have to do this kind of thing before...
Plus installed drivers from ATI, everything went flawless, rebooted. Wow, everything just flew and etc. BUT, why did ubuntu go back?????????????????????
I don't get it. It reverted and became shitty again, flickering over 9000. I just couldn't bear it...Why these problems?

---

### Post by danastasio on 2009-10-31
Hiya everyone!
I said that i would post back here if i found a solution for my sound issues and i did!! If you installed the "software modem" proprietary driver, remove it! apparently it has a nasty bug that makes your computer all unhappy and unable to play sound. But removing solves the problem 

though on start i noticed that the volume was automatically muted, so to solve this install aumix
```
sudo apt-get install aumix
```
and add the following to your startup scripts
```
aumix -v 50
```
this will set the main volume on your computer to 50%

> **Turk4n said:**
> Okay, re-installed and everything set....
However still no sound, wireless works, doesn't drop which is kinda cool, also like the interface now :)
So wondering...
Why doesn't my keys save, I mean password for network and when authentication once... do I have to do it twice, since I didn't have to do this kind of thing before...
Plus installed drivers from ATI, everything went flawless, rebooted. Wow, everything just flew and etc. BUT, why did ubuntu go back?????????????????????
I don't get it. It reverted and became shitty again, flickering over 9000. I just couldn't bear it...Why these problems?

I'm really not sure why your keys are not saving, I can't convince my parents to use network encryption so I dont really have any experiance in that field. I'll keep an eye out for you on the forums though.

What do you mean that "Ubuntu went back" I'm not really sure what your trying to say here.
"It reverted", what did, your system? so it went from awful to awesome and back to awful?

---

### Post by Turk4n on 2009-10-31
> **danastasio said:**
> Hiya everyone!
I said that i would post back here if i found a solution for my sound issues and i did!! If you installed the "software modem" proprietary driver, remove it! apparently it has a nasty bug that makes your computer all unhappy and unable to play sound. But removing solves the problem 

though on start i noticed that the volume was automatically muted, so to solve this install aumix
```
sudo apt-get install aumix
```
and add the following to your startup scripts
```
aumix -v 50
```
this will set the main volume on your computer to 50%

I'm really not sure why your keys are not saving, I can't convince my parents to use network encryption so I dont really have any experiance in that field. I'll keep an eye out for you on the forums though.

What do you mean that "Ubuntu went back" I'm not really sure what your trying to say here.
"It reverted", what did, your system? so it went from awful to awesome and back to awful?

Oh I meant, that after installing ATIs driver and rebooted I could see videos, use compiz flawless and play simple 3d games at max...meaning the drivers were ok. However restarting again, and booting up normally made it go back thinking drivers gone !
I just didn't get it !
As for keys, whenever I connect to an encrypted network, it will ask for password, BUT. Now it will not save it, for future use. Meaning I have to log in 9000 times, which sucks !

---

### Post by misfitpierce on 2009-10-31
Also so you know... a lot of cards were dropped off the prop drivers support from ATI and you must use opensource drivers for a lot of ATI cards now that arent the newer cards. ATI 200m and such are amongst the list along with many others. Just as a note...

---

### Post by Turk4n on 2009-10-31
> **misfitpierce said:**
> Also so you know... a lot of cards were dropped off the prop drivers support from ATI and you must use opensource drivers for a lot of ATI cards now that arent the newer cards. ATI 200m and such are amongst the list along with many others. Just as a note...

I have a quite new one...I think at least.
ATI Mobility Radeon HD 4650

---

