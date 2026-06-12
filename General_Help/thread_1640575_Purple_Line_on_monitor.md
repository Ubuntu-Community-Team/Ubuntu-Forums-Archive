---
title: "Purple Line on monitor?"
date: 2010-12-08
forum: General Help
---

### Post by Nicked on 2010-12-08
Hello everyone! Well i'm a complete newbie to linux but i managed to get it installed alongside windows 7 and use ndiswrapper to get my wireless network adapter working. But the problem i have now is that i have this purple line that runs vertically on the far left of my screen. Now i have had a bad monitor that has done this before and i have tried taking a screenshot and it does not appear in it. But when i boot into windows the line is not there so this leads me to believe that it is an issue with ubuntu. I have tried searching this but didnt find much. Any help would be appreciated.


edit: even though its easy to describe i recreated what it looks like in gimp.



[IMG]http://www.flickr.com/photos/49484247@N04/5243292462/[/IMG]

---

### Post by uRock on 2010-12-08
Hello and welcome to the forums.

[s]When Ubuntu is booted, have you hit the screen alignment button on the monitor to see if that fixes it.

Can you catch the purple line when taking a screenshot? To take a screenshot you can either hit print screen or go in the menus to Applications> Accessories> Take Screenshot, then to post it here just click the little paper clip beside the smiley face and use that to upload the pic.[/s]

Edit, never mind that part.

---

### Post by krazeivan on 2010-12-15
I'm having the same problem. Just bought a Dell XPS Studio sx8100 and a LG E2350 and have it hooked up using an HDMI cable. I haven't tried to use DVI or VGA cables, because I don't have any and I'm too lazy. It's identical to the jpeg posted above. I think it might be X since I had the same problem when I booted a Fedora 14 disc. Haven't tried to install the proprietary ATI drivers yet since I'm installing 10.10 while I'm posting this :)

---

### Post by krazeivan on 2010-12-15
OK, now that I've got Ubuntu installed I installed the ATI (AMD) drivers (didn't want to but that damn line was annoying so I had to try) and it went away. So this must be a "feature" in the radeon driver included in X. Granted I have a newer card so it's not as robustly tested (the devs only have so much time and energy.) 

As an FYI to the OP you need to go into the Catalyst control center (admin) and change the overscan to 0%. Otherwise you'll have a nice 1 inch black border around the screen (well I did.) Here is a link that shows in pictures what you need to do:

[http://superuser.com/questions/57239/overscan-in-catalyst-control-center](http://superuser.com/questions/57239/overscan-in-catalyst-control-center)

It shows it in Windows(tm) but it's 99% the same. Hope this helps.

---

