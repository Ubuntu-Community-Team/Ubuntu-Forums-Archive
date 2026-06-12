---
title: "Windows Advanced Options Menu"
date: 2010-11-12
forum: General Help
---

### Post by COKEDUDE on 2010-11-12
I dual boot between Windows XP and Linux Mint. I am trying to get the **Windows Advanced Options Menu** to show up. Normally you would press f8 to make this happen when your computer is booting. With a dual boot it makes it way more complicated. If you press f8 when your computer first starts it does nothing. Next the grub menu pops up and I select XP. After that it is to late and you can't get to your Windows Advanced Options Menu.

[IMG]http://i255.photobucket.com/albums/hh133/COKEDUDEUSF/Windows_Advanced_Options_menu.png[/IMG]

[http://i255.photobucket.com/albums/hh133/COKEDUDEUSF/Windows_Advanced_Options_menu.png](http://i255.photobucket.com/albums/hh133/COKEDUDEUSF/Windows_Advanced_Options_menu.png)

---

### Post by scouser73 on 2010-11-12
You should ask in the [[COLOR="Red"]**Linux Mint Forum**[/COLOR]]("http://forums.linuxmint.com/").

---

### Post by pricetech on 2010-11-12
With XP running, open msconfig.  On the boot.ini tab check the box for safeboot.  That should get you into safe mode.

Is that what you're after ??

---

### Post by COKEDUDE on 2010-11-12
> **pricetech said:**
> With XP running, open msconfig.  On the boot.ini tab check the box for safeboot.  That should get you into safe mode.

Is that what you're after ??

No actually I wanted to restore my last known good configuration.

---

### Post by coffeecat on 2010-11-12
I guess the trick would be to get grub to delay after you select the Windows option to give you enough time to press F8. I've looked in the command list in [the grub 2 manual]("http://www.gnu.org/software/grub/manual/grub.html") and the only one that seems to come close is the 'play' command, to play a tune from a file. Having a bootloader play a tune - they've thought of everything! :?

Anyway, I guess you would have to put this between the search and chainloader commands in the Windows stanza of your grub.cfg, but how you do this without directly editing grub.cfg and make it stick, I don't know offhand. And it's too late here for me to be able to think about it coherently.

---

### Post by pricetech on 2010-11-15
> **COKEDUDE said:**
> No actually I wanted to restore my last known good configuration.

I see.  Last Known Good .... rarely works since windows has a nasty habit of overwriting it with a failed boot even though it's not supposed to.

I take it you've already tried being very fast with tapping F8.

---

### Post by COKEDUDE on 2010-11-16
> **pricetech said:**
> I see.  Last Known Good .... rarely works since windows has a nasty habit of overwriting it with a failed boot even though it's not supposed to.

I take it you've already tried being very fast with tapping F8.

Yes :). I wish it was that simple.

---

### Post by yetiman64 on 2010-11-16
Hi COKEDUDE, when you have the grub menu up and Windows highlighted have a finger on the F8 button and ready to tap continually _*as soon as you press the enter button*_ for the Windows entry.

I have actually been able to bring this menu up immediately after the grub menu doing it this way with Ubuntu and it should also work with Mint. But you do have to be very quick and often it takes a few goes to get the timing down, don't stop tapping until you get the F8 screen up or if you miss and get the Windows loading bar. Good luck.

---

### Post by stinkeye on 2010-11-16
From Ubuntu mount your XP partition and edit the boot.ini file.
Make a copy first.
If you duplicate your XP boot line you will be shown an OS chooser
screen with a timeout.
Does no harm, just pretends there is another Windows install. 
Pressing F8 here will take you to recovery options.

You may have to add a line.
```
timeout=15
```


eg my boot.ini
```
[boot loader]
redirect=usebiossettings
redirectbaudrate=
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="XP" /noexecute=optin /fastdetect /usepmtimer
[COLOR="Magenta"]multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="XP" /noexecute=optin /fastdetect /usepmtimer[/COLOR]
```
[COLOR="#ff00ff"]Copy of first line[/COLOR]

---

### Post by COKEDUDE on 2010-12-11
Changing my timeout did the trick for. It was just 1 second before. Now I have way more time which makes it way easier to hit f8 fast enough. 

```
timeout=15
```

```
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

---

