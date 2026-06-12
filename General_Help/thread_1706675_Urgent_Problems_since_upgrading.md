---
title: "Urgent: Problems since upgrading"
date: 2011-03-14
forum: General Help
---

### Post by spike1 on 2011-03-14
I decided it was high time to update from jaunty yesterday so finally bit the bullet...

I was expecting some problems and WOW did I get em.
First the update to karmic went fubar, took me ages to get the right dpkg incantation to allow the package configuration to complete and then the thing wouldn't boot, couldn't find the UUID of my root using the karmic kernel but the older jaunty ones were still fine, although I'd lost compiz, it wouldn't start anymore no matter how much coaxing. So, I bit the bullet again and continued to upgrade, this time to LTS.

Still no compiz. I've got an intel chipset which was blacklisted, I bypassed the blacklist and every window now appears upside down if I try to switch to it. (only appears, the buttons/menus/etc are all in their original places, but not, if you see what I mean, only the visual changed, not the physical locations).

Now, I *LIKE* laying back on the sofa with the keyboard on my lap, but I can't DO that without SOME kind of ZOOM facility. I lost the ctrl-alt=+/- when I moved from hardy to jaunty. Never been able to get that back, no matter how many times I type "DontZoom" "false" into xorg.conf.

I also make extensive use of the virtual consoles on F1-F6...
And now, the powers that be have deemed that I can't use that either because the thing is set at some ludicrously high resolution that I need to squint close up to read it! And in their infinite wisdom they've taken away my fix for that TOO! 

vga=normal no longer works in grub's menu. Something overrides it in the boot process and now I can't figure out how to disable that either.

PLEASE help me get my computer back into a state I can USE IT comfortably.
All these stupid tweeks and fiddles that serve no purpose are really starting to get on my **** now.

So 
1: HOW DO I EITHER 


A: Get compiz to work without making all windows appear upside down (but only in looks, the buttons and menus are still the right way up PHYSICALLY, which makes things even more tricky cos you can't see where  the menu items are meant to be)


The chipset is:  00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

or

B: Give me a concrete foolproof way of re-enabling ctrl-alt-+/-

and

2: tell me PLEASE, HOW DO IT GET THE CONSOLES BACK? 640x480 is fine. 80x25 text resolution is brilliant, I do not need 200 characters per line! Mainly because I have to be 6 inches from the screen to read it.

---

