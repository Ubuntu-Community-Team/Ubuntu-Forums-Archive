---
title: "Ubuntu and Kubuntu difference in iso file size"
date: 2006-02-01
forum: General Help
---

### Post by Mishal on 2006-02-01
I have been using Ubuntu but want to try out KDE. But Synaptic tells me I will have to download more than 200MB to install KDE. On the other hand, the iso downloads of Ubuntu is 617MB and Kubuntu is 640MB....just a difference of 23MB?

So what's the catch? I have a slow connection and Synaptic is especially slow in downloading packages. And I am planning to upgrade to Breezy anyway (I am on Hoary now). So, should I download Ubuntu Breezy or Kubuntu Breezy? If I download Kubuntu, can I revert to GNOME-based Ubuntu when I want to? How?

---

### Post by korkow on 2006-02-01
I would recommend just installing ubuntu, and then do:

sudo apt-get install kubuntu

try it out, see if you like it. If not, just do

sudo apt-get remove kubntu.

---

### Post by Qrk on 2006-02-01
The kubuntu cd doesn't include Gnome. The 200MB extra to install kubuntu from synaptic is in addition to Gnome.

You can download whatever iso you want (kubuntu or ubuntu) but if you want the other desktop you have to install the synaptic packages.

---

### Post by qalimas on 2006-02-01
[QUOTE=Mishal]I have been using Ubuntu but want to try out KDE. But Synaptic tells me I will have to download more than 200MB to install KDE. On the other hand, the iso downloads of Ubuntu is 617MB and Kubuntu is 640MB....just a difference of 23MB?

So what's the catch? I have a slow connection and Synaptic is especially slow in downloading packages. And I am planning to upgrade to Breezy anyway (I am on Hoary now). So, should I download Ubuntu Breezy or Kubuntu Breezy? If I download Kubuntu, can I revert to GNOME-based Ubuntu when I want to? How?[/QUOTE]

The 23mb difference in ISO is simply because Kubuntu doens't include GNOME, if you want both, you have to have the size for both.  IOW, that 23MB is pretty much just the difference in GNOME and KDE in the distros, the 200 MB is how big the kubuntu install is, but it's not shown in the ISO as that much more, because you don't have GNOME taking up it's some 200mb.  Hope that was clear, it's getting late :P

---

### Post by Sutekh on 2006-02-01
[QUOTE=korkow]I would recommend just installing ubuntu, and then do:

sudo apt-get install kubuntu

try it out, see if you like it. If not, just do

sudo apt-get remove kubntu.[/QUOTE]
To install kubuntu you need to use
```
 sudo apt-get install kubuntu**-desktop**
```
and to remove the kubuntu-desktop you will have to folow this very simple guide

[HOWTO Fully remove the kubuntu-desktop meta-packages - by ]("http://ubuntuforums.org/showthread.php?t=96048&highlight=remove+kubuntu")[aysiu]("http://ubuntuforums.org/member.php?u=21941")

simply removing kubuntu-desktop won't achieve this

---

### Post by Mishal on 2006-02-01
[QUOTE=qalimas]The 23mb difference in ISO is simply because Kubuntu doens't include GNOME, if you want both, you have to have the size for both.  IOW, that 23MB is pretty much just the difference in GNOME and KDE in the distros, the 200 MB is how big the kubuntu install is, but it's not shown in the ISO as that much more, because you don't have GNOME taking up it's some 200mb.  Hope that was clear, it's getting late :P[/QUOTE]
Yup, that was clear. Thanks.

By the way, its not getting late HERE. It's early morning.:mrgreen:

---

