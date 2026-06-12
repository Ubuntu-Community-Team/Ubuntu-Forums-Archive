---
title: "Ubtuntu 10.04: Grub Boot Question"
date: 2011-02-24
forum: General Help
---

### Post by SexySara on 2011-02-24
Okay, I installed 9.04 then upgraded all the way to 10.04 and I am sticking with this version now. I just tried updating the Legacy Grub to Grub 2. My version of Grub right now is  1.98. Somthing went wrong when I doing the "upgrade-from-grub-legacy" command and I got error 15 or something to that nature. I fixed that by booting in to my live 9.04 cd and long story short, I mounted the drive to replace the grub and all worked well. I am able to boot right back up now *wipes sweat off for-head*.... HUGE accomplishment for me and I feel like a real linux geek now hahaha. Anyway here is my question...

I again ran...

```
~$sudo upgrade-from-grub-legacy
```And I am prompted with this...

Package configuration
```


 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474; A new version of configuration file /etc/default/grub is available, but   &#9474; 
 &#9474; the version installed currently has been locally modified.                &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; What do you want to do about modified configuration file grub?            &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474;        install the package maintainer's version                           &#9474; 
 &#9474;        keep the local version currently installed                         &#9474; 
 &#9474;        show the differences between the versions                          &#9474; 
 &#9474;        show a side-by-side difference between the versions                &#9474; 
 &#9474;        show a 3-way difference between available versions                 &#9474; 
 &#9474;        do a 3-way merge between available versions (experimental)         &#9474; 
 &#9474;        start a new shell to examine the situation                         &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474;                                  <Ok>                                     &#9474; 
 &#9474;                                                                           &#9474; 
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 
                                                                               

```I have no clue what to choose. Last time I did this, it gave me an option between sda1 and sda2 if I remember correctly... or was it hda1 and 2?. I think that is where I messed up, I just pushed enter on sda1 and I don't think it loaded the grub right. Anyhow... what do I need to do from this window above? I am not gonna push anything that I don't know, in fear of having to mount the live CD and load Grub again and blah blah blah lol.

I been reading some guides from Google and followed one word from word and this is how I got into this mess the fist place. Maybe I did something wrong, I dunno.

The command I used from the live CD is listed below in case anyone else has that same problem. I don't remember my error code number, but this command fixed it.

```
sudo grub-install --root-directory=/mnt /dev/sda
```

**EDIT:** Just found out that "Grub 1.98 is grub 2. Grub 1 (legacy grub)  never got beyond about 0.97", thanks to Google and Hiippytaff. I  think I should leave the grub alone now lol.

---

### Post by Rubi1200 on 2011-02-24
Normally, when you see that window you would choose the option to > install the package maintainer's version 
Be aware, though, that if you made any changes to /etc/default/grub or used any custom configurations that they will need to be done again.

On the other hand, the option to > keep the local version currently installed                 will keep your custom GRUB settings but may not install all new features of the package.

I have not played around with the other options and cannot comment on what they may or may not do.

Hope this helps.

---

### Post by SexySara on 2011-02-24
Sure does help, thank you. So if I choose "install the package maintainer's version", would I get the default splash again and everything will boot normally? I messed with some settings for Splash and am trying to get the default splash up and going again.

I installed SimplyLine - Plymouth theme from Gnome-Look and am wanting the default splash back.

From ect/default/grub, can I delete what I bolded in the code and the system will just boot without splash? How would I get the default splash back from installing the SimplyLine - Plymouth one? Or maybe I should just install the Maintainer's Version for the default splash? I didn't do any mods so I wouldn't be missing anything at all.

```
RUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=**"quiet splash"**
GRUB_CMDLINE_LINUX=**" splash"**
```

---

### Post by dragon999 on 2011-02-24
If you want to play with you usplash screen here is 2 links on customizing your grub boot screen.

[http://ubuntuforums.org/showthread.php?t=1445724&highlight=usplash+screen](http://ubuntuforums.org/showthread.php?t=1445724&highlight=usplash+screen)  

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Hope this might help you out... Good luck.

---

### Post by SexySara on 2011-02-24
Thank you Dragon, thats just what I needed :D

---

