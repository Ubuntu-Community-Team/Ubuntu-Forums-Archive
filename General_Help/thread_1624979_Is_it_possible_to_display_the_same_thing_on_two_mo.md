---
title: "Is it possible to display the same thing on two monitors simultaneously?"
date: 2010-11-18
forum: General Help
---

### Post by trpnblies7 on 2010-11-18
I'm planning on getting an HDTV soon, and I'd like to be able to hook it up to my computer so that I can watch movies on it through my computer. I *don't* want to have dual monitors in the traditional sense where my desktop is spread across two screens. Rather, I just want my desktop to appear exactly the same on both my monitor and TV.

Is this possible? And if so, what would be the best way to go about doing this? My video card has two DVI ports, so I was planning on running a cable from the unused port to my TV and using a DVI-VGA adapter. Or would I be better off getting a TV with an S-video port, which I also have on my card, and connecting it that way?

Any advice is appreciated. Thank you.

---

### Post by AlphaLexman on 2010-11-18
You DON'T want to plug into two different video outputs!

You DO need a 'hardware' video splitter with outputs to your monitor and HDTV.

---

### Post by trpnblies7 on 2010-11-18
I'm not quite sure I understand. Are you saying that instead of plugging a cable into both of my DVI ports, with one port going to my monitor and the other to my TV, instead I should just use one DVI port but use a splitter? Kind of like how I use a cable splitter so my TV and modem are hooked up to the same cable?

---

### Post by tgm4883 on 2010-11-18
> **AlphaLexman said:**
> You DON'T want to plug into two different video outputs!

You DO need a 'hardware' video splitter with outputs to your monitor and HDTV.

Um no. I have dual monitors set up without a splitter on my workstation. Now there are some video cards that have a special adapter that split it to multiple monitors, but I haven't seen many of those as they appear to be an exception to the rule.

> **trpnblies7 said:**
> I'm not quite sure I understand. Are you saying that instead of plugging a cable into both of my DVI ports, with one port going to my monitor and the other to my TV, instead I should just use one DVI port but use a splitter? Kind of like how I use a cable splitter so my TV and modem are hooked up to the same cable?

Don't do that. You can totally have the same image on both monitors. There is an option for it in System > Preferences > Monitors. Take a look at my screenshot.

---

### Post by trpnblies7 on 2010-11-18
Ah, thank you! I didn't even realize that option was there.

---

### Post by jocko on 2010-11-18
> **AlphaLexman said:**
> You DON'T want to plug into two different video outputs!

You DO need a 'hardware' video splitter with outputs to your monitor and HDTV.
Nonsense. All video cards I have ever had have been able to do exactly what trpnblies7 asks for.
As long as it has two (or more) outputs, it is possible to clone the desktop to the second screen. With and nvidia card and the proprietary driver, you set it up very simply through nvidia's X server settings program.
With any card or integrated gpu (ati, nvidia or intel) running on open source drivers, gnome-display-properties allows you to choose to either extend the desktop or clone the output very simply, and it has never failed to work for me through vga, dvi, s-video or hdmi...

---

### Post by trpnblies7 on 2010-11-18
I do have an nvidia card and the proprietary drivers. Glad to hear this sounds like a pretty simple thing to do. Thanks!

---

### Post by jocko on 2010-11-18
> **trpnblies7 said:**
> I do have an nvidia card and the proprietary drivers. Glad to hear this sounds like a pretty simple thing to do. Thanks!
You're welcome.

But there are a few things that may not be entirely obvious, so I might as well give you some help...
Once both screens are connected, open up the nvidia X-server settings program (Under System-->Administration) and go to the "X Server Display Configuration" page.
This page should show you that there are two displays, but that one is inactive. To activate the second screen, just highlight it with a mouse click, click the "configure" button, and select twinview. Then just drag one of the screens until it covers the other one (which will result in the same output on both screens). Then click apply.

One small thing is that if the two displays have different resolutions, the smaller one will not show the entire image (but you can of course set both displays to the same resolution to avoid that problem).

---

### Post by trpnblies7 on 2010-11-18
Great to know! Once I get the TV I'll give this a try.

---

### Post by The Cog on 2010-11-18
One possible hickup - If you want the same display on both monitors, it has to figure out a resolution that is compatible with both monitors. This might mean using a fairly low resolution, or having black bars on one of them where the image is cropped to the smaller screen's pixcel size.

---

### Post by trpnblies7 on 2010-11-18
I had a feeling that could be an issue, especially since my monitor uses a 16:10 aspect ratio.

---

### Post by tgm4883 on 2010-11-18
> **The Cog said:**
> One possible hickup - If you want the same display on both monitors, it has to figure out a resolution that is compatible with both monitors. This might mean using a fairly low resolution, or having black bars on one of them where the image is cropped to the smaller screen's pixcel size.

No. My 1680x1050 (16:10) and 1280x1024 (5:4) monitors disagree with your statement

:EDIT:

Sorry, forgot the original intent of the OP. This may in fact be the case since you want both screens to show the same image

---

### Post by AlphaLexman on 2010-11-18
> **jocko said:**
> Nonsense. All video cards I have ever had have been able to do exactly what trpnblies7 asks for.
I didn't know, sorry for the misinformation!

---

