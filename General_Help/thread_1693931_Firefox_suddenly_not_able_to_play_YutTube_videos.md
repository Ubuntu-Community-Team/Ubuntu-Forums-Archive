---
title: "Firefox suddenly not able to play YutTube videos"
date: 2011-02-23
forum: General Help
---

### Post by imbjr on 2011-02-23
I've turned off adblock and flashblock, and still no YT video will play.

Flash video works on Vimeo, and Chromium with its own version of adblock works with YouTube.

Erm ... I'm somewhat stumped!

---

### Post by imbjr on 2011-02-23
> **imbjr said:**
> I've turned off adblock and flashblock, and still no YT video will play.

Flash video works on Vimeo, and Chromium with its own version of adblock works with YouTube.

Erm ... I'm somewhat stumped!

Well, running Firefox via the terminal shows:

```
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory

(<unknown>:3939): Gdk-WARNING **: XID collision, trouble ahead
```

which is odd, because I've got an ATI card.

---

### Post by evenrelation on 2011-02-23
Very same problem here.

I'm completely lost.

---

### Post by imbjr on 2011-02-23
> **evenrelation said:**
> Very same problem here.

I'm completely lost.

I just stepped back the version of Flash I'm using and that did not fix it. I believe the issue is somehow related to the recent hardware acceleration feature added to Flash, but I could have swore things were ok after that last update.

---

### Post by ShadowDeath on 2011-02-23
I had the same problem but i think i fixed it... but i don't know the source of the problem...

Take a look here: [http://ubuntuforums.org/showthread.php?p=10487730](http://ubuntuforums.org/showthread.php?p=10487730)

---

### Post by evenrelation on 2011-02-23
For some unexplainable reason I am able to watch embedded videos but not videos directly on the YouTube webpage.

---

### Post by IWantFroyo on 2011-02-23
What happens when you run this:
```
 sudo apt-get install libvdpau_nvidia
```

if this doesn't, try libvdpau_nvidia*.

---

### Post by imbjr on 2011-02-23
> **IWantFroyo said:**
> What happens when you run this:
```
 sudo apt-get install libvdpau_nvidia
```

if this doesn't, try libvdpau_nvidia*.

```

E: Unable to locate package libvdpau_nvidia*
E: Couldn't find any package by regex 'libvdpau_nvidia*'

```

The thing is, I don't have an Nvidia card anyway. I'm lumbered with an ATI card.

---

### Post by vidwarren on 2011-02-23
> **imbjr said:**
> I've turned off adblock and flashblock, and still no YT video will play.

Flash video works on Vimeo, and Chromium with its own version of adblock works with YouTube.

Erm ... I'm somewhat stumped!

Same problem (although I don't have Chromium). For a temporary solution, try turning on Private Browsing (in Tools) that worked for me.

---

### Post by imbjr on 2011-02-23
> **vidwarren said:**
> Same problem (although I don't have Chromium). For a temporary solution, try turning on Private Browsing (in Tools) that worked for me.

No dice.

The really odd thing about this, is that it's only YT that's affected. Vimeo videos play ok.

---

### Post by evenrelation on 2011-02-23
MetaCafe also works fine.

---

### Post by IWantFroyo on 2011-02-23
Hmmm...
Try this:
System-Administration-Synaptic Package Manager- *search* vdpau-va-driver
Does that fix it? Good luck.

---

### Post by staticpunk84 on 2011-02-23
i had the same issue but I clicked that speaker on top of the desk top and went into some options and clicked everything that was checked muted and did the speaker test and their it was sound was working sorry Im using windows right now or I would be more step by step

---

### Post by imbjr on 2011-02-23
> **IWantFroyo said:**
> Hmmm...
Try this:
System-Administration-Synaptic Package Manager- *search* vdpau-va-driver
Does that fix it? Good luck.

Well that seems to have stopped the error messages I was seeing at the console, but no movies are loading @ YT.

---

### Post by evenrelation on 2011-02-23
> **IWantFroyo said:**
> Hmmm...
Try this:
System-Administration-Synaptic Package Manager- *search* vdpau-va-driver
Does that fix it? Good luck.
Nope, still none.

---

### Post by vidwarren on 2011-02-23
Yeah, I had the same thing with Vimeo working. I could play some embedded Youtube videos too (though the more recent embeds are iframes and wouldn't work).

One more thing to try is adding Flash-Aid: [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

Flash-Aid checks which version of Flash you need and updates for you. It didn't fix it for me (maybe it helped in conjunction with Private Browsing). However, it has seemed to help other people with the same problem.

---

### Post by imbjr on 2011-02-23
> **vidwarren said:**
> Yeah, I had the same thing with Vimeo working. I could play some embedded Youtube videos too (though the more recent embeds are iframes and wouldn't work).

One more thing to try is adding Flash-Aid: [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

Flash-Aid checks which version of Flash you need and updates for you. It didn't fix it for me (maybe it helped in conjunction with Private Browsing). However, it has seemed to help other people with the same problem.

No effect, as far as I can see. I even went into /etc/adobe/mms.cfg and made sure:

EnableLinuxHWVideoDecode=0

was set. The script that Flash-Aid uses removes the setting, but to ensure it wasn't defaulting to 1 I set to as above.

---

### Post by corncob on 2011-02-23
In response to an article in Ubuntu User Magazine I just installed minitube: [http://flavio.tordini.org/minitube](http://flavio.tordini.org/minitube)
```
sudo add-apt-repository ppa:neverfelde/minitube
sudo apt-get update
sudo apt-get install minitube
```
Its not supposed to need flash player.  I don't see any difference but then I could already play youtube videos, at least after I had installed libdvdcss2 and followed the tutorial at [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by vidwarren on 2011-02-24
For me this has just fixed itself. No idea why and I haven't changed  anything since it wasn't working. Maybe it was a glitch with Youtube.

Anybody else's suddenly working?

---

### Post by evenrelation on 2011-02-24
> **vidwarren said:**
> For me this has just fixed itself. No idea why and I haven't changed  anything since it wasn't working. Maybe it was a glitch with Youtube.

Anybody else's suddenly working?
Yup, fixed here as well.

---

### Post by imbjr on 2011-02-24
> **evenrelation said:**
> Yup, fixed here as well.

Me too as they said.

Mmm, what was that all about? Something YT did I can only assumed.

---

### Post by KJ KJ KJ on 2011-03-03
I encountered this flash plugin problem today with Firefox. 
I was running Ubuntu 10.10 inside VirtualBox on top of WinXP.

Videos on the YouTube site gave the "flash plugin has crashed" warning, those YouTube videos embedded in other sites did not.

I fixed it by (a) going to private browsing where it worked fine (b) then disabling hardware acceleration by right-click and choosing Settings and finally (c) coming out of private browsing to "normal" browsing, where it worked as it should.

---

