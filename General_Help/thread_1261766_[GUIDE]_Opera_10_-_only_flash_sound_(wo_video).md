---
title: "[GUIDE] Opera 10 - only flash sound (w/o video)?"
date: 2009-09-09
forum: General Help
---

### Post by ExiMoR on 2009-09-09
Hey guyz!
First of all: I've tried to find category where I can post this, but I had no success, so I'm posting it right there (General Help)...

Okay.. I've updated my Opera 9.6X to Opera 10. It have beatiful Matte-ish design, but that is not the main reason why I'm usin' it now, instead of Firefox.. It's fast, nice (again) and nice? :D Okay. Now the biggest reason why I'm writing that:
After update and testing.. Flash wasn't working. I've spend some my time to surf net and search for any help, but w/o success.. 
So.. I've finally figured where flash and other plugins are and why is not flash working...
I goes to Settings>Advanced>Contents>Set-up plugins and there I've spotted 3 dirs, from what is opera using plugins:
/usr/lib/opera/plugins
/usr/lib/mozilla/plugins
/usr/lib/flashplugin-installer
...
I've thinked like a: in flash is only sound.. so there is no video, but why...
I've spotted that in
/usr/lib/mozilla/plugins
is flash alternative and thinked what about to setup opera to don't use
/usr/lib/mozilla/plugins
...
I've unchecked it and tried youtube.. All was okay! sound, video...
So flash player alternative must kicking original flash player's butt and they are playing only sounds...
I've created directory
/usr/lib/opera/opera-plugins
and puted to it links to all mozilla's plugins, instead of flash player alternative...
Then I've setted up opera to don't use mozilla directory, but/and only opera-plugins dir..
All is working now well... 
Okay. Hope, that it can help to anybody..
____________
Sorry for my "english" :lolflag:

---

