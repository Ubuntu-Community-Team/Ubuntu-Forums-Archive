---
title: "icons vanished"
date: 2010-05-04
forum: General Help
---

### Post by ptoche on 2010-05-04
This is an issue that comes up once in a while, unfortunately I have not been able to find a solution that works for me.

I'm using Kubuntu, currently upgrading from 9.10 to 10.04 (I think) precisely in the hope that my problem will solve itself in the process. However, I'm still curious about what a solution might be. So one day most of the icons in the bottom-right taskbar (left of the clock) vanished. I'm not sure why nor precisely  when. I noticed it when I needed to connect wireless to another place than the one I usually connect to, and which did not connect automatically, that day looking for the network/manager/whateveritsactuallycalled icon, well it wasn't there. Also no longer there, the keyboard toggle icon (I use dvorak and it used to be possible to toggle back to standard US by clicking on an icon in the taskbar). There are probably other icons that disappeared too, like notification about updates maybe. The only icons I have left are the battery gauge (thank GOD for that) and something about the last plugged-in device. 

**So my much-loved icons are gone. Where are they now?**

I've tried a lot of different things, like adding widgets, but my problem doesn't seem to be about adding widgets, for instance the knetworkmanager doesn't show up as a widget I could add (another network manager called NetworkManager does appear as a widget, but it doesn't work at all), nor does the keyboard layout toggle icon (show up as a widget). I read something about a missing "notification area" that may have to be added -- but I don't seem to be able to do that, as the instructions I attempted to follow were not perhaps relevant to my kubuntu release.

Thanks for your input,

Patrick.

P.S. this is actually my first post here, so if I'm doing something wrong (like not having an avatar) please forgive me and inform me.

---

### Post by Untitled_No4 on 2010-05-04
Hi Patrick,

If I understand you correctly what you are describing is not really a problem but a change in the way some widgets are displayed which took place in KDE 4.4.

The Network Manager icon and other widgets have now moved into the system tray area. This is the area with the device notifier (i) on the right of it. Some of them might just be hidden or not set up to be there.

First thing you need to is unlock your widgets, if they are locked, and then right click on an empty area in your System Tray Settings. 

 Click on Auto Hide on the left pane and select which widgets you want to show, which to hide and which to let KDE handle automatically for you.

While you're at it have a look at the Plasma Widgets section which allows you to add widgets to the system tray.

I hope this solves your problems.

---

### Post by ptoche on 2010-05-08
Hi, untitled_no4 is it?

thanks a lot for your suggestions, it took me a little while to try them as I can't connect Ubuntu to the net from home, but no such problem from the local cafe, which is where I am connected now (unfortunately they close at 9pm...)

> what you are describing is not really a problem but a change in the way some widgets are displayed which took place in KDE 4.4.

okay, that's plausible, just to be clear all I have in my system tray area, at the bottom right-hand side of my screen, are, starting from the right: a clock (awkwardly presenting only parts of the display, the time, the pm and the month having bits cut off, useless and ugly but I don't care), then to the left a battery icon that works wonderfully well, and lastly to the left of all that an icon allowing me to "Show the Desktop".

In the system tray area, I can lock and unlock widgets at will. In the "Panel Options" I can add "Add Widgets," "Add Panel," "Lock Widgets," select "Panel Settings," and a very scary "Remove this Panel" option.

"Add Panel" does weird things I couldn't describe in words.

I haven't been able to find an "auto-hide" option anywhere near the system tray area.

I don't see anything specifically called "Plasma Widgets."

In the "Add Widgets" options, if I search for "Network" all I get is something named "System Monitor - Network" and described as "A network usage monitor." There is no trace of "KNetworkManager," which if I understand correctly is what I want.

If I add this "System Monitor - Network" widget, a very weird thing gets lodged as an icon. It's difficult to describe, just mumbled letters or numbers, looks very buggy. Nothing like the Network icon I once add in the system tray.

Am I close? many thanks,

Patrick.

Update: I have played around with the widgets a little more (I should have waited before posting my message) and found a very nice clock to replace the buggy one I had there, I also found lots of fun and useful icons, so I guess the only icon I'm really missing is a network-connection-status type icon that would tell me whether I'm connected or not and which, upon a click, would offer me to tweak its options. The "System Monitor - Network" widget that I get listed doesn't do any of these things. **Is there a way to add widgets to the list of widgets? ** Thanks!

---

### Post by Untitled_No4 on 2010-05-09
Hi Patrick

In KDE System Tray is a widget like the clock widget and you can place it on the panel or the desktop like any other widget, so it seems you don't currently have the System Tray widget. You can add it like you added the clock by opening the panel options and then selecting Add Widgets and adding System Tray. Here is my system tray for reference:

[IMG]http://farm4.static.flickr.com/3318/4590948681_a13c41ed2e_o.png[/IMG]

The system tray might already have the network manager, but if it doesn't go back to my previous instructions.

When you add a panel it usually adds a very small panel on the top left corner on the screen. You can then make it bigger or relocate it.

I hope this helps.
Golan.

---

### Post by doktormiod on 2010-05-22
Hi, I have a similar problem, after upgrading to 10.04 (i had kde 4.4 before) some icons don't appear in system tray. I don't think it matters if they are part of kde becouse amarok and kopete icons work properly but ktorrent doesn't. It's not in the tray though in tray settings theres a dialog with options for ktorrent (hidden, auto and always visible). Other icon that doesn't work is netowrkmanager and nm-applet(network manager for gnome).
Do you have any ideas?

---

