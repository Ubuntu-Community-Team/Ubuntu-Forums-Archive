---
title: "Laptop with WiFi working out of the box?"
date: 2006-02-28
forum: General Help
---

### Post by cronholio on 2006-02-28
Is there a laptop model that runs WiFi in Ubuntu easily, without having to install ndiswrapper or someting? I'm looking for something that costs less than &#8364;1000/$1200. I don't need a fancy graphics card, it will be for surfing and office work mainly. Any recommendations?

---

### Post by xhie on 2006-02-28
Hehe funny you ask...

What made me fall in LOVE with ubuntu was my WiFi working out of the box, infact everything working out of the box, I remember saying to myself "Oh my God... it all works, just like that, its amazing..."

Its a Toshiba R15 tablet. 

Now granted... The tablet stuff did NOT work out of the box, gettin the stylus to work took editing the xorg.conf file, the i810 driver does not support xrandr so to get the screen to filp I have to restart X with a differnt xorg.conf file.

But whatever, thats just tablet stuff, everything else was perfect. PERFECT.

Seriously I cant say it enough, this is why I love ubuntu. Those guys did an AWSOME job of getting the normal stuff working straight out of the box.

When I bought the R15 it was around $1,500 I think, probably cheeper now, and I dont know if it was just that or if most toshiba models are well supported, but I dont see why they wouldent be. 

As far as laptops go, I've seen alot, a LOT, of people have trouble with widescreen displays, for variours reasons, so stay away from that I guess, Compaq and ubuntu dont easly get along from what I can tell. Other then that I dont know, other then ... Ubuntu on the R15 rocks serious ***.

---

### Post by soonindallas on 2006-02-28
Laptop manufacturers are actually integrators.  Wifi working out of the box depends less on the brand of laptop than what type of 802.11 chipset is inside.  My Acer laptop is equiped with Intel's IPW2200 that is natively supported by Ubuntu, it just works. Out of the box.  Not all Acer's laptops are equipped with this 802.11 chipset and some require diswrapper (sp?).

This laptop has a widescreen and I have had no problems whatsoever with it.  However, Acer uses smart-battery technology that is unsupported by Linux so autonomous operation is touchy ... there is no battery meter for example.

I would suggest you think about the criteria that are important for YOU in a laptop based on the use YOU have for it: price, weight, volume, screen size, battery life, etc. How will you work with it ?

I needed a device that would work in several places, but not necessarily on the move: I rarely work in a place with no power, so the lack of a battery meter is not a show stopper for me, I preferred the nice price over that but your priorities may be different.

Having chosen a number of models, look at the hardware that equips them: driver support of the type and chipset for wifi access is a frequent source of questions in the forums as is 3D acceleration for the graphics card. Choose the combination that is best supported unless you feel adventurous.

You can look at other users' experience here: [https://wiki.ubuntu.com/HardwareSupportMachinesLaptops](https://wiki.ubuntu.com/HardwareSupportMachinesLaptops)

Choose your tools also. I use the gtkwifi applet for wifi connection management, I like it, but there are others.

In general fancy power management (ACPI) features -- like suspend to ram, graceful wakeup from hibernation -- need fiddling with, unless you can find pointers for your model of laptop. There are plenty in the wiki.

Edit: oh yeah, this laptop cost &#8364;1000 = approx $1200.

GL

---

### Post by ForsBrunn on 2006-02-28
I have an HP NX8220 with Intels Centrino in it which is supported out of the box with ipw2200.
The only thing I  had to fiddle with was WPA, WEP and unencrypted wifi was supported during installation already.

This laptop did cost €1500 in sweden but depending on equipment ( RAM, CPU speed, harddisk size etc. ),  I have seen it for about €800 here.
 
/JZ

---

### Post by jetwash on 2006-02-28
yeah so does my oldish dell 500m, works straight out of the box.. although it didn't actually correctly detected the network during installation, all i needed to do was put in the correct network name and wep key..

and that's why i use ubuntu too.. trying fedora (old one) last year was a disappointing experience

---

### Post by MJSOnline on 2006-02-28
[QUOTE=jetwash]yeah so does my oldish dell 500m, works straight out of the box.. although it didn't actually correctly detected the network during installation, all i needed to do was put in the correct network name and wep key..

and that's why i use ubuntu too.. trying fedora (old one) last year was a disappointing experience[/QUOTE]

What brand and model is yoiur laptop then?  I ask as I am looking at using my base unit, running Ubuntu 5.10 now, as a server and getting laptop to control it and use it as a downloading and surfing laptop by saving it all to the server. M

---

### Post by jbennett on 2006-02-28
I installed Breezy on my Dell Inspiron 600m about two weeks ago and everything was working right away.  Ubuntu detected both of my NICs and let me choose which one to connect with during install.  

The only thing I've noticed that I miss (and haven't had a chance to mess with yet) is the fact that running my finger down the side of my trackpad doesn't scroll a page down.  But I'm sure if I messed with it for a few minutes that I could figure it out and have it working.  

This laptop (Intel Pentium M, 2 Ghz, 80 GB hd, 1 GB RAM, Integrated wireless, integrated sound card and video card) cost approximately $1200, and I'm sure now you could get even a few more features for the same price, since its been about 8 months since I bought this one.

Hope that helps.  Good luck in your quest for the perfect laptop.:)

---

### Post by facefur on 2006-02-28
I did a straight Breezy installation on my IBM T43 laptop, and the wireless capability worked "out of the box" without a hitch - in fact, just about everything workes without a problem.

---

