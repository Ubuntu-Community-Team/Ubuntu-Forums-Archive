---
title: "ATI drivers"
date: 2010-06-04
forum: General Help
---

### Post by YigalB on 2010-06-04
I have ATI RV535 (Radeon X1650 series) (rev 9e).
How do I know if Ubuntu is using the specific drivers for that card?
Where can I see each HW device and the driver being used for?

---

### Post by Guy Sibley on 2010-06-04
it should be in system hardware drivers.  you need fglrx **Driver **that should enable the card and your higer speed graphics.  I hope that was helpful.

---

### Post by YigalB on 2010-06-04
> **Guy Sibley said:**
> it should be in system hardware drivers.  you need fglrx **Driver **that should enable the card and your higer speed graphics.  I hope that was helpful.
Thanks - how do I check that?

---

### Post by Mark Phelps on 2010-06-04
> **Guy Sibley said:**
> it should be in system hardware drivers.  you need fglrx **Driver **that should enable the card and your higer speed graphics.  I hope that was helpful.

ATI/AMD dropped fglrx support for this card over a year ago.  There are NO flgrx drivers that will work with this card and recent Ubuntu versions.  Downloading and forcing a fglrx driver install will only corrupt the display and force booting into console mode to remove the drivers.

Since you don't know what you're talking about -- please don't provide bad advice!!

The open source drivers are the only ones that will work now -- and they are installed by default.

---

### Post by quadproc on 2010-06-04
> **YigalB said:**
> I have ATI RV535 (Radeon X1650 series) (rev 9e).
As another poster has noted, your card is considered to be legacy.  There are no current ATI drivers for it.  However, you might be able to use it if you use an Ubuntu releae that is old enough, and if you can get a copy of an old enough ATI driver.   I think that ATI's version 9.3 driver is still available.
> How do I know if Ubuntu is using the specific drivers for that card?
If your system has the file /etc/X11/xorg.conf then look in it to see what driver is specified.  You can see that by typing this into a terminal:
```
grep "river" < /etc/X11/xorg.conf
```Look for a non-commented line which says driver.  The ATI proprietary driver is called fglrx.  You may also find "ati" which is a wrapper that attempts to figure out an open source driver appropriate for your card, or "radeon" which is an open source driver.  You might even see "vesa" which is a very simple, old, and robust driver but it doesn't do anything interesting.[quote]
Where can I see each HW device and the driver being used for?You can get some idea of things going on in your system by typing 
```
modprobe -l
```but I don't think that this is what you are after.

quadproc

---

### Post by YigalB on 2010-06-05
[QUOTE
If your system has the file /etc/X11/xorg.conf then look in it to see what driver is specified.  You can see that by typing this into a terminal:
```
grep "river" < /etc/X11/xorg.conf
```[/QUOTE]

I don't have this "xorg.conf" file.

Does it mean I have to spend money and buy new VGA card every time Ubuntu is releasing new update? Looks like the microsoft way. This card is good enough for me. Even too much for my needs (just a side server - most of the time I login remotely). My PC has no PCIe socket, so it seems I will need to buy a new PC....
This card is not that old.

---

### Post by jocko on 2010-06-05
> **YigalB said:**
> I have ATI RV535 (Radeon X1650 series) (rev 9e).
How do I know if Ubuntu is using the specific drivers for that card?
Do you get your monitor's native resolution? Then you most likely have the correct driver (= the open source driver named "radeon").
To check which driver is in use, just have a look in your /var/log/Xorg.0.log.
If there are a bunch of lines starting with something like "(**) RADEON(0): ...", you have the radeon driver, which is the only driver you can use with that card.
If there instead are lines starting with "(**) VESA(0): ...", you use the fail-safe vesa driver which is not a very good driver if you want high resolution and hardware acceleration.

> **YigalB said:**
> Where can I see each HW device and the driver being used for?
lshw will tell you all you want to know and more.
To get a nicely formatted html-file with all your hardware, run this in a terminal:
```
sudo lshw -html > ~/hardware.html
```
The file will end up in your home directory, and should be readable in any web browser.

---

### Post by Mark Phelps on 2010-06-05
[/QUOTE] Does it mean I have to spend money and buy new VGA card every time Ubuntu is releasing new update? Looks like the microsoft way. This card is good enough for me. Even too much for my needs (just a side server - most of the time I login remotely). My PC has no PCIe socket, so it seems I will need to buy a new PC....
This card is not that old.[/QUOTE]

Welcome to the world of Linux -- where very few manufacturers provide Linux-specific drivers for the hardware they sell, whereas they nearly ALL provide MS Windows drivers.

The card WILL work, only with the open source drivers, and provides good 2D support but very little hardware acceleration.

That said, I have the same X1650 running with the open source drivers and it works just fine -- can get all the special video effects with no problems -- and that's using the open source drivers.

But then, I have not made the mistake of upgrading to 10.04.  I'm staying with 9.10 for now because everything works with no problems, including the open source drivers.

And, no, you do NOT need to run out and buy a new video card; quite the opposite. If you read through the video subforum, you'll see post after post from folks who are running the latest ATI video cards and have nothing but problems.

But you DO have to live with the limitations of using the open source video drivers -- if you're using one of the ATI "legacy" cards (which you are).

---

### Post by jocko on 2010-06-05
> **YigalB said:**
> Does it mean I have to spend money and buy new VGA card every time Ubuntu is releasing new update?
No. The open source driver is still working, and it keeps getting better with every release.


> **YigalB said:**
> Looks like the microsoft way.
How is this "the microsoft way"? Ubuntu still works with your card, and there is NOTHING you need to do to get the proper driver working (it is already working). And it's in no way ubuntu's (or canonical's) fault that ATI abandoned their closed source support for their older cards.

> **YigalB said:**
> This card is good enough for me. Even too much for my needs (just a side server - most of the time I login remotely). My PC has no PCIe socket, so it seems I will need to buy a new PC....
This card is not that old.If it's good enough, why would you need to change it? And if you don't really need to get the maximum performance from your card, the open source driver is probably good enough...

---

### Post by YigalB on 2010-06-05
> **jocko said:**
> No. You the open source driver is still working, and it keeps getting better with every release.

I have stripes on the screen - not easy to work with. 
Also, I cant use the graphic features because it slows down the PC.
I assume is that the driver is using the CPU and not the GPU.

---

