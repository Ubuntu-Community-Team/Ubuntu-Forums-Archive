---
title: "help me to config gfx and monitor properly"
date: 2010-03-25
forum: General Help
---

### Post by Wesley on 2010-03-25
hi guys

spec of my machine -

intel i5
gigabyte P5M UD2
4GB DRR3
64GB SSD
ATI sapphire 5850 1GB pci-e
Viewsonic VX2260wm 22"

install ed ubuntu 9.10 went fine, fully updated and activated the ATI/AMD proprietary FGLRX driver. restarted ubuntu. 

now it's dsiplaying at 1920x1080 but shrink down with black border around if you know what i mean? 

also got horrible "steaming" lines from top to down. hard to explain. also got this horrible massive ATI watermark logo at bottom/left of screen.

i tried the new ubuntu 10.04 beta LIVE CD, it detected the graphic card and monitor PERFECTLY. but not the ubuntu 9.10.

can anyone help me please?

big many thanks

wesley :)

edit: my monitor is [http://www.viewsonic.com/products/desktop-monitors/lcd/x-series/vx2260wm.htm](http://www.viewsonic.com/products/desktop-monitors/lcd/x-series/vx2260wm.htm)
      my graphic card is [http://www.overclockers.co.uk/showproduct.php?prodid=GX-215-SP&groupid=701&catid=56&subcat=411](http://www.overclockers.co.uk/showproduct.php?prodid=GX-215-SP&groupid=701&catid=56&subcat=411)

---

### Post by Wesley on 2010-03-25
i got the feeling it's something do with the frequency?

copy/paste from viewsonic spec site 

>  Frequency  	Fh: 24-83kHz, Fv: 50-76Hz

---

### Post by Wesley on 2010-03-26
anyone? :(

---

### Post by Wesley on 2010-03-27
somebody know how???

---

### Post by Wesley on 2010-03-30
anyone?

---

### Post by Mark Phelps on 2010-03-30
Been a while since I've used the ATI proprietary drivers since I have no $$ to go out and buy a new graphics card simply because ATI dropped Linux support for my card a year ago ...

But, I used ATI drivers for several years and never got the display problem you mention -- or the watermark!

You saying you got these installed simply by choosing hardware drivers?

I would suspect they are corrupt in some way and would either go directly to the AMD site to get the drivers, or would install envyNG and use it to remove and reinstall the drivers.

IF you want, you can read the text in the link below about REMOVING the ATI drivers (don't bother with the xorg.conf stuff) and seeing if your display is then OK with the open source drivers:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by Wesley on 2010-03-31
hi

thanks for the reply

i downloaded the ATI driver from ATI website. 

file name is :

> ati-driver-installer-10-3-x86.x86_64.run

how to install this?

cheers again

wesley

---

### Post by Wesley on 2010-03-31
YES!!!!

i used this method [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

work perfect!!! very happy lol

thanks :)

---

