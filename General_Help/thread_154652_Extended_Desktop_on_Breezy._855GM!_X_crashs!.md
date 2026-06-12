---
title: "Extended Desktop on Breezy. 855GM! X crashs!"
date: 2006-04-03
forum: General Help
---

### Post by cpscotti on 2006-04-03
This is tho only issue not solved on my ubuntu.](*,) ](*,) ](*,) 
No solution in this site.:-? 
And I found a lot of people with this problems but none solution!

I had already tryed a lot of xorg.conf configurations. Mosto of them are linked in the end of the post.

What Happens: When I define in my

[COLOR="DarkRed"]	Screen 1 "Screen0" LeftOf "Screen1"[/COLOR] ;) 

statement in ServerLayout, X crashs before showing GDM.

I say "X crashs" because it stops showing a blank gray screen, with two small white rectangles, onte in the upper middle of the screen and other in the upper left.
When in this screen: no response for Ctrl + Alt + F(n) nor for Ctrl + C or Ctrl + Alt + Backspace. Only way out: Ctrl + alt + del!

Viewing the log file, no errors! The only statement that seems to be relevant is:
i810(1) No usable Configuration
(something like this... but in a few hours I'll put a link to the whole log file!)
 
I was told the relevant point on xorg.conf to configure was the device(s) definition, so down  comes a lot of Xorg.conf(s) I tryed!
(some of them have the string: **Screen 1 "Screen0" LeftOf "Screen1"**
are commented, but it was tested without the # (I just putted it there to start X properly after a Crash loop! (I needed to start recovery mode to get out of that!) )

[http://b.1asphost.com/cpscotti/2_screen.ext.conf.txt]("http://b.1asphost.com/cpscotti/2_screen.ext.conf.txt")
[http://b.1asphost.com/cpscotti/2_screen.ext.conf2.txt]("http://b.1asphost.com/cpscotti/2_screen.ext.conf2.txt")
[http://b.1asphost.com/cpscotti/2_screen.ext.conf3.txt]("http://b.1asphost.com/cpscotti/2_screen.ext.conf3.txt")
[http://b.1asphost.com/cpscotti/xorg.conf3.TEST.txt]("http://b.1asphost.com/cpscotti/xorg.conf3.TEST.txt")

[Cloned External Monitor, putting this here just to show a sample "stable" correct configuration of my xorg.conf ]("http://b.1asphost.com/cpscotti/2_screen.clone.conf.txt")


82852/855GM Integrated Graphics Device
Dell Laptop 100L

Thanks in advance!:D

---

### Post by cpscotti on 2006-04-03
Adding two log files!

Both crash at the same line for diferent xorg.conf configurations!

[First one]("http://b.1asphost.com/cpscotti/Xorg.0.log.txt")

[Second one]("http://b.1asphost.com/cpscotti/Xorg.0.log.old.txt")

---

