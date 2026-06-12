---
title: "Ubuntu stuck at log-in loop. Is GNOME broken? How can I fix it?"
date: 2010-12-28
forum: General Help
---

### Post by sirspazzolot on 2010-12-28
When I boot into Ubuntu, it goes to the log in screen. I can type in my password and then the screen flashes black and then the log-in screen comes back. If I boot into recovery mode, I can log in via terminal, but if I type startx it just brings up a black screen and a mouse cursor and that's it. Did GNOME get messed up? How would I fix it? I have an Ubuntu LiveCD that I can use, so if I have to install any packages or something, would I be able to download them in the livecd and just install them on my broken installation instead of having to figure out connecting to wifi in a terminal?

thanks in advance.

---

### Post by sirspazzolot on 2010-12-28
I'd lurrrrrrrv a response. Gparted also doesn't work on my computer, either, and I can't reinstall Ubuntu because the installer crashes since gparted is broken. Should I just reformat my entire hard drive and pray that I can reinstall Ubuntu afterwards? I really don't know why gparted won't work. Would reformatting so my hard drive is just one big partition fix it?

---

### Post by amsterdamharu on 2010-12-28
I think this is an icompatible videocard. Did it work before?

If you get the login screen could you press control + alt + F1, then log in and post the output of the following command?

```
sudo lshw -C video
```

Just to see what videocard you've got.

---

### Post by sirspazzolot on 2010-12-28
It worked before. I have an intel integrated video card. I don't remember the exact name, but my video card isn't the issue.

---

### Post by sirspazzolot on 2010-12-28
By the way, I'm on an Ubuntu LiveCD if that's any indication that my video card works fine.

---

### Post by sirspazzolot on 2010-12-28
I'm gonna go ahead and bump this topic before I go to bed. Honestly, I give up trying to fix this install. Will somebody please tell me if reformatting my entire hard drive will let me use gparted/Ubuntu installer? Or present me with a method to install Ubuntu to a preexisting ext4 partition. My computer has done nothing but break more since I started trying to fix it, so I'm giving up. I want to just start over.

---

### Post by amsterdamharu on 2010-12-28
> By the way, I'm on an Ubuntu LiveCD if that's any indication that my video card works fine. 	
No, it's not. It means it could work fine but the installed Ubuntu might have some broken settings.
Re formatting and re installing might fix it but it's a bit overkill since you might be able to fix it easily if we know what's wrong with it.
You don't have a cable connection to the Internet do you? Otherwise you could try the recovery mode and do a dpkg reconfigure (repairs broken packages).

If you're in the terminal (control + alt + F1 and log in) you can check the /var/log/Xorg.0.log
I am talking about your installed Ubuntu of course since you won't find anything in the var/log of the live CD

Type the following command (note the X is upper case):
```
nano /var/log/Xorg.0.log
```

Maybe you'll find something in there, errors usually begin with (EE)

Maybe the kern.log has something interesting:
```
nano /var/log/kern.log
```

It might not be the videocard since you get a graphic log in screen.

---

### Post by sirspazzolot on 2010-12-28
I know with 100% certainty that unless my video card became defective in the last four days, it's not the issue. 10.10 worked perfectly fine (except for gparted) until I was trying to fix gparted. I'll post the content of the logs here; I don't really trust my own judgement anymore and  I just want to fix my laptop. I don't really mind overkill as long as I'm sure beyond reasonable doubt that it would work.

---

### Post by sirspazzolot on 2010-12-28
The xorg log file had:
```
 (WW) The directory "/usr/share/fonts/cyrillic" does not exist.

(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory) 
```
It also says it's falling back to old probe method for vesa and fbdev and that AIGLX is disabled.

I couldn't tell if anything was weird in the kernel log. I wish I could just post the whole damn thing here though

---

### Post by sirspazzolot on 2010-12-28
I think I was right about GNOME being broken;
```
gnome : depends: swfdec-Mozilla but it is not going to be installed
E: Broken packages 
```

---

### Post by sirspazzolot on 2010-12-28
Installing gnome has a dependency hell situation so I tried running sudo apt-get install Ubuntu-desktop but it appears I'm not online. I went to the log-in screen, ctrl+alt+f1 and ran it. How do I connect to wifi through a terminal? :P

---

### Post by sirspazzolot on 2010-12-28
cough

---

### Post by amsterdamharu on 2010-12-28
```
iwconfig
```Shows you available network device

```
sudo ifup [COLOR=Red]wlan0[/COLOR]
```ifup activates a network device, here wlan0 is an example check the iwconfig what the name of your wireless is.

If it's not configured check here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
under 3.6.2

---

