---
title: "Blank screen (ATI) on TV when it works on Monitor."
date: 2011-07-31
forum: General Help
---

### Post by spwango on 2011-07-31
Hey all,

Natty install -- ATI 9800 is the video board. 

I installed Natty on it with the machine hooked up to a Samsung LCD with a 1680x1050 resolution over DVI.  No problems at all.  I want the box to pretty much output MP3s and web video, so I'm not needing much.  When I take the box and hook it via DVI to my LCD, I get a blank screen on boot up.  I try sticking the natty CD in it, and I get a blank screen trying to live boot it too.  The LCD doesn't do 1680x1050, so I brought it back to my Samsung and set the default resolution to something nice and safe:  1280x1024.  Still the same behavior.  When I take splash mode off, I see a "load fallback graphics devices fail" error as it is booting up.  Hard for me to think the driver is the fault here when it works on my over LCD just fine.  Any ideas?  Thanks.

---

### Post by spwango on 2011-08-01
Any ideas on this?  I'm still stumped.  I haven't dug up detailed specs to be sure the card (Radeon 9800) can do 1080p or not, but it's highest resolution is higher than that.  I still can't get this to work. :(

---

### Post by Mark Phelps on 2011-08-01
The problem you're facing is that "old" board has been relegated to "legacy" status by AMD/ATI -- meaning, they haven't provided restricted drivers for it for years.

You're limited to the default open-source driver now, and it only provides basic functionality.  So, I doubt you're going to be able to get that to work.

---

### Post by spwango on 2011-08-01
> **Mark Phelps said:**
> The problem you're facing is that "old" board has been relegated to "legacy" status by AMD/ATI -- meaning, they haven't provided restricted drivers for it for years.

Perhaps I'm ignorant about the way drivers work on the Linux side, but I find it odd that the board can drive my LCD but can't drive my TV.  Is there a way to force the resolution at start up to work around this?

If not, is there are an older version you'd recommend?   My needs are pretty simple here.

Thanks for the advice.

---

### Post by Mark Phelps on 2011-08-02
> **spwango said:**
> If not, is there are an older version you'd recommend?   My needs are pretty simple here.

IF you mean older version of Ubuntu, I do know that ATI dropped support with Ubuntu 9.04 for the "X" series of cards -- 'cause I had an X1650 that didn't have restricted drivers available anymore.

That would make 8.10 the "newest" version with drivers for your card.  But, you might have to go back to 8.04 -- and that's not supported anymore.

---

