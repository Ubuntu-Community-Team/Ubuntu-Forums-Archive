---
title: "How to restore graphic settings through terminal?"
date: 2010-04-06
forum: General Help
---

### Post by femil on 2010-04-06
Hi
I have a laptop fujitsu siemens amilo pi 1505 for about a year there was ubuntu 8.10 installed on it and everything worked fine. 3 days ago i upgraded it to 9.10 and there where the problems began. Sound crashed OS couldn't find sound card. I've removed alsa, pulse audio completly and sound came back. After about 5-15 min's icons dissappeared from the desktop and i had to restart. From then every time i start after booting i see that:
[http://img594.imageshack.us/img594/4158/img0158f.jpg](http://img594.imageshack.us/img594/4158/img0158f.jpg)
and if i change kernel:
[http://img144.imageshack.us/img144/555/img0159gl.jpg](http://img144.imageshack.us/img144/555/img0159gl.jpg)
though anything i do there in this window makes no difference whatsoever.
So then can I somehow restore graphic settings from the terminal?
Or repair/restore basic settings of ubuntu without loosing data?
Please help!:frown:

---

### Post by femil on 2010-04-06
is there anything i can try? please help i need this laptop for tomorrow with data!

---

### Post by clhsharky on 2010-04-06
HI

Need more info.

```
lspci
```

In terminal, give the results.


Sharky

---

### Post by pbrane on 2010-04-06
you can default your graphics setting like this:
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by femil on 2010-04-06
well i can't copy the lspci here but i know that the graphic card is Intel 945GM
also, when i type
sudo dpkg-reconfigure -phigh xserver-xorg 
nothing happens it just skips like i never typed that

---

### Post by pbrane on 2010-04-06
> **femil said:**
> well i can't copy the lspci here but i know that the graphic card is Intel 945GM
also, when i type
sudo dpkg-reconfigure -phigh xserver-xorg 
nothing happens it just skips like i never typed that

It's very quick. Did you logout/in or reboot after? You could also just remove your /etc/xorg.conf file or rename it. Then reboot.

---

### Post by femil on 2010-04-06
lspci card:
VGA compatible controller: intel corporation mobile 945GM/PM/GMS,  943/940GML express integrated graphics controller rev ( 03)

i did 
sudo dpkg-reconfigure xserver-xorg
and no change at all, still same screen should i purge xorg and reinstall it?

---

### Post by femil on 2010-04-06
during start i found that
[http://img682.imageshack.us/i/img0164fn.jpg/](http://img682.imageshack.us/i/img0164fn.jpg/)
and this Fail!.... during running in low graphics mode:
[http://img682.imageshack.us/i/img0163n.jpg/](http://img682.imageshack.us/i/img0163n.jpg/)[URL="http://img682.imageshack.us/i/img0164fn.jpg/"]
[/URL]

---

### Post by pbrane on 2010-04-06
if dpkg-reconfigure doesn't work you could try reinstalling xorg. That command should have updated your /etc/X11/xorg.conf file to default. I would try renaming /etc/X11/xorg.conf to /etc/X11/xorg.conf.bak to see if xorg is the problem. That should cause xorg to auto configure everything. If that doesn't work you can try reinstalling xorg.

After looking at your screenshots I see dkms is running fglrx update. That shouldn't be running if you have intel graphics.

---

### Post by femil on 2010-04-06
so what should i do then?

---

### Post by femil on 2010-04-06
purge fglrx?

---

### Post by pbrane on 2010-04-06
> **femil said:**
> purge fglrx?

That sounds like a plan. Try that and see if that helps. Try renaming /etc/X11/xorg.conf if it doesn't.

---

### Post by femil on 2010-04-06
when i try to purge it says "couldnt find package fglrx"... what should i type?

---

### Post by femil on 2010-04-06
i couldn't purge it it said it was not installed so i did that
[sudo apt-get install ubuntu-desktop --reinstall]("http://ubuntuforums.org/sudo%20apt-get%20install%20ubuntu-desktop%20--reinstall")
and everything got back to normal :S

---

