---
title: "Ubuntu to ?"
date: 2010-08-14
forum: General Help
---

### Post by fidelandche on 2010-08-14
Hi all,

At the moment I am running Lucid Lynx on my laptop, however it is running slow, so I would like to try a different version of Ubuntu but not sure which.

 The specs of my laptop are;

Processor	 Intel® Celeron® M Processor 440 
1 MB L2 cache | 1.86 GHz | 533 MHz FSB)
Chipset	 Intel® 943GML chipset
Display panel	 15.4-inch WXGA (1280 × 800)
Memory	Installed memory: 512 MB (2 × 256) 
Total slots: 2 DDR2 slots | Available slots: 0 DDR2 slots
Maximum memory: 2 GB
Video controller	 Intel® Graphics Media Accelerator 950 
Up to 64 MB of shared video memory
Audio	 High definition audio - 2 channel
Hard drive	80 GB 5400 RPM SATA hard drive
Optical drive	 8X Multi-format dual layer DVDRW
Modem	Integrated V.92 56K modem
Network	
10/100 Ethernet
Intel® PRO wireless 4965 802.11a/b/g

  Which version would run best on these specs?
  How do I change over? are the other versions in the repos?
  If they are in the repos, when I install does it remove Lucid?
  Or is it best just to download the file, burn to disk then install over/remove Lucid?

---

### Post by Smart Viking on 2010-08-14
You could install xfce4, another desktop enviroment. It is a little more lightweight. It will not remove anything only add features, and you can choose between gnome and xfce4 on the login screen.

```
sudo apt-get install xubuntu-desktop
```

---

### Post by fidelandche on 2010-08-14
> **Smart Viking said:**
> You could install xfce4, another desktop enviroment. It is a little more lightweight. It will not remove anything only add features, and you can choose between gnome and xfce4 on the login screen.


  Ok I did that, xfce4 is now installed, however when I booted up the laptop after the install I did not have the choice of gnome or xfce4. Has something gone wrong?

---

### Post by Pifilatakanemu on 2010-08-14
I'd rather suggest you to use LXDE. While Xubuntu can get even more bloated than Gnome LXDE really saves ressources.

Lubuntu will be an "official" part of the Ubuntu familiy with the release of 10.10 

At the login screen you should have the possilibity to select Gnome, XFCE, LXDE etc. check the row at the bottom.

Of course you don't see it when you have Auto-Login enabled.

Check it out:

[http://lubuntu.net/](http://lubuntu.net/)


You install it through the package "lubuntu-desktop"

---

### Post by Smart Viking on 2010-08-14
It should looks somewhat as the image below, you see "sessions: GNOME" at the bottom, thats where you choose. :)

[IMG]http://www.debianadmin.com/wp-content/gallery/1004/1.png[/IMG]

---

### Post by fidelandche on 2010-08-14
I guess I need to remove xfce4 first?

---

### Post by fidelandche on 2010-08-14
Ok, thanks for that Smart Viking. I must have missed that when I logged on. I was expecting the splash screen of Ubuntu and I got the plash screen of xfce4 instead.

---

### Post by Smart Viking on 2010-08-14
> **fidelandche said:**
> I guess I need to remove xfce4 first?

Not really, if you have enough space on your harddrive you can have so many desktop enviroments as you wish. :) But i suggest you at least try xfce4, to see if it helps with the speed. As lxde is much more light weight than xfce4 and gnome, it does not look so good(many people like it though).

If you want to remove xfce4, here is the command: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

:)

---

### Post by Pifilatakanemu on 2010-08-14
> **fidelandche said:**
> I guess I need to remove xfce4 first?


You can have XFCE, LXDE and Gnome installed at once without hassles.

---

### Post by Pifilatakanemu on 2010-08-14
> **Smart Viking said:**
>  As lxde is much more light weight than xfce4 and gnome, it does not look so good(many people like it though).

:)

Reconsider your statement after having a look at this screencast: 

[URL="http://lubuntu.net/blog/lubuntu-screencast-turn-lubuntu-ubuntu-look"]http://lubuntu.net/blog/lubuntu-screencast-turn-lubuntu-ubuntu-look
[/URL]

;D

---

### Post by jakupl on 2010-08-14
Small tip: When you have chosen one desktop environment, try to stick to it. I don't think it's good to switch back and forth. It will mess up some configuration files.
I might be wrong though.

---

