---
title: "flgrx catalyst control centre 2.6 no dual monitor - 1.8 has dual monitor"
date: 2009-07-31
forum: General Help
---

### Post by charonred on 2009-07-31
I'm running Hardy 8.04.3 (32bit) as my main OS with ATI catalyst control centre 1.8 (restricted fglrx) and it supports my graphics card and dual Samsung monitors with display as one large desktop, and indentifies both monitors 1 & 2
(system is as per my signature below)

As I've installed Jaunty 9.04 on several friends PCs, I thought I'd try it on my PC on another drive, mainly because it boots in almost half the time and generally has better/updated support for many things. 

However, with Jaunty it has the ATI CCC ver 2.6 (restricted fglrx) and it won't display as one large desktop, the options are 'greyed' out (see attached images - 1st two images are for 8.04.3 with the 2nd two being for 9.04) and it only identifies monitor 1 (both monitors run, but only display the same desktop).

Can I replace the fglrx CCC ver 2.6 with 1.8, and if so how would I do that.?

---

### Post by MaxIBoy on 2009-07-31
Have you tried running the program with root access? Because I know part of the control center just acts as a front-end for modifying /etc/X11/xorg.conf in a graphical way, and that file is protected from modification by ordinary users. 

Run the command "gksudo amdcccle" in the terminal, type in your password as normal, see if it works that way.

---

### Post by charonred on 2009-07-31
rebooted and tried that, but it seemed to spit the dummy (see attached)

---

### Post by MaxIBoy on 2009-07-31
Okay, that's quite odd, and seems to suggest that the graphics drivers aren't installed fully or something.


Can you confirm that you have full 3D acceleration? (More than Compiz, try firing up a 3D game.)

---

### Post by charonred on 2009-07-31
what 3D games are available to run ?

I haven't installed much apart from base 9.04 install, then activated restricted drivers (flgrx), installed  Jaunty updates, installed compiz settings manager, then rebooted.

I just set desktops to 4 and enabled desktop cube, rotate and reflection/deformation - that works ok.

---

### Post by khelben1979 on 2009-07-31
> **charonred said:**
> what 3D games are available to run ?

You can try Doom 3 demo version from ID software..

---

### Post by charonred on 2009-07-31
demo download is redirected to Activision site which takes forever to not load.

I'll try again later, for now I have to go back to Hardy as my business and emails run from there.

---

### Post by charonred on 2009-07-31
Thought I'd try a couple of things to identify where the problem lies as such;

1st I booted from a live 9.04 'Jaunty' CD - goes through Grub, then to Ubuntu splash with the 'progress bar' (both monitors are displaying same content); but when it finishes the progress bar, monitor 2 stops displaying. System continues to coloured splash background on monitor 1 only, then loads desktop. When I shut down, monitor 2 starts displaying the same shut-down splash as monitor 1.


I then tried the same with 8.04 'Hardy' live CD - goes through same boot/loading procedure all the way to desktop with both monitors displaying same content all the time.

Then I booted from 8.0.2 'Hardy' live CD (Feb '09 disc)- goes through same boot/loading procedure all the way to desktop with both monitors displaying same content all the time.

Then I booted from 8.10 'Intrepid' live CD - goes through same boot/loading procedure all the way to desktop with both monitors displaying same content all the time.

So it appears to handle monitors 1 & 2 in Ubuntu 8.04, 8.04.2 & 8.10 from live CDs.

The problem occurs only with 9.04

Out of curiosity I tried Kubuntu 9.04; got the same result as Ubuntu 9.04, the only difference was  once loaded it detected both monitors in desktop notification area of top panel (see image), but obviously I couldn't enable desktop effects to test the one large desktop effect (see image).

Again out of curiosity, I booted back to the installed 9.04 and added the KDE packages. When I rebooted and logged into KDE session; when I went to the display settings, it showed both monitors as CRTs ?? couldn't get screenshot, as KDE started alternating between non-responsive desktop, and a black screen with just a cursor on it (this went on for several minutes before I reset PC)

So seems to be a bug with 9.04, so until that's fixed, looks like I have to stay with 8.04 - which is a shame because 9.04 boots faster, gives me more printer control options on Epson R310 (cd hub size etc), detects my Lexmark e230 properly, and my Epson CX5300 actually started working again (needs new cartridges though).

One other thing I'll try; when I built the system I used a Asus EAH2600 Pro graphics card (512MB with 2 x DVI outputs), which I only recently replaced with an Asus EAH3450 (512MB with 1 x VGA, 1 x DVI outputs); I'll reinstall the HD2600 later today and see if that is detected properly - for now, it's a sunny winter's day, too nice to stay inside, so after lunch I'm going for a ride on my other toy TL1000S :D
.

---

### Post by MaxIBoy on 2009-08-01
Okay, I think I realized your problem.

Here is what you should try doing:
```
sudo aticonfig --initial=dual-head
```

---

### Post by charonred on 2009-08-01
thanks, thought I'd check just before I go out

did that,rebooted - got both displays being detected and identified, but still no large desktop option

---

### Post by MaxIBoy on 2009-08-01
I was able to do this for a while, but keep in mind that COMPIZ WILL NOT WORK IF YOU DO THIS!


[LIST]
[*]Edit /etc/X11/xorg.conf.
[*]In the "serverlayout" section, add a line at the end with this code:
```
Option     "Xinerama"     "true"
```
[/LIST]

This will enable Xinerama and give you a big desktop mode. However, it's a sub-optimal solution because Xinerama is depreciated (kept around for legacy reasons,) and it results in RANDR being disabled. A lot or programs complain about RANDR being disabled, although the complaints are mostly harmless. However, FGLRX is incapable of enabling both Xinerama and Composite at the same time. An advantage to Xinerama though, is that even if the two monitors aren't the same size, windows are still the same "scale" on both displays.

With Catalyst 9.7, the control center started working properly for me and I was able to enable big desktop mode without Xinerama. Although now when I drag windows over to my square screen, they look "too tall." Still worth it for Compiz, in my opinion.

---

### Post by charonred on 2009-08-01
Thanks again MaxIBoy, think I'll stick with Compiz though, is Catalyst 9.7 available via Synaptic?

I'll get to this at other end of the day, it's early morning here in West Australia, and I'm getting ready for regular Sunday country ride with the Armadale [Ulysses Club]("http://www.ulyssesclub.org/") - clear blue skies in middle of winter (can't ask for more).

---

### Post by MaxIBoy on 2009-08-01
No, it is not as of right now. Certainly it will never make it into the Ubuntu 9.04 repositories, since Ubuntu 9.04 is already released, but I think it will probably be in 9.10 soon.

You can install it following these directions:
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually) 
The guide claims to be written for Catalyst 9.6 but it works for 9.7 as well. Just make sure you download the right version!

---

### Post by charonred on 2009-08-05
Thanks; I finally got round to doing all those terminal scripts, and have Catalyst 9.7 installed (also had to run that 'dual head' script again)

Unfortunately it's still not right; can't rearrange my desktop display positions from 1-2 to 2-1 (to match actual monitors), and 'Multi Display' options only offers 'Single (Independent display) 

maybe I'll go back and try the EAH2600 Pro card instead, but not today.

---

