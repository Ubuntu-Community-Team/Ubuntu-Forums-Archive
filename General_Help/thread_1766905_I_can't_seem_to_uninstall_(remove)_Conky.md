---
title: "I can't seem to uninstall (remove) Conky"
date: 2011-05-25
forum: General Help
---

### Post by airspoon on 2011-05-25
First I'd like to mention that I'm brand-new to Ubuntu, having just recently installed 11.04. Well, earlier today I installed 'conky-all' and now I can't seem to remove it. To install it, I used:
```
sudo apt-get install conky-all
```

I then used a conkyrc that I found on an internet tutorial. It seemed to run okay but it was very ugly so I tweaked a few variables. However, after doing so, I couldn't get conky to work again. So, just to see if it was the variables that I set which could have broke it, I changed the conkyrc file back to that ugly one which worked before. I then tried to run conky again and this time it didn't work either. 

I then decided to remove conky in an effort to reinstall the conky, this time just conky as opposed to conky-all. I used:
```
sudo apt-get remove conky-all
```

Thinking that I had successfully removed conky, I did another apt-get to install conky. When I couldn;t get that one to work, I tried to remove it. However, this time I decided to check and see if it was actually removed, by using:
```
conky -v
```

Apparently I wasn't able to remove conky because the terminal kicked back:
```

dell:~$ conky -v
Conky 1.8.0 compiled Fri Apr 23 10:38:37 UTC 2010 for Linux 2.6.24-27-server (i686)

Compiled in features:

System config file: /etc/conky/conky.conf
Package library path: /usr/lib/conky

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft
  * ARGB visual

 Music detection:
  * MPD
  * MOC

 General:
  * math
  * hddtemp
  * portmon
  * Curl
  * RSS
  * Weather (METAR)
  * Weather (XOAP)
  * wireless
  * support for IBM/Lenovo notebooks
  * nvidia
  * eve-online
  * config-output
  * Imlib2
  * ALSA mixer support
  * apcupsd
  * iostats
  * ncurses
  * Lua

  Lua bindings:
   * Cairo
   * Imlib2

```

Can anyone enlighten me as to what is going on and how I might troubleshoot this by either removing the conky package all together or finding out what went wrong so that I can try and fix it?

Any and all help would be greatly appreciated. Thanks.

---

### Post by linuxinstalledfromhdd on 2011-05-25
After you uninstalled it did you clear out the configuration settings?

---

### Post by wildmanne39 on 2011-05-25
> **airspoon said:**
> First I'd like to mention that I'm brand-new to Ubuntu, having just recently installed 11.04. Well, earlier today I installed 'conky-all' and now I can't seem to remove it. To install it, I used:
```
sudo apt-get install conky-all
```

I then used a conkyrc that I found on an internet tutorial. It seemed to run okay but it was very ugly so I tweaked a few variables. However, after doing so, I couldn't get conky to work again. So, just to see if it was the variables that I set which could have broke it, I changed the conkyrc file back to that ugly one which worked before. I then tried to run conky again and this time it didn't work either. 

I then decided to remove conky in an effort to reinstall the conky, this time just conky as opposed to conky-all. I used:
```
sudo apt-get remove conky-all
```

Thinking that I had successfully removed conky, I did another apt-get to install conky. When I couldn;t get that one to work, I tried to remove it. However, this time I decided to check and see if it was actually removed, by using:
```
conky -v
```

Apparently I wasn't able to remove conky because the terminal kicked back:
```

dell:~$ conky -v
Conky 1.8.0 compiled Fri Apr 23 10:38:37 UTC 2010 for Linux 2.6.24-27-server (i686)

Compiled in features:

System config file: /etc/conky/conky.conf
Package library path: /usr/lib/conky

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft
  * ARGB visual

 Music detection:
  * MPD
  * MOC

 General:
  * math
  * hddtemp
  * portmon
  * Curl
  * RSS
  * Weather (METAR)
  * Weather (XOAP)
  * wireless
  * support for IBM/Lenovo notebooks
  * nvidia
  * eve-online
  * config-output
  * Imlib2
  * ALSA mixer support
  * apcupsd
  * iostats
  * ncurses
  * Lua

  Lua bindings:
   * Cairo
   * Imlib2

```

