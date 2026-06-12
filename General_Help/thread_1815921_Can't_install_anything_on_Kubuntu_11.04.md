---
title: "Can't install anything on Kubuntu 11.04"
date: 2011-08-01
forum: General Help
---

### Post by enlitenapa on 2011-08-01
Hi! I've recently installed Kubuntu. First time using Linux, been using windows for the past 8 years, so please have patience with me.

First some specifikations about my computer:

> Kubuntu Release: 11.04
NOT installed inside of windows.
Version 4.6.2 of KDE
Version of Grub: Version: 0.97-29ubuntu61 (Copied from result of konsole command)
No other operating systems installed.

Pc Information:
Desktop
CPU: Genuine Intel
64-bit
GPU: nVidia Corporation GT216 [GeForce GT 220]
RAM: 4GB

My problem: I'm not able to install anything at all, except for the Apps in Kpackagekit (Software Center).
E.g: I tried installing a game called Heroes of Newerth ([www.heroesofnewerth.com](www.heroesofnewerth.com)) and downloaded the .sh file as specified. I also right-clicked and clicked "properties" and under the tab "persmissions" i filled the box "Is executable". But when i dubble-click the .sh file nothing happens. According to the guides the setup should start by just doing that. 

Thought on an other forum i was told that dubble-clicking doesn't work on sh. files.

So i opened konsole and typed ./HoNClient.2.1.0.1.sh (the setup for the game).
But all i got was this message:

> 156244+0 records in
305+1 records out
156244 bytes (156 kB) copied, 0.122757 s, 1.3 MB/s

(<unknown>:7535): Gtk-CRITICAL **: IA__gtk_text_attributes_ref: assertion `values != NULL' failed

(<unknown>:7535): Gtk-CRITICAL **: IA__gtk_text_attributes_ref: assertion `values != NULL' failed
Segmentation fault

---

