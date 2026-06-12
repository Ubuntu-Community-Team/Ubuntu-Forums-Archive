---
title: "Help with mouse setup (10-button Kensington Pilotmouse)"
date: 2010-10-06
forum: General Help
---

### Post by davenkara on 2010-10-06
I am extremely new to running Ubuntu (3 days and counting), but finally made the commitment and won't turn back now.  I am having trouble with getting all 10 buttons of my Kensington Pilotmouse Laser Wireless Pro working.  I'm not averse to doing some research on my own, but after three days and no progress I've become confused by:

imwheel
xmodmap
xinput
xorg.conf
_many_ others...

I can't tell which one(s) are current and should be used and which ones are obsolete, still functional, or now in conflict with Ubuntu 10.04.  Some references to current (I'm using Ubuntu 10.04) methodology on how to configure the "extra" buttons on a mouse (or better yet THIS mouse) would be great.  

Also, I might as well describe my specific problem for context.

I am running World of Warcraft (sigh, I know) under Wine on a Dell XPS system I received from a family member.  When I go to bind operations to the 3 thumb buttons, only buttons 8 and 9 (forward/backward) are recognized.  Clicking the middle thumb button (10) is simply not recognized.  I had a similar issue in Windows and used the Kensington MouseWorks program to remap button10 to a "mmiddle/wheel click" in order to get it to do anything.

I believe what I'm looking for is a way to enable/recognize the 10-th mouse button (it obviously _can_ do something) and get it to pass clicks into the game.  Now, I'm familiar with what I did before, so mapping the middle left thumb button to "also" send a middle/wheel click to the game (or any app really) would be perfectly fine.

---

### Post by davenkara on 2010-10-06
I stumbles across a reference to "xev" and tried running this on my console.  When I do so, it opens a window in which I can test out my mouse responses.  Although the button mappings are completely different than I expected, I do see the following when I click on the middle thumb button:

ButtonPress event, serial 36, synthetic NO, window 0x4200001,
    root 0x15a, subw 0x0, time 7393108, (87,123), root:(90,176),
    state 0x10, button 10, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x4200001,
    root 0x15a, subw 0x0, time 7393244, (87,123), root:(90,176),
    state 0x10, button 10, same_screen YES

So it seems the Ubuntu is seeing the button10 press.  But perhaps it is not being passed into the child process?  Or at least not correctly?

I see processes for Wow.exe and wineserver both running.  Would I need a process/app specific configuration to pass button10 correctly?  Some of the (possibly obsolete) options I've been coming across implied that I might need a app/specific mapping.  I think I'd rather have a "general" solution, but I really don't know what I need or should have.

---

### Post by davenkara on 2010-10-06
My self-education continues.  The application (warcraft) am trying to pass button10 into will NOT accept button 10.  There's a limit on how many buttons it will accept (5 it seems)... which is probably why button 8 or 9 (according to xev) matches button5 in the game's keybinds.

My previous goal was impractical.

What I would like to do instead, is get a reference or process as to how I can remap buttons on my mouse to another button on the mouse.  For example, remap the middle thumb button (10) to the middle/wheel click (2 according to xev) which is hard to access without scrolling or tilting.  I essentially did this in Windows using the Kensington MouseWorks program, so now I'm looking for the "right" way to do so in Ubuntu.

I tried playing around with xinput, but I'm not sure how it correlates with the xev output, and it its the appropriate path to pursue.

---

### Post by davenkara on 2010-10-07
I figured it out... or at least how to make it work with Ubuntu 10.04.  I hope this is a/the "correct" way.  I used the xinput command to list and find my mouse, then another xinput command to perform the remap of the mouse buttons. 

I wanted to remap button10 to duplicate button2 (wheel/middle click) and used the following:    

xinput set-button-map 11 1 2 3 4 5 6 7 8 9 2    

The first "11" is the device id for my mouse because I couldn't get the matching string from the "xinput --list" to work.  For some reason, my mouse is listed as a keyboard and as a mouse/input device with the same string, but different device IDs.    Any time I hot-plug my mouse transceiver the device number can change, so I'll probably solve this with some sort of parsing script that runs on every login.

---