Can anyone enlighten me as to what is going on and how I might troubleshoot this by either removing the conky package all together or finding out what went wrong so that I can try and fix it?

Any and all help would be greatly appreciated. Thanks.

Hi you can remove it and all config files by typing this command
```
Sudo apt-get --purge remove package name
```Also there is a lot that goes into getting a conky to work and look the way you want it to, start by checking out [http://conky.sourceforge.net/](http://conky.sourceforge.net/)  :guitar:

---

### Post by airspoon on 2011-05-25
No, is that what I'm doing wrong here? Should I delete the conkyrc file?

Thanks.

---

### Post by airspoon on 2011-05-25
Okay, thanks guys! Using the --purge worked. For future reference, should I use that command for other packages that I may need to remove?

Again thanks!

--airspoon

---

### Post by linuxinstalledfromhdd on 2011-05-25
What I would do is uninstall Conky completely before trying to reinstall it.  It sounds like you have residual config files remaining  even after you reinstall conky that could be the culprit. I could be wrong about this though. :S

---

### Post by airspoon on 2011-05-25
I thought that I had completely uninstalled it. I was unaware of the --purge parameter. However, after using the command:
```
sudo apt-get --purge remove conky
```That should have fixed whatever I messed up by installing over the other install, right? Thanks.

Also, though off-topic it might be, I noticed that the output of the terminal said 'Linux 2.6.24-27-server'. Is that correct even though I have the desktop version of Ubuntu? I just noticed that.

---

### Post by linuxinstalledfromhdd on 2011-05-25
I don't know about that. Where did you download your disc from?  There is a server version you could have installed.

---

### Post by airspoon on 2011-05-25
@[linuxinstalledfromhdd]("http://ubuntuforums.org/member.php?u=1050936")

I got it from the Ubuntu website and I'm absolutely certain that I got the desktop version. I just had noticed that when I checked the version of conky, it said '... for Linux 2.6.24-27-server'. Hmmmmm....:o I'm wondering if I got the wrong conky package, though I got it through 'apt-get' so I don't know how I would get the wrong package.

---

### Post by linuxinstalledfromhdd on 2011-05-25
That sure is strange.

---

### Post by wildmanne39 on 2011-05-25
> **airspoon said:**
> No, is that what I'm doing wrong here? Should I delete the conkyrc file?

Thanks.

Hi, you will need to read the conky pages that I gave you in that link and there is a thread that is good with conkies it is called conky screen shots. I will show you what mine looks like but I am not that good at them I took one from the thread and made it work on my computer, but this one is pretty hard better to start with an easier one then move on to a harder one.:D

---

### Post by linuxinstalledfromhdd on 2011-05-25
That looks sharp! :P

---

### Post by airspoon on 2011-05-25
Wow, that does look amazing! I also like that bottom task-bar (menu). How did you get that? Is that part of Unity, or can I get one like that for Gnome Classic?

I'll take a look at those links. Thanks for the help.

--airspoon

---

### Post by wildmanne39 on 2011-05-25
> **airspoon said:**
> Wow, that does look amazing! I also like that bottom task-bar (menu). How did you get that? Is that part of Unity, or can I get one like that for Gnome Classic?

I'll take a look at those links. Thanks for the help.

--airspoon
Hi, thanks to both of you, the bottom launcher is called awn and it is in the synaptic package manager,also they have one called docky, I used the instructions from a thread on here two days ago and got the cube and all effects working too, so I a am pretty happy. The script for the conky was done by VinDsl he does great work, I just modified it to work with my computer.

---

