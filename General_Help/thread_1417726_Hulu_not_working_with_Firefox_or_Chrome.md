---
title: "Hulu not working with Firefox or Chrome"
date: 2010-02-27
forum: General Help
---

### Post by kut77less on 2010-02-27
I recently installed a 64bit version of flash on firefox and Google Chrome. When I go to hulu, so I can watch a video, It does not play the video and simply says, "Sorry unable to load video, please check your internet connection" All other flash related sites work

---

### Post by johngreth on 2010-02-27
I've also have problems with flash on some sites. I never use hulu, but the problem probably has to do with the flash installed. There's nothing to do but wait for Adobe to release something better.

---

### Post by Ozymandias_117 on 2010-02-27
I don't know what the problem is, but it isn't a problem with flash. I have Ubuntu 64-bit with flash installed and Hulu runs fine.

---

### Post by Chronon on 2010-02-28
I have the same problem with Firefox 3.5.8 on a 64-bit Kubuntu 9.10.  Interestingly, Hulu Desktop streams videos just fine.  I'm not too sure of the particular circumstance that leads to this problem.  I have a 32-bit Ubuntu 9.10 running Firefox 3.5 and it streams fine in the browser.

---

### Post by brianpatrick on 2010-03-01
Ubu 9.10, 64 bit, workstation, fully updated, Firefox
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.8) Gecko/20100214 Ubuntu/9.10 (karmic) Firefox/3.5.8
I just "upgraded" to:
Shockwave Flash File name: libflashplayer.so Shockwave Flash 10.0 r45

No worky! "... Check YOUR internet..." WTF? Youtube works perfectly as does BBC, Fox, NPR, CNN and most other flash sites I have tried (abc.com just locks up, CBS <- douches object to adblock). 

It used to work. Is it Hulu, adobe or the advertisers pizzing on Linux? Some claim it works. Perhaps it is 32bit. 

I nuked all 10.0.32 flash versions in my file system, overwriting with adobe's l-&-g 64 bit, 10.0.45. 

And, Opera fails too, using 10.0.45 in /usr/lib/opera/plugins/libflashplayer.so 

I hate booting my old xp box with a crappy monitor to watch. 

Death to flash. Long live HTML5!

    BrianP

---

### Post by ubun_two on 2010-03-01
I have the same problem with my 64bit Karmic.  It was working fine in Jaunty 64bit before I upgraded the same system.  I can run Hulu using Hulu Desktop, but not with Firefox, Chrome, nor Epiphany.

Furthermore, Hulu seems to work fine on my netbook which has 32bit Karmic.

---

### Post by Chronon on 2010-03-02
Yes, this seems to only occur in 64-bit systems, from what I have seen.  I suppose a bug report should be filed if it hasn't been done yet.

---

### Post by Chronon on 2010-03-08
Apparently, some folks are seeing this [with Open Solaris too](http://opensolaris.org/jive/thread.jspa?threadID=121880&tstart=6), so it's not likely a kernel issue.

---

### Post by samMD on 2010-03-22
> **brianpatrick said:**
> Ubu 9.10, 64 bit, workstation, fully updated, Firefox
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.8) Gecko/20100214 Ubuntu/9.10 (karmic) Firefox/3.5.8
I just "upgraded" to:
Shockwave Flash File name: libflashplayer.so Shockwave Flash 10.0 r45

No worky! "... Check YOUR internet..." WTF? Youtube works perfectly as does BBC, Fox, NPR, CNN and most other flash sites I have tried (abc.com just locks up, CBS <- douches object to adblock). 

It used to work. Is it Hulu, adobe or the advertisers pizzing on Linux? Some claim it works. Perhaps it is 32bit. 

I nuked all 10.0.32 flash versions in my file system, overwriting with adobe's l-&-g 64 bit, 10.0.45. 

And, Opera fails too, using 10.0.45 in /usr/lib/opera/plugins/libflashplayer.so 

I hate booting my old xp box with a crappy monitor to watch. 

Death to flash. Long live HTML5!

    BrianP


Opera supports HTML5 now everything else needs to support it, by the way 

I solved the issue: "O Menu"(since its 10.10 just go to "tools")--->"settings"--> "preferences"-------> "advanced"----> "content"--> "plug-in options"-----> "change path" 

make sure the only boxed that is checked is for the directoy: /usr/lib/plugin-installer

---

### Post by efflandt on 2010-03-22
At some point in time Hulu stopped working with "real" 64-bit flash in a browser, but supposedly works with 64-bit flash in Hulu Desktop.  But not for me because my old Athlon64 lacks the lahf_lm instruction used by real 64-bit flash.  While the flashplugin-lahf-fix works for most 64-bit browser flash for me, Hulu Desktop apparently does not pick up the lahf fix plugin, so it will not even load.

I suspect people who say Hulu works fine with their 64-bit browser are not really using 64-bit flash.  They are probably using flashplugin-installer, which is 32-bit flash with nswrapper, and does work fine for me in 64-bit Ubuntu with Hulu in a brower or Hulu Desktop.

But my old computer is a little on the slow side, so I switch my screen resolution from 1080p to 720p when viewing Hulu.  I have a stand alone BluRay player for streaming Netflix HD (which I hear does not currently work in Linux).

---

### Post by andrewthomas on 2010-03-22
> **efflandt said:**
> 

i suspect people who say hulu works fine with their 64-bit browser are not really using 64-bit flash.  They are probably using flashplugin-installer, which is 32-bit flash with nswrapper, and does work fine for me in 64-bit ubuntu with hulu in a brower or hulu desktop.



+1

---

### Post by tylerious on 2010-05-27
> **efflandt said:**
> At some point in time Hulu stopped working with "real" 64-bit flash in a browser, but supposedly works with 64-bit flash in Hulu Desktop.  But not for me because my old Athlon64 lacks the lahf_lm instruction used by real 64-bit flash.  While the flashplugin-lahf-fix works for most 64-bit browser flash for me, Hulu Desktop apparently does not pick up the lahf fix plugin, so it will not even load.

I also have an older Athlon64 with the same issue. On another forum, it was suggested to use the flashplugin-lahf-fix.so and modify  /usr/share/applications/huludesktop.desktop to:

TryExec=huludesktop
Exec=LD_PRELOAD=/usr/lib64/mozilla/plugins/flashplugin-lahf-fix.so huludesktop %F

This does not work for me (I get a 'No such file or directory' error), though it might be a step in the right direction. Does this work for anybody else?

EDIT: This is the link to the other forum: [http://www.hulu.com/discussions/19/111980/508132](http://www.hulu.com/discussions/19/111980/508132)

---

