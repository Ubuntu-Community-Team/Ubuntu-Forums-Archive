---
title: "microphone not reconized"
date: 2010-10-20
forum: General Help
---

### Post by Tinya_Fair on 2010-10-20
Hello, I have a toshiba a100 and i cannot get my mic to work. I have gone into gnome-alsamixer to find that capture was red. I place in these commands to see if a link to why my mic is not working could be found.

jurrietto@jurrietto-Satellite-A100:~$ uname -a
Linux jurrietto-Satellite-A100 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686 GNU/Linux
jurrietto@jurrietto-Satellite-A100:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861-VD Analog [ALC861-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
jurrietto@jurrietto-Satellite-A100:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
jurrietto@jurrietto-Satellite-A100:~$ head -n 1 /proc/asound/card*/codec#* 
==> /proc/asound/card0/codec#0 <==
Codec: LSI Si3054

==> /proc/asound/card0/codec#3 <==
Codec: Realtek ALC861-VD

The driver i use a a realtek, I need my mic working because i do schooling online and if i dont get my mic working then they will drop me from the course i am taking. I did try Mepis but because there are no more updates for it, i couldn't use pidgin ( yahoo) or even Gyachi. Please can someone help me, i dont want to waste $400 dollars for my course through school, it was a pain in the butt to get that money in the first place.

Oh yeah i also forgot i use Ubuntu 10.10 the new maverick Meerkat edition.

---

### Post by Shompol on 2010-10-20
Here's the fix that I used on my Sony Vaio, despite the fact that the fix was originally created for Toshiba :)

[http://translate.google.com/translate?hl=en&ie=UTF-8&sl=auto&tl=en&u=http://forum.ubuntu-it.org/index.php%3FPHPSESSID%3D051f54728935c3ae50e56d77ead8a4da%26/topic,337405.0.html&prev=_t&rurl=translate.google.com&twu=1](http://translate.google.com/translate?hl=en&ie=UTF-8&sl=auto&tl=en&u=http://forum.ubuntu-it.org/index.php%3FPHPSESSID%3D051f54728935c3ae50e56d77ead8a4da%26/topic,337405.0.html&prev=_t&rurl=translate.google.com&twu=1)


Try all three values of the "snd-hda-intel model" variable, one should definitely work. The funny part is that when I was fooling around with it, I could not get it to work, but a few days later mic started working, which means there is some extra magic involved (probably called "system restart")
 -Shompol

---

### Post by Tinya_Fair on 2010-10-21
When i did that, it turned off my sound completely.

---

### Post by Shompol on 2010-10-26
I suspect you changed output settings in alsamixer... At any rate, since you did not do anything drastic, like uninstalling packages, it should be trivial to revert it to the way it was before (a-la dead mic) -- just revert your changes to alsamixer and alsa-base.conf.

If you tried their suggested tweaks (and did not forget to reboot after each change) to no avail, there is another way!!! 

Buy a Logitech USB headset. Because USB does not plug into audio jack, it completely bypasses sound card with all the inherent problems.

I have one, but never tried that headset on Linux. If you are interested, I can bring it home and see if it's easy to get it to work.

---

### Post by Shompol on 2010-10-27
This is the lines I tried in alsa-base.conf and the last one worked for my sony vaio:

[COLOR=#000000][FONT=Arial]shompol@miao:~$ tail  /etc/modprobe.d/alsa-base.conf[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]#this was recommended to make mic work[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]#options snd-hda-intel model=toshiba-s06[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]#options snd-hda-intel model=toshiba-rx1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]options snd-hda-intel model=auto[/FONT][/COLOR]

I am sorry for pointing you to the wrong guide. It seems i merely used keywords from this guide to google the one that works. I recommend you try the above settings plus google for "snd-hda-intel toshiba" to find something relevant to your laptop.

---

