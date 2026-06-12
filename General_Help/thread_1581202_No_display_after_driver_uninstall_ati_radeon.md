---
title: "No display after driver uninstall ati radeon"
date: 2010-09-24
forum: General Help
---

### Post by disflipgotsgame on 2010-09-24
BACKGROUND INFO
So I have a NEW computer problem.. lol.  The last few weeks I have been dual monitoring from my lcd monitor to my hdtv.  LCD was connected via vga and my tv via hdmi.  To my knowledge, my pc has two graphic cards, both ATI Radeons.  One I believe is on the mother board, ATI Radeon 4200HD series, and the other is in a PCI slot ATI Radeon 5600HD series.  I THINK that when I had it dual monitored the tv was connected via 4200HD and LCD via 5600HD (could be wrong).

WHAT I DID
Everything was working fine (i was mainly just using the HDTV as my only monitor and main monitor).  As you can guess I was gaming on the hdtv, but I was not satisfied with the slight lag I felt.  So I looked at forums to see what I could do and they mostly said 1)  change settings on tv to game mode, 2) turn off vsync on your graphics card.  

So I did #1, but when I tried to do #2 I could not open my graphics cards “menu” aka CCC aka Catalyst Command Center.  So I read up on why this might happen and they said I should uninstall drivers and reinstall the drivers, so I did this as well (with most current drivers from the AMD site, version 10.9) and still I could not get into the CCC.  As I was reading more forums, they were saying the 10.8 version mainly has this problem.  So what I did was I downloaded 10.7 (did not install yet) and uninstalled the new 10.9.  

When I went to reboot the cpu after the uninstall of 10.9 there was no display on my HDTV.  I figured I just need to go back to my LCD which was still hooked up to my cpu.  No display there as well.  I tried dvi and vga hook ups from the monitor to both graphic cards but nothing worked to get me a display.  I also tried my girlfriends monitor, which only has vga, to both graphics card and still nothing worked.  So at this point I have NO display.

After about an hour of trying different combinations of cords, monitors, plugs, tv’s ect, I RANDOMLY somehow got a display with my  girlfriends monitor vga to the 5600 card (I think).  I had to hold the vga cord a certain way on attached to the monitor in order for the display to work.  So since I had a display, I quickly installed 10.7.  After installation, it did not prompt me to reboot (which I thought was weird) so I just went to properties and tried to change the resolution to the max 1600x something, to see how it looks.  The screen went blank and the display never reappeared. 

Now I basically have NO DISPLAY again.  After another hour of playing with cords, monitors, etc, I decided to just go to bed and try not to throw the computer and monitors across the room at some of my girlfriends cats.  

Any suggestions? I have been reading forums, some say it might be hardware, but in my case everything is new (within 5 months old).  Some talk about a reset on my motherboard, but I don’t know how to do it without a display.

---

### Post by robsoles on 2010-09-25
Welcome to UF.

While looking at the black display you should be able to access terminal by pressing [CTRL]+[ALT]+[F1] or, alternatively, boot from the LiveCD. If booting from the LiveCD then choose 'try ubuntu...' and use the GUI to mount your file-system for you, it should be under 'places'

If in terminal booted from the PC in question you can issue the following command
```
sudo 'mv /etc/X11/xorg.conf /etc/X11/xorg.conf-not-working-20100925
```Which will move your current settings out of the way. Exit terminal and restart the machine, let us know if you need help from where you find yourself on restart.

If in GUI/Desktop from LiveCD you can get file-browser as root so open the 'Applications->Accessories-Terminal' and type in```
gksudo nautilus
``` then you should be able to navigate using file-browser to /media/-pick-a-string-of-hex- (-pick-a-string-of-hex- will likely be a weird number including letters up to F) and find /etc/X11/xorg.conf in that partition/file-space.

Rename, or move, xorg.conf out of the way and your system has a good chance to reboot to an operable desktop using defaults and you can have another go at choosing a resolution. :)
[COLOR=Red]
Please be careful with the file-browser that opens with the command I gave you, when you close that window you can press [CTRL]+[C] in terminal to exit the command if it doesn't release the prompt.[/COLOR]

How does that work out for you?

---

