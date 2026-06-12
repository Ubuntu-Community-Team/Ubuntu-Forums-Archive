---
title: "Screen out of range"
date: 2011-05-21
forum: General Help
---

### Post by Zurfy on 2011-05-21
My screen is always telling me "signal out of range. 75.0 KHz / 60 Hz when I have my graphic card driver installed.

I have tried many ways to solve that problem and I have been tried many things that I read in many tutorials...
I don't know how to solve that and I've been trying new things for nearly 2 weeks.
I have tried the same thimgs in ubuntu 10.10, 9.10 and 9.04 but with no results.

Can you try to help me please?
By the way, I have ATI graphic card.

I have ubuntu 10.04 now.

---

### Post by linuxinstalledfromhdd on 2011-05-21
ATI graphics cards are notoriously difficult to get configured just right in Ubuntu.  Can you swap out the card with something that isn't ATI?

---

### Post by Zurfy on 2011-05-21
I only have that graphic card (ATI).

Should of change of distribution then?

---

### Post by wildmanne39 on 2011-05-21
> **Zurfy said:**
> I only have that graphic card (ATI).

Should of change of distribution then?

Hi, I have that problem with my nvidia card, it is something with natty, I have had a nvidia card for the last for years in three different computers and this is the only time it has been a problem. I modified my xserver file and the card is read right by my nvidia configuration manager but it is still wrong in the display settings of nattty so I get an error message when booting I can not see the screen and it adds about a minute to boot time.

---

### Post by Zurfy on 2011-05-22
And is there anything I can do to solve the problem.

---

### Post by dandnsmith on 2011-05-22
I've used 3 or 4 different ATI cards (at the very least) with ubuntu of different releases without any problem with CRT and widescreen LCD monitors (without special manufacturers drivers). I've used, recently, 8.04,9.10 and 10.04.

Have you actually tried a standard install without adding ATI drivers?

HTH

---

### Post by Kschikan on 2011-05-22
The "Out of Range" errors are usually from your monitor not being able to process what your graphics card is putting out. If you get the specs for your monitor online, you can see whether it's the horizontal sync or the vertical sync that's having issues.

If you'd like to try and reconfigure the X screen manager (which handles your graphics), there's a decent tutorial below:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by randomreuben on 2011-05-24
I have the same problem as described by Zurfy, but I can't even get to the login screen before I get the error saying that it's out of range.  It gets to the out of range error immediately after starting.  Please help.

---

### Post by Zurfy on 2011-05-24
> **dandnsmith said:**
> I've used 3 or 4 different ATI cards (at the very least) with ubuntu of different releases without any problem with CRT and widescreen LCD monitors (without special manufacturers drivers). I've used, recently, 8.04,9.10 and 10.04.

Have you actually tried a standard install without adding ATI drivers?

HTH

yea. If I don't have the ATI drivers installed there's no problem then. But I need them.

---

### Post by Kschikan on 2011-05-24
randomReuben: if you can get to the tty terminal (press CTRL+ALT+F1) you can change your monitor size from there, hopefully to something your monitor can display. To get back to the graphical environment after changing that, use CTRL+ALT+F7 (F2-F6 are other tty terminals).

to change your resolution from the screen:

```
xrandr -a
```
The above lets you see what resolutions you have available

```
xrandr -s <size>
```
The above lets you switch to the given size

---

### Post by randomreuben on 2011-05-25
Thanks for the tip, but I ended up reinstalling out of frustration.  If I don't install the ATI driver, everything works fine.  Thank you again for your suggestion.  I'm sorry I didn't get to try it.

---

