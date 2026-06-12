---
title: "Speed man, I need more ..."
date: 2006-03-17
forum: General Help
---

### Post by wannabelinuxconvert on 2006-03-17
I've just built a system out of some old bits I had laying around but I seem to have some speed issues when it comes to the graphics side of things ...

Specs of new system 

Pentium III 733mhz
384mb SDRAM
30gb Maxtor HD
Matrox G200 8mb Graphics card

I actually bought the graphics card off of Ebay for a few quid as the mobo I have has onboard intel graphics but it won't display above 1024x768.

I have downloaded the latest drivers from the Matrox website and reconfigured X but I seem still to have some problems.

The screen redraw is not overly that quick and also when running glxgears, the gears start off real nice and smooth and fast for about five seconds and then almost grind too a halt.

Is there anyway to get more speed out of this card/desktop !?

Mic

---

### Post by atomicmoose on 2006-03-17
Your hardware is starting show it's age. The PIII 733 is probably fine for Linux, depending on what you want to do, but the Video Card is going to be a choking point. An 8MB card is extremely outdated, and is the reason for your choppy video.

---

### Post by bugmenot on 2006-03-19
Since you left out the part.....

Have you recompiled the kernel you are using?

Have you changed the kernel scheduler to pre-empt?

Is it using the graphics card or the on-board AGP?

.I always compared my usage experience to WinXP

I was kinda fedup with WinXP being more responsive.

Then just one change of scheduler to pre-empt and 
now its much more responsive

I swear, every desktop linux user should change the 
kernel scheduler to pre-empt
......the increase in performance will bring tears to your eyes

And ther's a Frick'in N'Curses GUI for configuring the kernel options
There is no reason not to do it.

Since The processor is kinda old...

I figured tweaking it for all its worth is the only way........

and thats all i had to say

Oh and is your resolution greater than 1024x768 16 bit or 24 bit or 32 bit
colors??

---

### Post by wannabelinuxconvert on 2006-03-19
Hi,

Could you give me a quick how-to to do this pre-empt thing !?

What actually does it do !?

Also, the screen res is 1280*1024 24bit @ 60 refresh rate.

The Matrox card is PCI as the on board Intel card wouldn't display above 1024*768.

Mic

---

### Post by taurus on 2006-03-19
Get some nice nVidia cards for less than $50!!!

---

### Post by wannabelinuxconvert on 2006-03-19
Its not that easy to find a decent PCI card ... thats why I ended up buying the Matrox

---

### Post by taurus on 2006-03-19
[QUOTE=wannabelinuxconvert]Its not that easy to find a decent PCI card ... thats why I ended up buying the Matrox[/QUOTE]
[http://www.newegg.com/Product/ProductList.asp?Brand=1402&N=2000380048+1305520548+4025+50001402&Submit=ENE&Manufactory=1402&SubCategory=48](http://www.newegg.com/Product/ProductList.asp?Brand=1402&N=2000380048+1305520548+4025+50001402&Submit=ENE&Manufactory=1402&SubCategory=48)

:rolleyes:

---

### Post by jerrykenny on 2006-03-19
Change your default color depth to 16 from 24 (might help a wee bit)

Issue the commands

sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.good
sudo gedit /etc/X11/xorg.conf

scroll thru the file untill you get to the default depth, change that to 16.

Also make sure you've got the latest kernel, and you might benefit from switching to the i686 kernel (instead of default i386)

When you're at the install stage . . . . assuming you're using ext 3   check the noatime option for the filesystem . . . . or notail for reiserfs . . .

---

### Post by NeghVar on 2006-03-19
Id drop your resolution back to 1024x768. running at 1280x1024 is probably taxing your vid card there.

---

### Post by wannabelinuxconvert on 2006-03-20
I'm curious about the linux-686 kernel !?

What's the difference between this one and the default 386 one !?

Is it easy to upgrade !?

---

### Post by jerrykenny on 2006-03-20
686 kernel is just optimised for pentium 3 and 4's , very easy to install, just start synaptic and go to the "base" section . . . . .

---

### Post by virgule on 2006-03-20
[QUOTE=bugmenot]
(...)
Then just one change of scheduler to pre-empt and 
now its much more responsive

I swear, every desktop linux user should change the 
kernel scheduler to pre-empt
......the increase in performance will bring tears to your eyes
[/QUOTE]
Excuse me but where you got 'pre-empt' from? I only have **noop**, **anticipatory**, **deadline** and **cfq** in here. Default Setting is anticipatory so I switched to cfq and it is actually much more responsive and quicker.. but just what is 'pre-empt' and where did you get this from? Perhaps we have different arch. Maybe I am off the boat with 'my' scheduler? I would appreciate if you would light my way.
```

]# cat /sys/block/hdc/queue/scheduler
noop anticipatory deadline [cfq]

```

---

### Post by Patrick-Ruff on 2006-03-20
yeah man I'de be interested to hear that pre-empt stuff to. seems hela cool. I'de liek to make my Ubuntu laptop faster then it already is (in comparison to Windows). it seems a bit slow at times, however, I think I just thought of a great idea for the community to build, an 'optomization kit' for Ubuntu, Kubuntu, Edubuntu, Xubuntu and all them. (mainly ubuntu) wouldn't that be tight? you know like special tools to automaticly optoimze it or make it easy for the end user to optomize his/her system. good idea? bad idea?

---

### Post by Patrick-Ruff on 2006-03-20
any answers yet?

---

