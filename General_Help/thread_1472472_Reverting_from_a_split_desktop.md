---
title: "Reverting from a split desktop"
date: 2010-05-04
forum: General Help
---

### Post by infracom on 2010-05-04
I'm fairly new to Ubuntu. I had a bit of a problem after setting up a split desktop over two monitors yesterday. Setting up the split desktop was very easy, getting rid of it was the issue.
 
One of my computers (call it Longshot) dual boots between Ubuntu Lucid and Windows Vista. Longshot is attached to two monitors, a Dell (monitor A) and an HP (monitor B). Each monitor can use either a VGA or a DVI connection. Monitor B is also normally used as a monitor for a Windows 2000 machine (call it Wolverine). So monitor B is attached as VGA to Wolverine and DVI to Longshot. This works well and for most of the time I use monitor A on Longshot and monitor B on Wolverine. 
 
Occasionally I use both monitors for Longshot using a split desktop. Yesterday in Ubuntu I setup a split desktop with A and B as side by side monitors, A was on the left. Ubuntu put its menu bar at the top of monitor B and I had a few icons on the 
desktop of monitor A but no menu bar. After I had finished what I was doing I rebooted Longshot into Vista and worked on Longshot using monitor A only. 
 
Today I was using monitor B for Wolverine. I rebooted Longshot into Ubuntu. Because the desktop had been split over two monitors and monitor B was not available to Ubunto I did not have access to the toolbar to use only monitor A for Longshot. I 
expected to be able to do something like right mouse click on the desktop on A to stop using a split desktop but it seems this is not an option. I had to switch monitor B manually from VGA connected Wolverine to DVI connected Longshot so I could revert from split desktop using it, then manually switch off DVI conection to be able to continue using Wolverine. 
 
OK this was only slightly inconvenient, but what if I had physically removed monitor B or I had not known how to switch between VGA and DVI modes on the monitor. Is there some **easy** way to revert to a single from a split desktop if the toolbar containing the system menu is not on the monitor?

---

### Post by infracom on 2010-05-05
Maybe my first post was too long.  Does anyone know if there is a command line command to set:

[B]system->preferences->monitors->same image in all monitors
[/B]
This should do what is needed.

---

### Post by infracom on 2010-05-05
I'm doing a lot of talking to myself. But if anyone else is interested, the command to do almost what I want seems to be   [B]

gnome-display-properties[/B]

I found this by going to "system->preferences->monitors", right-mouse-click, "add this launcher to desktop" and looking at the properties of the added launcher.

---

