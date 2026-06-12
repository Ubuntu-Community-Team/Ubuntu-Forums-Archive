---
title: "Steam crashing"
date: 2011-01-01
forum: General Help
---

### Post by j1gs4w on 2011-01-01
I am running ubuntu 10.10 and wine 1.3.10. Steam installs and runs fine, but once i login, within 5-10 seconds, steam crashes. 

copy from terminal:
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used

i have google'd about it, and have nothing regarding it.

any advise would be great,
thanks

---

### Post by lovinglinux on 2011-01-02
Have you tried installing Steam via PlayOnLinux?

[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

I'm not using 10.10, but Steam works incredibly well for me.

---

### Post by MrWestwood on 2011-01-02
> **lovinglinux said:**
> Have you tried installing Steam via PlayOnLinux?

[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

I'm not using 10.10, but Steam works incredibly well for me.

Is Play on Linux free?

---

### Post by Vigh on 2011-01-02
yes, just install from software centre I believe, otherwise although I have never tried, you could use a Virtual Box Windows Machine with Direct3D support installed, but you would have to own a copy of XP to do that

---

### Post by lovinglinux on 2011-01-02
> **MrWestwood said:**
> Is Play on Linux free?

Yes, it is. It actually uses Wine, but provides an easy way of properly configuring it according to software installed. 

It has been a while since I tried to install Steam without PlayOnLinux, so I'm not sure if the improvements are due to wine itself. However, last time I tried, it didn't work well. I wasn't able to install demos or buy games. Now it works perfectly. BTW, there is a huge Holiday discount now, that will last for less than a day. I just bought Portal for $7.50.

---

### Post by j1gs4w on 2011-01-02
lovinglinux, i'm <3'ing u 


thanks alot for your help

---

### Post by j1gs4w on 2011-01-02
lovinglinux, i'm <3'ing u 


thanks alot for your help

---

### Post by j1gs4w on 2011-01-02
lovinglinux, i'm <3'ing u 


thanks alot for your help

---

### Post by axept on 2011-01-02
I'm running Steam on Wine, works well. I've downloaded Condition Zero from Steam.

The gameplay works great for 5-10 min, then it hangs, can't do anything. Only way I can quit is a hard reboot. 

Anyone know why this is happening? I've tried running it in VirtualBox with XP, but got a problem with the mouse and I got too high latency in online game.

I use Wine 1.3.9 on Ubuntu 10.10

---

### Post by lite1979 on 2011-03-30
axept, this is off topic, but if you're running certain games in wine, you may have to disable GameOverLay.dll in winecfg in order for your game to run...

---

### Post by norseman-has-a-laptop on 2011-10-23
wget -q "http://deb.playonlinux.com/public.gpg" -O- | sudo apt-key add -
sudo wget [http://deb.playonlinux.com/playonlinux_lucid.list](http://deb.playonlinux.com/playonlinux_lucid.list) -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux

now how do i uninstall this haha it made my steam problem even worse

---

