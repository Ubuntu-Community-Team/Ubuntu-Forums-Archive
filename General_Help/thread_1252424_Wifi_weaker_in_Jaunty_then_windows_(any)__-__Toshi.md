---
title: "Wifi weaker in Jaunty then windows (any)  -  Toshiba Satellite A215 S7437"
date: 2009-08-28
forum: General Help
---

### Post by Parastatic on 2009-08-28
Hello I have  Toshiba Satellite A215 S7437, when i am running windows my wifi works perfectly.  Can go everywhere in my home and not have to worry about it.  Now the problem is, when I am running Ubuntu Jaunty x64 my wifi does work, but!  it will detect the access points but will says the connection is weak and list it at 1mb/s.  e.g. everything times out unless I get really close to the access point.   I waited until now to switch to Linux because I wanted my laptop to be supported and technically it is, but the wifi does not work nearly as it should.   Any help would be greatly appreciated.    Thanks in advance.

---

### Post by Parastatic on 2009-08-28
I am gonna re post this in the networking section, just noticed that now.  Sorry

---

### Post by uylug on 2009-08-28
Can you post the output of
```
iwconfig
```

Also, don't trust the signal indicator. On my computer it often says it's at 30% and works WAY better than when i used to use Windows which said it was at a stunning 100%.

Windows just lies.

---

### Post by Parastatic on 2009-08-28
yeah give me a minute  :)

---

### Post by Parastatic on 2009-08-28
This si what iwconfig gave me.   Only have windows installed atm  so have to do the live cd, but had the same problem either way.
```
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"belkin54g"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:17:3F:67:D8:BC   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=40/100  Signal level:-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ubuntu@ubuntu:~$ 
```

---

### Post by SuaSwe on 2009-08-28
> 
On my computer it often says it's at 30% and works WAY better than when i used to use Windows


I agree - it appears Windows is less accurate. On XP it was always "excellent" whereas with Ubuntu it sits at around 75-80%, and I never experience drops in connection (as opposed to with Windows, where it occasionally lost signal).

---

### Post by Parastatic on 2009-08-28
> **SuaSwe said:**
> I agree - it appears Windows is less accurate. On XP it was always "excellent" whereas with Ubuntu it sits at around 75-80%, and I never experience drops in connection (as opposed to with Windows, where it occasionally lost signal).


guess I am special then, because mine gets worse with ubuntu.  Really want to switch over, but if I cant get this working properly the other half wont be very happy with me.

---

### Post by SuaSwe on 2009-08-28
What encryption are you using? Have you checked in System -> Administration -> Hardware Drivers whether there might be some lovely proprietary drivers for you to use? :)

Was the wireless stable before? Is it actually dropping now or just *looking* unstable?

---

### Post by Parastatic on 2009-08-28
No encryption, it was never stable on ubuntu unless i was next to the ap.  otherwise it don't work at all.  Using xp atm.

---

### Post by SuaSwe on 2009-08-28
Try changing wireless broadcast channels, and if you can, upgrade the drivers. What wireless card/drivers are you using?

---

### Post by Parastatic on 2009-08-28
it is a realtek RTL8187B / and using the default drivers from the distro.

---

### Post by uylug on 2009-08-28
Same as mine! I am running the same drivers as you. If you've got a 32 bit distro, install ndiswrapper and set up windows drivers!! I've got both 32 bit and 64 bit Ubuntu. For the 32 bit one, installing ndiswrapper was a great solution. For the 64 bit one, i was unable to install the 64 bit driver so i just run this command, which makes the connection work quite a bit better:

```
sudo iwconfig wlan0 retry 999999
```

---

### Post by Parastatic on 2009-08-28
I'll give that command a try and yeah I am using the 64 bit edition.  hopefully, i'll tell ya all about it on linux  lol.

---

### Post by uylug on 2009-08-28
That command needs to be run every single time you boot your computer. And i haven't found a way to make it automatic because it needs to be run once the connection has been established and not *exactly* at startup... so no idea... If you find a solution let me know :D

Also, the 64 bit drivers caused my computer to crash and I had to hard reset it, login as root using safe mode and uninstall the drivers. I would not do it if it was you, but if you want you can give it a try. If you get it to work, it works way better than the default driver.,

---

### Post by Parastatic on 2009-08-28
Well it is working splendidly right now with that command and this is off of the live cd, and not an install.   Now your saying I should not use the drivers that came with it?  :o   Now I am happy to be using my laptop the way I wanted to the time I got it, about a year ago but nothing was supported lol.

---

### Post by uylug on 2009-08-28
> **Parastatic said:**
> Well it is working splendidly right now with that command and this is off of the live cd, and not an install.   Now your saying I should not use the drivers that came with it?  :o   Now I am happy to be using my laptop the way I wanted to the time I got it, about a year ago but nothing was supported lol.

I had problems with it, with different Ubuntu versions, but like I said, you can give it a try if you want but I would not do it. I am happy to hear it has been fixed! Its not a real fix but oh well :)

---

### Post by Parastatic on 2009-08-28
Now I just have to fix the tweaky video.  If I scroll fast

---

### Post by uylug on 2009-08-28
> **Parastatic said:**
> Now I just have to fix the tweaky video.  If I scroll fast

Wait, your computer is almost the same model as mine lol! Mine has a intel graphics chipset and i never had any problems with it. What about yours?

---

### Post by Parastatic on 2009-08-28
the specs of mine is a amd turion64 x2   ati radeon chipset and then the realtek wifi chipset

---

### Post by Parastatic on 2009-08-28
I'll be right back, have to go pick someone up from work, maybe you can help with my video issues as well.  :)

---

### Post by uylug on 2009-08-28
> **Parastatic said:**
> the specs of mine is a amd turion64 x2   ati radeon chipset and then the realtek wifi chipset

Allright, I've had an ATI card before and they are truly a pain. The safest way to install the drivers is the following.

Update your package list
```
sudo apt-get update
```Install Envy
```
sudo apt-get install envyng
```You can start envy from the terminal like

```
sudo envyng
```Or graphically using the Applications menu (I think).

You can use this tool to install your ATI Drivers. Let me know if it works!!

---

