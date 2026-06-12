---
title: "Startup / Booting takes forever"
date: 2012-02-18
forum: General Help
---

### Post by tuX9th on 2012-02-18
Hi,
Recently my system takes forever to startup. It somehow freezes then waits for like 60 - 80s and then boots up the way it is supposed to
 I can't really find out what it is. I looked over my logs but I don't really know whats wrong.
So her are some logs.
dmesg (that's obviously the point where it freezes)
```

[    1.761760] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   69.954516] udevd[380]: starting version 173

```Full dmesg [http://paste.ubuntu.com/847202/](http://paste.ubuntu.com/847202/)

When i push ESC or F1 during startup I get to this screen, which is in no log (or I simply couldn't find it :P) so I had to screenshot it with my handycam
[http://sagdas.net/bilder/error.jpg](http://sagdas.net/bilder/error.jpg)

boot.log [http://paste.ubuntu.com/847205/](http://paste.ubuntu.com/847205/)
udev [http://paste.ubuntu.com/847211/](http://paste.ubuntu.com/847211/)

So if anyone has an idea whats wrong, please let me know.
If you need more information just post I'll provide it.
Dispite what's in my Profile Information I use **_Ubuntu 11.10._** I Somehow can't change my profile info. Dunno why, board doesn't let me :P

---

### Post by che47audio on 2012-04-19
Hi there,

I'm battling my way through the same problem. please check the thread below.
Also try unplugging the sata cable to your dvd/cd drive. for some reason this took about 25 secs off my boot time?

[http://ubuntuforums.org/showthread.php?t=1921305&highlight=che47audio]("http://ubuntuforums.org/showthread.php?t=1921305&highlight=che47audio")

Che

---

### Post by tuX9th on 2012-04-20
I resolved the problem by installing the backports udevd.
It's not really a fix but it worked.

greets

---

### Post by che47audio on 2012-04-20
How much did this alter your boot time by? Did it get rid of the mounting issue that was adding the best part of a minute?
How do I go about installing the backports udevd?

thanks

---

### Post by tuX9th on 2012-04-20
well it got back to normal.
reduced the period where it was waiting for something from over 1minute to nothing
open synaptics go to settings -> sources -> updates and check backports.
i'm using 11.10 so i have no idea what you are using and if it solves anything. I don't even know what the problem is you have

---

### Post by che47audio on 2012-04-21
I seem to have a similar problem to yourself, very slow boot time. I have managed to shave a few seconds of here and there but the boot is still way longer than it should be. I seem to be getting the same mounting issue that you had with your system- see below.

```
[    2.748041] usb 4-5: new full speed USB device number 2 using ohci_hcd
[    8.107824] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   22.660159] udevd[367]: starting version 173
[   22.690472] lp: driver loaded but no devices found

```

I have now checked the backports within the synaptic sources. Should I expect it to install or update something? because according to update manager there are no updates to install, after i have checked backports. 

Thanks
che

---

### Post by tuX9th on 2012-04-21
hm!
maybe the backports version from february is now the updates version. i have no idea...
maybe your issue solves itself when updating to 12.04

---

### Post by che47audio on 2012-05-15
Just as an update, I never got to the bottom of this issue. I gave in in the end and bought an ssd, which boots 12.04 in about 12 secs :)

edit- I must mention that removing my somewhat dated dvd drive cut the boot time by some 20 secs!! I bought a new dvd drive too.

---

