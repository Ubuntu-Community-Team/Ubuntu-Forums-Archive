---
title: "NFL Rewind-Move Networks Media Player"
date: 2009-09-11
forum: General Help
---

### Post by eival on 2009-09-11
new update - i know this is old but i just wanted to update all those that were interested in this service last year, the NFL has now switched to Adobe Flash and ive already paid for the 1 month and watched a few games and it works perfectly, pretty much the same quality if you already had MLB.tv and NBA League Pass Broadband.

nfl.com/rewind
:popcorn:

============================================

original post below:


Ubuntu 8.04
NFL Rewind service
Firefox 3.014(ubuntu)
Firefox latest stable(WINE 1.0/windows xp sp3)
Move Networks Media Player - mandatory to load NFL rewind
--------------------

first off, if anyone knows a way to sneak Ubuntu's firefox past the "your OS isnt compatible" when trying to sign-in to the service then that would take care of everything....


how ever, my next options/issues are, i then tried accessing it with WINE, using Firefox and i got the Move Networks Media Player installed and everything was fine but now when i actually sign in an the player box opens it crashes the entire browser immediately. how do i find out whats causing the crash and possibly fix it?


my next option/issue was to use my Windows XP VM, everything worked fine, this time im able to actually open up the player and see last nights Steelers/Titans game available to be selected but im assuming since im running thru a VM my videocard doesnt have enough memory to actually run the video cause the area where the game should be(idk the correct term) but instead of a black area it was showing trails of tabs/windows that were open just prior to this popup window and it never clears. 

my Nvidia card only has 256 MBmb of memory which 2x the recommended amount to run NFL Rewind according to nfl.com however they say that only 32mb is required and i currently have the VM at half 128mb(the recommended ammount) so it should play fine, i can view HD video on youtube/gametrailers.com/myspace an other places without any issues in the VM.

and i know its not RAM/memory cause i have the VM at 900mb my total is 2 gigs, and nfl says 512mb is the recommended amount, so im almost double in that aspect.

would increasing the VM memory help? would it freeze up my entire computer allotting all memory to the VM?


if i cant get any of these to work my only option left would be create a partition an install windows so i could run it with full resources :-&

unless theres more options that ive already tried above, any help or tips will be appreciated!:popcorn:



EDIT: forgot about this lil error, perhaps its actually a flash 10 issue, i have the lastest stable version installed, heres a screencap of the trailing issue i mentioned plus the actual error

[http://i31.tinypic.com/2hhf5vt.png](http://i31.tinypic.com/2hhf5vt.png)

---

### Post by sit properly on 2009-09-11
I'm having the exact same issue. I tried to install it under Firefox in WINE, but it crashed (also trying to view NFL Rewind) whenever I'd try to view it. I tried it in IE4Linux and it wasn't even recognized as Windows OS.

I don't have an XP disc, so getting it working with VM isn't an option for me. WINE would be great. 

Anyone have any suggestions?

---

### Post by eival on 2009-09-11
i guess if someone knows how to edit Firefox to make websites think its Windows rather than Ubuntu would be enough to get it working.

---

### Post by Bucky Ball on 2009-09-11
[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

That could be what you need. I haven't tried it. Have a good read first and be aware that some people have this crashing their machine but apparently easy enough to fix. You can set the User Agent to report IE even though you are using Firefox.

---

### Post by sit properly on 2009-09-12
This would fool their site, making it think it's Windows, however, Move Networks Media Player will won't work. 

Unless you could somehow trigger it to open in WINE. Is this an option?

---

