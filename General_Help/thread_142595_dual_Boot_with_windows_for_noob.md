---
title: "dual Boot with windows for noob"
date: 2006-03-10
forum: General Help
---

### Post by scotishhaggis on 2006-03-10
hey guys new to Ubuntu and linux in general used knbilunx for a about a year tho. av been look around for a while and every 1 keeps pointin to this distro and it looks good. Does Ubuntu auto install a boot loader in th MBR like GRUB to allow for dual boot with windows?

---

### Post by Zelut on 2006-03-10
Yes it does.  If you already have existing windows it'll ask if you want this listed as well, install grub & setup your dual-boot just like that.

---

### Post by scotishhaggis on 2006-03-10
cheers thx lets hope this goes well i tried fedora erlyer on today as my mate had it on cd. never worked at all and that was supose to install grub to.

---

### Post by Herman on 2006-03-10
Welcome, scotishhaggis, click on my left-hand sig link for a website showing you some example installs and some extra info on installing.
Good Luck with it. :D (Herman)

---

### Post by RJMacReady on 2006-03-10
Hello there scottishhaggis, it's great you've chosen the best Linux distro! 

Your best friend in these early days will be the [Unofficial Ubuntu Guide]("http://ubuntuguide.org/"). It tells you everything (well, almost everything) you need to know!

Good luck and have immense fun! :p

---

### Post by scotishhaggis on 2006-03-10
got it installed now looks great!!! just a few things i need to get installed 
1. sound card have no sound yet ? i have a soundblaster live 7.1 24bit edt
2. Grx driver? the rez on scree is making me blind . i have 19intft and rez will only go to 1204*768 need it bigger.
3. divx codec or xvid are ther any for ubutu

any help with that lot or should i post some where else

---

### Post by RJMacReady on 2006-03-10
To install the Linux DivX codec, type this into a terminal: ```
sudo apt-get install libdivx4linux
```

Not sure about the sound card issue, and I'm not sure if 7800's are supported by the open source nVidia drivers.

However, to *try* the nVidia drivers, you can follow [this]("http://ubuntuguide.org/#installnvidiadriver").

In a terminal, type **glxgears**. If it looks as slow as hell, you're not accelerated!

---

### Post by scotishhaggis on 2006-03-10
well is there any way to force the grapics drivers to go to 1280 * 1024

---

### Post by truoc444 on 2006-03-11
try to configure ALSA for sound.  i believe it's alsaconf or something like that it's been a while since i've done it, but it worked for me.  you can try to manually edit your Xorg.conf to add the desired resolution, just make sure your refresh rate is set right.

---

