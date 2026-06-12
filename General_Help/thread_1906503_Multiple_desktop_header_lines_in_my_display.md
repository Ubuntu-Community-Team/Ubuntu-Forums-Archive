---
title: "Multiple desktop header lines in my display"
date: 2012-01-09
forum: General Help
---

### Post by Shay123 on 2012-01-09
Hello,
I have upgraded to Ubuntu 11.10 and gone back to the Gnome 2 style desktop. No major problems - even got two screens working. Switched on a few times everything is working fine.

Today I have switched on and my primary laptop screen has the desktop header line at the top and four blank header lines underneath. The second screen has one blank header line.

The system is usable but the screen space is getting smaller - is it retribution for not using the new screen saving Unity system?  ;)

I can not even find a problem related to this one so any help will be gratefully received!

Shay

---

### Post by Shay123 on 2012-01-09
Hi should have added some tech info?
Laptop HP G60dual boot Vista and Ubuntu 11.10 uding Grub bootloader
Second screen Hanns HX191DPOT 19 inch
Graphics card GeForce 8200 M G
Graphics Driver NVidia latest as loaded by Ubuntu - active and working
Xserver seems to be by Nvidia also

---

### Post by Shay123 on 2012-01-09
Hello,
I have been playing with this (Display package- under system settings -does not always acknowledge two screens) and tried to get rid of the dual display and taken out the Nvidia driver and reinstalled it. 

I also played with the Nvidia Xserver panel and the display package. 

Well I got back the original laptop screen and it now works under unity and Gnome 2 desktop environments but instead of five header lines I know have ten!

A little knowledge is a dangerous thing? :o

Shay

---

### Post by Shay123 on 2012-01-11
Having read more threads I think this is related to the missing header that people get when they have installed Ubuntu 11.10 and then tried to install second monitors or back track to the Gnome Desktop? 

It is also possible that this is an Xserver problem as the Multiple screen Pkg and the Nvidia Xserver pkg have different info in them?

Last chance saloon before I go back to Ubuntu10 and wait for some good reviews of Ubuntu 12 ;)

---

### Post by Shay123 on 2012-01-11
Hello,
Had to reinstall Ubuntu 11.10
Then Installed the [COLOR=Blue]Nvidia driver[/COLOR]
[INDENT] [COLOR=Blue]185[/COLOR] was on the list under the recommended driver - this has updates in it.
[/INDENT]AT THIS POINT you should save your[COLOR=Red] **[COLOR=DarkRed]/etc/x11/[/COLOR]**[/COLOR] file somewhere very safe - according to all the advice I read! I didn't cos I was prepared for my system to fall apart and reinstall. (Years of mental WIN reinstalls still reside in my brain - Ubuntu is still easier)

Then went to [COLOR=Blue]Nvidia Xserver[/COLOR] package
[INDENT]Used [COLOR=Blue]twin view[/COLOR] setting and made my laptop the [COLOR=Blue]Primary Screen[/COLOR] and [COLOR=Blue]Enabled[/COLOR] the second LCD screen

I then tried to save to the the xorg.conf file - this gives an error but I ignored it looked and pressed the preview button of the following screen. 

I then saved the contents of the [COLOR=Red]**[COLOR=DarkRed]xorg.conf[/COLOR]**[COLOR=DarkRed] [/COLOR][/COLOR][COLOR=Red][COLOR=DarkRed][COLOR=Black]in a non-formatted text file [/COLOR][/COLOR][/COLOR][COLOR=Red][COLOR=DarkRed][COLOR=Black]for my own interest and education and possible rewrite of this file if needed in the future[/COLOR][/COLOR][/COLOR].
[/INDENT]I then quit and restarted the computer and everything works

Then went into a terminal to run gnome-session-fallback ( I had previously run a different package to get the classic menus etc and it was somewhere between setting the classic menu and the twinview screens that problems occurred.

Everything seems to runnning ok now but if anyone can tell me what the conflict was IO would be grateful to hear as this is tied to the no menu problems other people had but this seemed to be the only outcome of multiple header bands at the top of the screen.

Seamus

---

