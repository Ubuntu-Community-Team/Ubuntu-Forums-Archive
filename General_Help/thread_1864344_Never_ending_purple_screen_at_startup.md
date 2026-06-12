---
title: "Never ending purple screen at startup"
date: 2011-10-18
forum: General Help
---

### Post by closingBrace on 2011-10-18
Hi guys, 

Sometime (not really often), my laptop shows me the purple screen for a very long while. In fact, I suspect an infinite loop (but it can be something else). Let's see...

Here are the relevant technical details :
 
My laptop is a Dell Studio 1558 with the following technical specs :
 
[LIST]
[*]4 Core i3 M 330 @ 2.13 GHz
[*]6 GB of RAM
[*]500 GB Hard drive (ST9500420AS)
[*]15 GB ext4 / partition
[*]10 GB swap partition
[*]~436 GB ext4 /home partition
[*]ATI Mobility Radeon HD 5000 series     (with FGLRX activated)
[*]IDT 92HD73C1X5 sound card
[*]Ubuntu Desktop i386 10.04     (2.6.38-11-generic-pae)
[/LIST]
 Here are the symptoms :
 
[LIST]
[*]When it happens, my laptop seem to     “freeze” at the purple screen instead of displaying the login     screen.
[*]When it happens, if I hit     CTRL-ALT-F1, nothing happens, I'm stuck at the purple screen.
[*]When it happens, if I hit     CTRL-ALT-DEL, sometime I see the Ubuntu logo with normal reboot     progression, but sometime CTRL-ALT-DEL does nothing.
[*]When it happens, if I press the     power button for 8 seconds, my laptop shuts down and then when I     boot it, everything works perfectly until the next time it happens.
[*]It happens about one time once 20 or     30 startups.
[/LIST]
 Here are my questions :
 
[LIST]
[*]What can I do to help you helping     me?
[*]What can I do to fix this problem?
[*]Am I the only one who has this     problem?
[*]Which log can I read to have more     detail about what's happening?
[/LIST]
 ANY help will be welcome.
 
Thank you.

---

### Post by gennatolls on 2011-10-18
I had the same problem with an HP Dv7. I think it had something to do with the ATI graphics driver. Upgrading to the newest kernel (in 11.10) solved my problem

---

### Post by closingBrace on 2011-10-19
I already planned to switch to 11.10 this weekend. Let's see if it will fix this.

---

