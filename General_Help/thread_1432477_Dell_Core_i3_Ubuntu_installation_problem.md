---
title: "Dell Core i3 Ubuntu installation problem"
date: 2010-03-17
forum: General Help
---

### Post by MiguelBarrios on 2010-03-17
Hi there:

I've been trying to install Ubuntu in a Dell laptop, Inspiron, with  Intel Core i3, that is running in Windows 7 rigth now. I burn the .iso image (twice) and put the Cd in. Then restart it, and... nothing.

Off curse, I run F12 then, and run the CD. This time I get the introduction panel, pick up a language and try to run it whitout installig -to search for any problems- and... nothing. It kinds of start, but then I get a black screen (not black like "turn-of black" but like "loading black"), eventually I get the start music, that's why I suppose that it may be a screen conection problem.

Well, the same thing happens when I choose the "Install" option, and even when I try to install it in Windows like a program.

Anyone has an idea?

I will be most gratefull if someone give me a clue.

Thanks a lot;

Miguel Barrios

---

### Post by blueridgedog on 2010-03-17
I appears that Ubuntu is loading (the start sound), but it can't load the display driver.  Do you know the make and model of the graphics card?

---

### Post by MiguelBarrios on 2010-03-17
Well, it's all Dell factory production.

So, the graphics card must be an Intel HD Graphics.

Thanks for taking interest.

Hope it helps...

Miguel Barrios

---

### Post by blueridgedog on 2010-03-18
What version of Ubuntu?

I suggest you try the alternative (non-graphical) install disk.

I am not a display driver guru - you may get help here, but you may also want to post in the laptop specific forum.

---

### Post by pinco pallino on 2010-03-18
Hi, I have the same problem with the intel HD graphics (I have an HP laptop), and I move around the installation problem choosing the "safe graphics" option: after the boot from the installation CD when the ubuntu logo appears with the principal options, type F4 and choose safe graphics option.
I installed the system, but with the pour VGA graphics...:(

I looking for someone who face the problem of the driver for the intel HD graphics card...

ciao
andrea

---

### Post by wrose51106 on 2010-03-18
The new Core i3 CPU's have integrated graphics built right in. I believe you will need to wait for a new kernel, 2.6.33 for updated driver support.

Currently under 9.10 we are sitting at 2.6.31. Last I heard 10.4 will be shipping with 2.6.32 since this is a LTS release. You could always download the beta and give it a whirl :D

-Bill

---

### Post by kaibob on 2010-03-18
> **MiguelBarrios said:**
> Well, it's all Dell factory production.

So, the graphics card must be an Intel HD Graphics.

Thanks for taking interest.

Hope it helps...

Miguel Barrios

There are a lot of threads in the Lucid Lynx forum on i3 and i5 machines with integrated HD graphics, and a number of users have gotten their computers working satisfactorily. So, you may want to try the Lucid beta or have a look at the Lucid Lynx forum.

---

### Post by pinco pallino on 2010-03-18
I fixed the graphics problem replacing vesa with intel in 
[FONT="Courier New"]/etc/X11/xorg.conf[/FONT] 
as suggested in a post that I read somewhere in this forum and that now I cannot find to quote.

[FONT="Courier New"]Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
EndSection[/FONT]

instead of

[FONT="Courier New"]Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection[/FONT]

ciao
andrea

---

### Post by ntitdost on 2010-04-06
I have Toshiba L500, core i3 and 4G DDR3. The issue is such as yours. After insert Ubuntu 9.10 64 bits cd, (I have checked with both Cd and USB), we only choose language and then nothing return. Now, waiting for Ubuntu 10.04 release. Does anyone use 10.04 beta version for core i3,i5,i7 model?

---

### Post by joesnr on 2010-04-11
There is a similar thread at: [http://swiss.ubuntuforums.org/showthread.php?p=9075779](http://swiss.ubuntuforums.org/showthread.php?p=9075779) where the problem is apparently solved with beta1 of 10.04 but note beta2 has since been released.

---

### Post by akashgupta0307 on 2010-08-15
f

---

### Post by swaraj_de on 2011-03-13
[SIZE=3]This is not graphics driver problem.
Choose proper kernel distribution

Check the link below
[http://dimaspriyanto.com/2010/06/02/installing-ubuntu-on-intel-core-i3-processor/):P]("http://dimaspriyanto.com/2010/06/02/installing-ubuntu-on-intel-core-i3-processor/%29:P")
[/SIZE]

---

### Post by bkratz on 2011-03-13
How appropriate--an old thread to a "dead" link!!

---

### Post by swaraj_de on 2011-03-13
[quote=swaraj_de;10555208][SIZE=3]this is not graphics driver problem.
Choose proper kernel distribution

check the link below
[http://dimaspriyanto.com/2010/06/02/installing-ubuntu-on-intel-core-i3-processor/]("http://dimaspriyanto.com/2010/06/02/installing-ubuntu-on-intel-core-i3-processor/%29:p")[/SIZE]

---

### Post by bkratz on 2011-03-13
> **swaraj_de said:**
> [quote=swaraj_de;10555208][SIZE=3]this is not graphics driver problem.
Choose proper kernel distribution

check the link below
[http://dimaspriyanto.com/2010/06/02/installing-ubuntu-on-intel-core-i3-processor/]("http://dimaspriyanto.com/2010/06/02/installing-ubuntu-on-intel-core-i3-processor/%29:p")[/SIZE]



I get this for the link

Error 404
404 Error: The page you are looking for can't be found. Sorry!

There could be a few different reasons for this:

---

