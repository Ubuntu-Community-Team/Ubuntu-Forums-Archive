---
title: "boot time text screen ends at ubuntu@ubuntu:~$"
date: 2010-12-20
forum: General Help
---

### Post by Mike_tn on 2010-12-20
What can you do when you get blank screens with text at boot time that stop at prompts like this ubuntu@ubuntu:~$

This is for a Ubuntu dual-boot installation that's more or less good and working fine for a while, and then for instance maybe I messed with something like a plymouth splash thing or had a large download from the update manager or played with a "dd" restore to the MBR. *I have no problems currently but did in the past, more than once*. So I'm planning for future upheavals. Usually when it happens I pretty much abort everything and reboot with a LiveCD and reinstall GRUB or last time I used SuperGrub2 to boot in to the installation then purged and reinstalled fresh GRUB packages. But what if I have my laptop away from home and no disks with me. Can I do anything at those blank screen prompts to boot in? I'm going by memory but I have seen various prompts that look like terminal prompts, not the grub prompts. Stuff like ubuntu@ubuntu:~$ or root@ubuntu:~$ or in other distros I see  [myname@*localhost* ~]$  
What can I type to get saved?

---

### Post by psihokiller4 on 2010-12-20
try

```
startx
```

but if you don't have installed any desktops yet

you may prefer:

```
sudo aptitude install ubuntu-desktop
```

---

### Post by sikander3786 on 2010-12-20
I apologize but I couldn't understand your post properly.

Do you mean it is all working and just starts booting to the command prompt after an update/upgrade?

Or when you re-install Grub?

Which graphics card is there and any proprietary drivers are installed then?

---

### Post by Mike_tn on 2010-12-20
thanks **psihokiller4**! I will save that to a text doc on my USB

(like your signature comment, i tried Mandriva, Xubuntu and a dozen live CDs, I come back to Ubuntu too, really good stuff, good people)

---

### Post by Mike_tn on 2010-12-20
> **sikander3786 said:**
> I apologize but I couldn't understand your post properly.

Do you mean it is all working and just starts booting to the command prompt after an update/upgrade?

Or when you re-install Grub?

Which graphics card is there and any proprietary drivers are installed then?

I meant it is not going to the blank screen with prompt at present but has many times in the past. So I have no malfunction to try a solution on today. Just want tips for the future because often I'm offline when on Ubuntu, not always, and usually fix it with a sledgehammer approach.

It might go to the prompt when something is changed. Or maybe if I havn't used Ubuntu for a day or two because I was using the other OS and come back to it and now its weirding out at boot-time for an unknown reason. I play with things like Live USBs and Live CDs and various OSs.

I have two Ubuntu systems. A 2010 Dell Laptop with Intel chipset that can get online and dual boots with W7. And a 2006 hp desktop with nVIDIA chipset and nvidia-common driver from Ubuntu and it dual boots with XP.

By the way: that machine set up is a good way to save yourself a monthly Internet charge. You can find a wireless connection to hop on with your laptop wherever, libraries, hospitals, schools, neighbors. The cost of the internet will pay for your laptop in .... I got an 18 month no interest deal on the laptop and I figure it's paid for in Internet fee savings. I copied all packages to the offline desktop and they match.

---

### Post by sikander3786 on 2010-12-20
Ok, then sometimes reconfiguring the graphics also helps if the updates break graphics somehow.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bad
```

Note capital 'X' for X11. This might return an error if there is no preconfigured xorg.conf. Just ignore and proceed to the next one.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

```
sudo shutdown -r now
```

---

### Post by Mike_tn on 2010-12-20
> **sikander3786 said:**
> Ok, then sometimes reconfiguring the graphics also helps if the updates break graphics somehow.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bad
```Note capital 'X' for X11. This might return an error if there is no preconfigured xorg.conf. Just ignore and proceed to the next one.

```
sudo dpkg-reconfigure -phigh xserver-xorg
``````
sudo shutdown -r now
```


ahhh thanks for that. Saved it with the other. Making a print out.

---

