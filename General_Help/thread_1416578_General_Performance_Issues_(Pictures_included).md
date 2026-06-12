---
title: "General Performance Issues (Pictures included)"
date: 2010-02-26
forum: General Help
---

### Post by smcnally on 2010-02-26
I'm having performance issues with Ubuntu 9.10 and I'm having a really hard time figuring out if it is related to my video card or some other hardware that may not be playing nice.  These are the most noticeable issues to me:

Programs seem to take longer to load than I'm used to with previous versions of Ubuntu and application performance seems sluggish.  In example, Songbird takes about 25 seconds to fully open and it's UI opens in chunks.  When it does open it the scrolling in it is jumpy.  Scrolling in Firefox also doesn't seem quite right.  This all happens with visual effects turned on or off.  Surprisingly, the visual effects set to "Extra" seems to run smoothly (the effects, not the applications).

The other issue I have is that I cannot play Hulu or YouTube video in a size bigger than about 640 pixels wide without it affecting the playback.  It looks great in a small window, but once you start stretching it, or go full screen, it isn't even watchable.  

I'm including snapshots of the system information along with System Monitor and my Vid Card settings.  Any help would be greatly appreciated.

[IMG]http://i17.photobucket.com/albums/b68/stevesreef/Ubuntu/sys-monsnapshot.jpg[/IMG]

[IMG]http://i17.photobucket.com/albums/b68/stevesreef/Ubuntu/sys-monsnapshot2.jpg[/IMG]

[IMG]http://i17.photobucket.com/albums/b68/stevesreef/Ubuntu/sys-monsnapshot3.jpg[/IMG]

[IMG]http://i17.photobucket.com/albums/b68/stevesreef/Ubuntu/nvidiasnapshot2.jpg[/IMG]

[IMG]http://i17.photobucket.com/albums/b68/stevesreef/Ubuntu/nvidiasnapshot3.jpg[/IMG]

[IMG]http://i17.photobucket.com/albums/b68/stevesreef/Ubuntu/nvidiasnapshot.jpg[/IMG]

[IMG]http://i17.photobucket.com/albums/b68/stevesreef/Ubuntu/nvidiasnapshot4.jpg[/IMG]

[IMG]http://i17.photobucket.com/albums/b68/stevesreef/Ubuntu/nvidiasnapshot5.jpg[/IMG]

---

### Post by smcnally on 2010-02-26
And here are the last two snapshots:

[IMG]http://i17.photobucket.com/albums/b68/stevesreef/Ubuntu/nvidiasnapshot7.jpg[/IMG]

[IMG]http://i17.photobucket.com/albums/b68/stevesreef/Ubuntu/nvidiasnapshot8.jpg[/IMG]

---

### Post by smcnally on 2010-02-28
Nobody has any ideas?  If everything looks fine in the images the what should I look into?

---

### Post by Richard1979 on 2010-02-28
This probably won't be much help to you but I also run an Nvidia card on a 24" monitor with the same native resolution as you.
I found that Youtube videos wouldn't play well unless I opened them in a new window by clicking on the embedded video.
You might also want to enable Sync to VBlank or VSync etc. It should improve video and game quality.

---

### Post by Easy Limits on 2010-02-28
Try changing your GPU Scaling Method to Stretched.

---

### Post by Easy Limits on 2010-02-28
And change your Open GL Performance > Image Settings slider to be more in the middle instead of all the way to the right.

---

### Post by smcnally on 2010-03-01
Thanks, those recommendations seemed to help some.  It still seems like it isn't where it should be though.

---

