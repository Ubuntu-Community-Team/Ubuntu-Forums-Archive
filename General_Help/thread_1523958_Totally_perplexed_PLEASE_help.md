---
title: "Totally perplexed PLEASE help"
date: 2010-07-04
forum: General Help
---

### Post by unbuntunewb on 2010-07-04
So I turned on my computer and it was not widescreen as it should be but was a square in the middle of my monitor and had low res. So I updated and restarted. After doing that I get a blank screen. I can hear the drums at startup and it seems its working ok but for some reason I get no screen. My monitor just says "VGA not supported" I have nVidea

I dont know what to do please help!

also my monitor is a HD tv

---

### Post by J V on 2010-07-04
Which model HDTV do you have, this sounds like a connection error... Perhaps you can connect via a DVI cable? (It's the white one as opposed to the blue one)

Also, could it be that you plugged it into the wrong socket? The video card and motherboard each have their own video sockets, you need to plug it into the video card socket.

---

### Post by unbuntunewb on 2010-07-04
I have an isignia tv and it worked fine before. 

I just did this at a terminal I got by hitting control alt f1 and right click

ctrl+alt+f1 and login if you need to

sudo nano /etc/X11/xorg.conf

find this section and edit it to read the same

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

then type this

sudo /etc/init.d/gdm restart

now I get the ubuntu screen but it just freezes. The five little dots that blink as it boots dont even move

---

### Post by J V on 2010-07-04
Ok, which version of ubuntu are you on, later versions don't use xorg.conf IIRC...

As for your setup, you screwed up the xorg.conf...

Try this to reset it:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by unbuntunewb on 2010-07-04
in on 10.4.

I do not know how to get to the terminal (or wherever it is I can put in that command) before I did anything to the xorg I was able to get to a terminal by hitting ctr alt right click and f1, now I cant do anything

I also tried recovery by hitting shift but that didnt work either

---

### Post by J V on 2010-07-04
Ok, right now you've gotten yourself into such a paradox it will just be easier to reinstall the system... Sorry. Backup your stuff before you go messing about with system files

---

### Post by unbuntunewb on 2010-07-04
are you positive? what exactly did I do? also I did this when I could but nothing happened
sudo dpkg-reconfigure xserver-xorg

---

### Post by overdrank on 2010-07-04
Try booting into recovery mode and reconfigure the graphics.
When booting the system at the grub loading select recovery mode then will be given the option to boot normally and other options like configure graphics. I do not remember all the options at the moment.

---

### Post by J V on 2010-07-04
Well, you told the system to output VGA on a DVI only system, then your grub (Boot system) locked you out cause you didn't set it up for recovery, so all thats left is to either chroot or reinstall, and reinstall is much much easier by now...

---

### Post by unbuntunewb on 2010-07-04
how exactly do I get to recovery mode or grub? can I use the live cd to restore?

---

### Post by J V on 2010-07-04
You can use the livecd, but that's chrooting and you need to know a good deal of commandline to make it work...

You said previously that you tried shift and it didn't work (Which was the grub recovery)

---

### Post by unbuntunewb on 2010-07-04
when and where should I be pushing shift?

---

### Post by J V on 2010-07-04
Just hold it from when you power on the computer until it crashes or you see a menu...

---

### Post by unbuntunewb on 2010-07-04
well this blows. back to windows

---

