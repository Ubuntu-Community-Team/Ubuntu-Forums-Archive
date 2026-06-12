---
title: "No touchpad scroll function"
date: 2011-09-04
forum: General Help
---

### Post by bilijoe on 2011-09-04
This is kind of a re-hash of a thread that was marked 'solved' and died out in May of last year.

I have an HP Pavilion dm1--not a Netbook, per se', but almost. I recently restricted the Windows 7 that came on it to a tiny little partition, and installed Ubuntu 11.04 as the primary OS. Most things went really smoothly, except now I have no scroll function from the touch-pad. In an old thread (#1467503) I found reports of similar problems (in version 10.04), and a "workaround". This seemed to fix things for most people, the thread was marked 'solved' and died out.

However, it's now more than a year later, the alluded-to "fix in an upcoming version" either never went in, or doesn't help in my case. I ran "modprobe -r -v psmouse" and "modprobe -v psmouse proto=imps" from a root terminal. Both seemed to do their jobs, but had no effect on my 'no scrolling' problem. All the touch-pad functions work fine under Windows 7, but I don't want to run Windows--I'm in Love with [Ubuntu] Linux.

:confused:Is anyone else [still] having this problem? Does anyone know if there's been any more research done on it, or any attempt to fix it within the OS. Are there any newer or better workarounds or patches anyone knows of. Not having a scroll feature on the touch-pad makes using the interface kind of clunky, so I really want to get this to work right.:( Any help will be greatly appreciated.:popcorn:

---

### Post by bilijoe on 2011-09-07
Is this really such a mystery? This question has showed up countless times, in countless forums, _*starting as early as **2005***_*!* :confused::( 

If a proper fix cannot be found and incorporated into the kernel REAL SOON, I strongly suggest that the Ubuntu Developers (and others, as well as some computer manufacturers) post a WARNING, notifying [potential] users that [SIZE=2]*"This Product is NOT COMPATIBLE with ALPS Touch-pads!"*[/SIZE]

This is beginning to seem ridiculous. **2005** folks; not 6 or 8 months ago, but **6 YEARS ago**... and it clearly affects a lot of people. Screw the other OSs, can't we at least get this item fixed, once and for all? At least in our Beloved Ubuntu!

_**Developers, please make this one a priority**_. I'm sure a ton of users will thank you.;):popcorn::popcorn:

---

### Post by bunny rabbit on 2011-09-25
I can't help you with the touchpad but for what it's worth; I own a Lenovo G550 and have an Alps touchpad which is recognized as a Ps/2 mouse. So I can't scroll or multitouch either. I think it's terrible too because I love to use the touchpad.
But I have learned that it is because the Alps driver still is closed source. That is the reason why the touchpad is not working properly with Ubuntu and why I remain patient.
All I can do is wait and stay on the lookout because I'm not educated enough regarding computers. I hope that you can wait too with the knowledge that you're not the only one with this problem.
By all means let people know if/when you do find a solution!
All the best,

---

### Post by bilijoe on 2011-09-25
Thanks for responding. I was beginning to think I was imagining all the posts I see elsewhere that refer to this problem. 

I really don't want to get back into hardware/device driver programming, but if I have to, I will. First, I'm going to try some back door, and black hat approaches. This is probably going to take a lot of research, and I can't read as fast as I used to, so it may take me a while, but I WILL find a fix for this. This situation is entirely too short-sighted and stupid, not to mention arrogant (on ALPS part) for users, or the industry to tolerate.

If you are versed in the use of the social sites (FaceBook, Twitter, etc)--I am not--you might try to trigger a campaign to inundate ALPS, _and_ all the _computer_ _manufacturers_ who use the ALPS touch pads, with emails, snail-mails, phone calls, and posts on all the appropriate forums, to severely castigate both ALPS, and the manufacturers who use their touch pads, for failure to provide proper support for their products. Also, a firm promise to the computer manufacturers to boycott their products in the future, unless they _*quickly*_ provide, and make readily available a proper fix for this problem.

If I were a manufacturer, at this point, I'd be calling ALPS to inform them that either they make a retro-fit fix available, for free, to everyone who requests it, or I'd be canceling all standing orders, and switching to another source for touch pads.

---

### Post by Clicksights on 2011-09-27
Maybe a good idea to make one topic about these touchpad/mouse problems!
And make it a sticky!
It seems to be a really big problem for a lot of laptops.

[http://ubuntuforums.org/showthread.php?t=1841660](http://ubuntuforums.org/showthread.php?t=1841660)
[http://ubuntuforums.org/showthread.php?t=1772092](http://ubuntuforums.org/showthread.php?t=1772092)
[http://ubuntuforums.org/showthread.php?t=1850443](http://ubuntuforums.org/showthread.php?t=1850443)
[http://ubuntuforums.org/showthread.php?t=1734886](http://ubuntuforums.org/showthread.php?t=1734886)
[http://ubuntuforums.org/showthread.php?t=1546730](http://ubuntuforums.org/showthread.php?t=1546730)

Too just name a few from the last day alone!!!
This is crazy! 
There must be a better solution than no solution!

---

### Post by bilijoe on 2011-10-01
> **Clicksights said:**
> Maybe a good idea to make one topic about these touchpad/mouse problems!
And make it a sticky!
It seems to be a really big problem for a lot of laptops.

[http://ubuntuforums.org/showthread.php?t=1841660](http://ubuntuforums.org/showthread.php?t=1841660)
[http://ubuntuforums.org/showthread.php?t=1772092](http://ubuntuforums.org/showthread.php?t=1772092)
[http://ubuntuforums.org/showthread.php?t=1850443](http://ubuntuforums.org/showthread.php?t=1850443)
[http://ubuntuforums.org/showthread.php?t=1734886](http://ubuntuforums.org/showthread.php?t=1734886)
[http://ubuntuforums.org/showthread.php?t=1546730](http://ubuntuforums.org/showthread.php?t=1546730)

Too just name a few from the last day alone!!!
This is crazy! 
There must be a better solution than no solution!

I agree, but it shouldn't become sticky until we have a [real] solution for it. I've done a lot of research, and I think I'm closing in on a solution but, at this point, it looks like it might be the kind of thing only a relatively experienced user could do. When I do get something working, I will see how much it can be simplified. Keep checking here every few days. I figure I'm still a week or so away from success.;)

---

### Post by bunny rabbit on 2011-10-16
bug #550625 is probably going to do it for you. Seth Forshee has written a fix. [http://goo.gl/B5U6i]("http://goo.gl/B5U6i")
I have my touchpad working how it's supposed to.
I hope this helps.

---

