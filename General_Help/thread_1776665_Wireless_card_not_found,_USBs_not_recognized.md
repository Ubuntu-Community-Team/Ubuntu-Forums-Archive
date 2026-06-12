---
title: "Wireless card not found, USBs not recognized"
date: 2011-06-06
forum: General Help
---

### Post by ObliviousFreak on 2011-06-06
Okay, this might be really simple, I'm brand new to linux. 

So I'm running a live disk of ubuntu 11.04 because my windows 7 is totally messed up and wouldn't recognize my external hard drive and I cant back up my documents. I actually really like Linux and wanna keep it, but I have 2 problems. 1, I can't figure out for the life of me how to connect to the Internet. Its not scanning for any wireless networks and only seems to want me to connect via Ethernet. I think the problem is that it doesn't recognize my wireless card/doesn't know it's installed. Is there any way to fix that? I just want to be able to connect to wifi. 

Now my second question. I can acess all my files fine, but Linux doesn't seem to register my external hard drive either, nor any other USB device. It just acts like there not plugged in. No error message or Anything. Is the a way to fix that? I fear that there might be some sort of hard ware issue, because in windows seven it doesn't recognize USB devices or my wireless card (among many many other problems) either. Although, I tried An older version of ubuntu on this same computer once and had a similar wireless issue which I was never able to resolve before my 7 was having any wireless issues.


Anyway, and help whatsoever would be really appreciated. I really need my computer back


Btw if it helps I have a Dell inspiron n4010

---

### Post by linuxinstalledfromhdd on 2011-06-06
> **ObliviousFreak said:**
> Okay, this might be really simple, I'm brand new to linux. 

So I'm running a live disk of ubuntu 11.04 because my windows 7 is totally messed up and wouldn't recognize my external hard drive and I cant back up my documents. I actually really like Linux and wanna keep it, but I have 2 problems. 1, I can't figure out for the life of me how to connect to the Internet. Its not scanning for any wireless networks and only seems to want me to connect via Ethernet. I think the problem is that it doesn't recognize my wireless card/doesn't know it's installed. Is there any way to fix that? I just want to be able to connect to wifi. 


You need to install Wireless Network Drivers:

```

sudo apt-get ndisgtk ndiswrapper-common ndiswrapper-utils-1.9

```

Then you will need to download the windows *.inf wireless driver for your wireless adaptor. 

Here is more instructions on how to accomplish this:


[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

> 
Now my second question. I can acess all my files fine, but Linux doesn't seem to register my external hard drive either, nor any other USB device. It just acts like there not plugged in. No error message or Anything. Is the a way to fix that? I fear that there might be some sort of hard ware issue, because in windows seven it doesn't recognize USB devices or my wireless card (among many many other problems) either. Although, I tried An older version of ubuntu on this same computer once and had a similar wireless issue which I was never able to resolve before my 7 was having any wireless issues. 

Try the NTFS Configuration tool:

```
sudo apt-get install ntfs-3g
```

Google that application to learn how to use it.

---

### Post by ObliviousFreak on 2011-06-06
I don't think that it's a driver issue. When I do lspci it doesn't even bring up what wireless card I have. Also when I tried to get the ndiswrapper, it said "invalid operation ndisgtk"

---

### Post by linuxinstalledfromhdd on 2011-06-06
Try using a live disc or live USB of Ubuntu 10.10, and check and see if these problems still exist:

Here is a walk-though to try this:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

When you boot into the live disc, find out if these problems still exist or not.

---

### Post by ObliviousFreak on 2011-06-06
They do. I tried using 10.10 before, and the Internet problem was still there. That's why I don't still use it. I never tried using a USB. I think I still have my old live disk, so I'll see about USBs

---

### Post by linuxinstalledfromhdd on 2011-06-06
Let's do a cross reference on your system.

What model/make of system?  What the wireless adaptor you are trying to install make/model?   

Let's get the bottom of that first...

---

### Post by ObliviousFreak on 2011-06-06
Yea, USBs don't work on 10.10 eather

---

### Post by linuxinstalledfromhdd on 2011-06-06
Did you try this?

[http://times.imkrisna.com/2011/02/fixing-network-problems-ubuntu-10-04-on-dell-inspiron-14r-n4010/](http://times.imkrisna.com/2011/02/fixing-network-problems-ubuntu-10-04-on-dell-inspiron-14r-n4010/)

---

### Post by ObliviousFreak on 2011-06-06
It's a Dell inspiron n4010, and i have no clue what the adaptor is. The card is whatever came in th comp, and I'm trying to use it with an airport travel router

---

### Post by linuxinstalledfromhdd on 2011-06-06
For now keep googling around that name/make/model on google search engine, and include in the search terms Ubuntu, and see if you find a work-around.  It looks like you are going to need to download the drivers from the manufacture's web site, and then use ndiswrapper.

---

### Post by ObliviousFreak on 2011-06-06
*sigh* yea, I guess I'll have to. I kept getting errors with that workaround

---

