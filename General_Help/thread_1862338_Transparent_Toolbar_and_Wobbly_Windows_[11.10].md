---
title: "Transparent Toolbar and Wobbly Windows [11.10]"
date: 2011-10-16
forum: General Help
---

### Post by Gitominoti on 2011-10-16
So I have two questions, and I'm not to great with Ubuntu, so give me the fix in simple terms. First of all, I'm trying to get the toolbar at the top of the screen and the bar at the top of all windows to be transparent. Basically like Aero in Windows Vista/7. I've looked for a tutorial, but I haven't found one that works for 11.10.

Second of all, I have wobbly windows turned on in the Compiz settings. However, sometimes it doesn't work (as in, the windows don't wobble when I move them). This worked when I had 11.04 on the Classic setup.

Anyways, any help would be great. Thanks

---

### Post by gufide on 2011-10-16
for the wobbly window, sorry, there's no fix for the moment, it happen for me too and I just waiting for a compiz update.

 For the transparent panel and launcher, this in the compizconfig setting manager in the unity plug-in, then in the experimental options, then you can adjust the transparency.

If you want a more windows-like interface, you can install kde on your computer. Here's a screenshot:

I hope this was helpful

EDIT: you can install kde  by searching kde-standard in the software-centre

---

### Post by moorhead98 on 2011-10-16
Lol, showing a screenshot of opensuse in a form about ubuntu. 
Anyway, go to the software center and install "CompizConfig Settings Manager"
Then open it up, and scroll down to the section called "Ubuntu Unity Plugin"
Then at the "Experimental" tab, find "panel opacity"
Then just mess around with it to find what you like.
For window transparency, hit ALT and F2 then type in "gconf-editor"
Then hit the arrow on "apps" then scroll down untill you find "gwd"
Then on the right, look for where it says "Metacity_theme_opacity", double click on the number, and then replace it with something smaller than 1 (a decimal)
Then everything should be good for you!

---

### Post by viperdvman on 2011-10-16
The only problem is, changing the GWD settings in gconf-editor doesn't work in 11.10's Unity... at least not on my LiveUSB session.

And the Compiz settings only work for the launcher, top panel, and dash... nothing regarding the windows or the title bar opacity.

I too want to know if there's any settings specific to 11.10 that make the window titlebars translucent. I have it working on my 11.04's Ubuntu Classic just fine (I'll check my 11.04's Unity another time).

---

### Post by Raaaaay on 2011-10-18
For the wobbly windows problem, I had the same thing. What seemed to have solved it for me is that I went into Compiz configuration > Effects > Wobbly windows, and tweaked a few settings for the sake of it. In particular, I changed "grid resolution" to full, and "spring K" to full. This will change the behaviour of wobbly windows a little bit, but at least now the windows wobble every time I try to move them.

---

### Post by viperdvman on 2011-10-18
Update... using GWD (and probably Ubuntu Tweak too) actually helped to fix the transparent menus problem, and also the titlebars too, though I had to reboot to get the changes to show on my live session.

---

### Post by abisdad on 2011-10-23
Upgraded to 11.10 yesterday, and missed my wobbly windows - so did some research and found that you needed to install compiz thingy.

[COLOR="Red"]**Did that and stuffed my install up!!!**[/COLOR]

Dual screen off an Acer TravelMate.

Everything froze on main screen, fortunately Ubuntu Software Center was still running with compiz thingy still in it, so I hit the uninstall button asap. Uninstalled OK, but still top menu bar and side bar were frozen.

Re-booted and the only thing running when I logged back in was file manager!  (Which was great as I was able to back up everything!)

I then did a partial re-install - keeping my files etc. but still the same!

[COLOR="Red"][B]I HAD TO DO A COMPLETE REINSTALL AFTER!

DO NOT INSTALL "_COMPIZCONFIG SETTINGS MANAGER_" - IT WILL STUFF UP YOUR SYSTEM - READ THE COMMENTS UNDER MORE INFO!!!! #-o[/B][/COLOR]

---

