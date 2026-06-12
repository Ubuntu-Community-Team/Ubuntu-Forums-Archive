---
title: "Keyboard stops working, items on taskbar only get highlighted when clicked"
date: 2010-08-22
forum: General Help
---

### Post by Chewy2 on 2010-08-22
Every once and a while I get this bug where my keyboard stops working in any application, and if I try to click on the buttons on the task bar at the top, they just get highlighted and don't do anything. This means I can't even just log off to fix it(unless I use a keyboard shortcut maybe) and have to shut down my computer and turn it back on to fix it.

Has anyone else experienced this problem? It usually happens while I'm browsing the internet typing something.

---

### Post by Chewy2 on 2010-08-23
Bump...

I find it hard to believe that nobody else has this problem. It happens to me at least once a day, three times so far today. Even once right when I started it up.

It should be noted that right click does not work at all, and only some of my AWN applications work, while the main menu doesn't.

Also when I just tap the power button it doesn't display the shutdown options as usual.

---

### Post by Chewy2 on 2010-09-13
I found out that the problem comes up when I turn off my laptop mousepad. 

No idea how to fix it however.

---

### Post by uylug on 2010-09-13
How about you go into the touchpad settings and untick the disable touchpad while pressing keys.

I can't remember whats it called but it's always said to be a bug, but it's actually a feature. I love it.

---

### Post by Chewy2 on 2010-09-14
Alright I tried doing that and I'll try messing around with it a bit and seeing if I can replicate the bug.

Not sure if that's what is causing it though. It's not the touchpad not working that's the problem, it's the keyboard not working that is.

---

### Post by Chewy2 on 2010-09-20
Alright that did not fix the problem, it just happened again.

Not even sure if I toggled the mousepad this time although I might have by accident.

I'm really surprised that this bug has zero attention seeing how nasty it is.

---

### Post by LuxAeterna on 2010-10-24
I have this problem as well. Taskbar suddenly becomes useless. Unable to restart unless I press CTRL+ALT+DEL and press "Restart". Then it works again for some time...

---

### Post by Sunflower1970 on 2010-10-24
I have this problem, too, on an old Dell Dimension 8200 desktop computer. Started in 10.04. I'm using a Microsoft, natural, multi-media wireless keyboard and mouse. There are lots of threads on here and on google with the same problem. 

1. I know it's not the batteries in either the keyboard or mouse. They're brand new.
2. There's a fix which works for some people from launchpad: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636311](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636311) towards the bottom. It's to replace xserver-xorg-input-evdev in maverick and use the one created in a ppa here. Didn't work for me.
3. Turning the computer on and off doesn't work. I don't know when my keyboard and mouse will stop working and it will do it each and every time I turn the blasted thing on.

What seems to work for me, and this is the ONLY workaround I've found that does work is to flip the computer on, wait till the keyboard and mouse begin acting weird, then switch yourself in to a console (ctrl + alt +F1) log in, then take yourself out of the console with ctrl + alt + F7. After that everything will work fine...until you turn off the computer for the day/night/etc. You'll have to do this every time the computer acts wacky.

Hope this and the suspend/hibernate (for laptops) issues get fixed in other updates soon.

---

### Post by Sunflower1970 on 2010-10-26
I just figured out what is causing this for me. Clicking Ctrl+t in nautilus or Firefox, or anything. When I turn on the computer, open up a browser, nautilus, whatever program allows me to open a new tab with ctrl+t, the keyboard and mouse stop working. If I drop in to a console with ctrl+alt+F1, log in, then go back to X with ctrl+alt+F7, everything is completely fine. I can open tabs to my heart's desire in whatever program I'm in. It's just that first occurrence. This all started in 10.04. I couldn't pin it down at that time, but I figured it out this morning. I now know I either need to avoid ctrl+t altogether, or just drop in to a console and come out of it again.

I've just tested this a few times with different programs and it happens like clockwork. Every time.

---

