---
title: "Linux Troubles! (Frustrated)"
date: 2011-06-04
forum: General Help
---

### Post by gregoryshock on 2011-06-04
I apologize for not being more active here.  I just been so busy lately.  

I installed Ubuntu 10.04 64-bit.  (That is all I know about my Linux operating system)  

I have Windows Vista 32 Bit.  I would like to change the boot order.  In other words, I want windows to be my default boot, not Linux.

So far Linux has been useless to me.  My main problem, is I don't know enough about it.  Apparently I need wine, so that I can install a windows type manager. Or I can't run my modem.  Otherwise I can't get it online!  (I read some where, that some people have connected using a Verizon modem without the manager.  But this requires user name and password.  None of which I have)  

I posted here once before, but the advice didn't help.  There simply wasn't enough information.  They told me what website to go to.  [http://apt-web.dahsy.at/](http://apt-web.dahsy.at/)  And then told me Select your base distribution.  I don't know what my base distribution is.  How can I find out?  And then I have no idea what mirror to download from.

---

### Post by Joe- on 2011-06-04
No sure if this will work but if you install a program called 'grub customizer' from synaptic you can move the OS lists and put Vista above Linux. I'm not sure if this will work because I have Wubi and the program doesn't work for me.

---

### Post by linuxinstalledfromhdd on 2011-06-04
> **gregoryshock said:**
> I apologize for not being more active here.  I just been so busy lately.  

I installed Ubuntu 10.04 64-bit.  (That is all I know about my Linux operating system)  

I have Windows Vista 32 Bit.  I would like to change the boot order.  In other words, I want windows to be my default boot, not Linux.

So far Linux has been useless to me.  My main problem, is I don't know enough about it.  Apparently I need wine, so that I can install a windows type manager. Or I can't run my modem.  Otherwise I can't get it online!  (I read some where, that some people have connected using a Verizon modem without the manager.  But this requires user name and password.  None of which I have)  

I posted here once before, but the advice didn't help.  There simply wasn't enough information.  They told me what website to go to.  [http://apt-web.dahsy.at/](http://apt-web.dahsy.at/)  And then told me Select your base distribution.  I don't know what my base distribution is.  How can I find out?  And then I have no idea what mirror to download from.

Try burning a disc of 10.10, and try installing from that.  Here is a really simple walkthrough you can follow if you are having trouble:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by gregoryshock on 2011-06-04
Since I have a 10 gig internet limit (Thanks to Verizon's plans)  I don't dare download my own Linux versions.  Don't have enough bandwidth for it.  My friend downloaded this one for me.  I'm sure it's a i386 cause This isn't an AMD computer.

---

### Post by linuxinstalledfromhdd on 2011-06-04
It's not a linux problem. You need more bandwidth.  I understand.

---

### Post by stinkeye on 2011-06-04
For your boot order, run this in terminal...
```
grep menuentry /boot/grub/grub.cfg | cut -b 1-11 --complement | cut -d "'" -f1 | cut -d "\"" -f 1 | nl --starting-line-number=0
```

Numbering starts at zero.
Take note of the number for your Windows entry.
eg for me it's [COLOR="Magenta"]4[/COLOR]
```
glen@Natty:~$ grep menuentry /boot/grub/grub.cfg | cut -b 1-11 --complement | cut -d "'" -f1 | cut -d "\"" -f 1 | nl --starting-line-number=0
     0	Ubuntu, with Linux 2.6.38-8-generic
     1	Ubuntu, with Linux 2.6.38-8-generic (recovery mode)
     2	Memory test (memtest86+)
     3	Memory test (memtest86+, serial console 115200)
     [COLOR="#ff00ff"]4[/COLOR]	Windows NT/2000/XP (loader) (on /dev/sda1)
     5	Ubuntu, with Linux 2.6.35-28-generic (on /dev/sdc1)
     6	Ubuntu, with Linux 2.6.35-28-generic (text mode) (on /dev/sdc1)
     7	Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sdc1)
     8	Ubuntu, with Linux 2.6.35-27-generic (on /dev/sdc1)
     9	Ubuntu, with Linux 2.6.35-27-generic (text mode) (on /dev/sdc1)
    10	Ubuntu, with Linux 2.6.35-27-generic (recovery mode) (on /dev/sdc1)
```


Now open grub with gedit as root...
```
gksudo gedit /etc/default/grub
```


Change the line (should be at the top)
```
GRUB_DEFAULT=0
```
to
```
GRUB_DEFAULT=[COLOR="#ff00ff"]x[/COLOR]
```
where [COLOR="#ff00ff"]x[/COLOR] is your windows boot menu entry number.

Save and close.

In the terminal run
```
sudo update-grub
```
Done.

**@ Joe-** I don't think grub-customizer is in Synaptic.
You would need to install through this PPA: [**_[COLOR="DarkRed"]https://launchpad.net/~danielrichter2007/+archive/grub-customizer[/COLOR]_**]("https://launchpad.net/~danielrichter2007/+archive/grub-customizer")

---

### Post by Joe- on 2011-06-04
Have you tried my suggestion? Post #2

---

### Post by gregoryshock on 2011-06-04
This is all very complicated stuff.  I will need to print this, and study it more.  Do I need to download grub from somewhere?

---

### Post by Joe- on 2011-06-04
Have a look at this video: [http://www.youtube.com/watch?v=In0-_VF5Pe8&feature=youtube_gdata_player](http://www.youtube.com/watch?v=In0-_VF5Pe8&feature=youtube_gdata_player)

Should help you move the OSs
Any problems just post them here :)

---

### Post by gregoryshock on 2011-06-04
Thank you :)  I'm currently downloading the video.

---

