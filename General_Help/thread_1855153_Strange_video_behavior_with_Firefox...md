---
title: "Strange video behavior with Firefox.."
date: 2011-10-05
forum: General Help
---

### Post by Druegan on 2011-10-05
Hi folks, 

I'm posting this here because I haven't a clue where it might better fit, but for the last couple weeks, I've been having a hell of a time with some graphics issues that are giving me fits, and I'm desperately hoping somebody can talk me through a process of troubleshooting them.

I'm running Ubuntu 10.10 64 bit, nVidia GeForce GTX 460 video card, Acer P235H widescreen monitor, Biostar A770E3 mainboard, 8 gigs of memory, 650w PSU.. AMD Phenom II X6 1055T Processor.. also the proprietary nVidia drivers from the repo.

About 2 weeks ago, there was a system update that came through, and I started developing a weird intermittant screen flicker.  I think the update in question involved Compiz, but I'm really not sure. I'm fairly new to Ubuntu and its parts..

It looked *almost* like the screen was trying to re-draw itself weirdly.. like I could almost see something show up and disappear faster than the eye could follow that showed up as a flicker. 

I'd been running this exact setup for 6 months previous without any trouble..so I started rooting around seeing if I could correct the problem.

I eventually tracked the problem down.. sort of... I run 2 web browsers, side by side.. Chromium, which I do nothing but play Runescape on.. and Firefox, which I use for everything else. I noticed the problem was related to certain webpages in Firefox. 

I've no idea what it is on these pages that's causing the issue.. I'm thinking maybe flash.. but I've uninstalled flash (I think), blocked all javascript with Noscript..  And some of these pages still produce the flicker even with no obvious flash or scripting running. CSS problem maybe?

I even upgraded from Firefox 4 to Firefox 7.. no change.. behavior is still the same.  

I've checked for hardware things.. like the video card getting too hot, or speakers too near the monitor.. nothing's turned up..  it's only on certain pages.. and it can vary in intensity from just a flicker to half the screen going black for periods of time, colors whiting out next to a flicker line... 

Can anybody help me diagnose what's maybe going on here, or suggest possible fixes?  Is there some way to roll back that last Compiz update set, or something maybe that the Compiz update would have changed?  Driver uninstall/reinstall or something?

Thanks in advance for any help.
Sincerely, 
  Druegan

---

### Post by pqwoerituytrueiwoq on 2011-10-05
what is the nvidia driver version?
[IMG]http://i.imgur.com/LeNvT.png[/IMG]
does [google body]("http://bodybrowser.googlelabs.com/") work? (webgl test)

---

### Post by Druegan on 2011-10-05
Driver version is: 260.19.06

I looked into updating the drivers from the nVidia site, but they're in some kind of weird .run format that I haven't a clue what to do with.

And yeah, Google Body appears to work fine.. I'm not seeing any kind of flicker or the like.. (although this is something I hadn't seen before, now I must compulsively play with it. lol)

---

### Post by Druegan on 2011-10-06
Bit of an update... on at least one page, the "screen flicker" seems to be an attempt to re-draw the display at a spot that is not centered on the screen.  The odd bit is that it changes as I scroll up and down.. certain parts of the page produce a slower flicker of the top half of my entire display..(firefox,desktop, whatever is open) flashing across the bottom 40% or so of the screen.  

It's only firefox that seems to cause this, and only on certain pages..  (the page that caused this identifiable image flicker at certain points is [http://blog.sudobits.com/2010/10/24/how-to-install-gyachi-in-ubuntu-10-10/](http://blog.sudobits.com/2010/10/24/how-to-install-gyachi-in-ubuntu-10-10/))..   One that causes all sorts of crazy graphical weirdness, such as "bleaching out" parts of the screen (like a photo overexposure) with flashes to half-screen black is [http://damo-qigong.net/wudang/wudang.htm](http://damo-qigong.net/wudang/wudang.htm)... but only when the browser views the very top of the screen..  Just now it had my whole monitor going black and barely showed anything until I mouse-wheel scrolled it down past that spot..

I don't know if these examples help anybody, but this is most vexing, and any help would be greatly appreciated.

---

### Post by Druegan on 2011-10-07
Aight.. solved it, although I'm not sure how..

did a total uninstall and reinstall of compiz and related packages, then uninstalled the old nvidia drivers and finally figured out how to upgrade to the newest versions.. seems to have done the trick.. no more weird display effects. :)

---

