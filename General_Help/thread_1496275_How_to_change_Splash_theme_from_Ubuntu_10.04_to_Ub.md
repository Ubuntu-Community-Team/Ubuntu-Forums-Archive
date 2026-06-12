---
title: "How to change Splash theme from Ubuntu 10.04 to Ubuntu 9.10?"
date: 2010-05-29
forum: General Help
---

### Post by KingBongo on 2010-05-29
Hi. I would like to change the Splash themes in Ubuntu 10.04 (Lucid) so they look like the ones in Ubuntu 9.10 (Karmic). I would like to get the white blinking Ubuntu logo w/o any text in the center of the screen back. How to do that? 

I like it clean and simple and think the Ubuntu logo (including text) in 10.04 is ugly. I love the one in 9.10. 

Can somebody also help me to disable splash entirely (as an option) so I only have a black screen during boot? It makes boot-time shorter. I tried to replace "quiet splash" with "" (file:/etc/default/grub, line:GRUB_CMDLINE_LINUX_DEFAULT="quiet splash") and yes the splash disappeared but I got a lot of text instead. I don't want that either.

---

### Post by KingBongo on 2010-05-30
Business as usual :P I don't know how many threads I have started without getting any replies at all. Anybody?

---

### Post by ibuclaw on 2010-05-30
Tried Replacing "quiet splash" with just "quiet" ?


Plymouth is tightly integrated into the startup process, so it is a wee bit difficult to remove/replace it.

---

### Post by WorMzy on 2010-05-30
As far as I've seen, there's no way to replace plymouth (10.04 boot splash program) with usplash (boot splash program for 9.10 and previous versions of Ubuntu).

Re-adding "quiet" to your kernel parameters will cull most of the text. I don't think it's possible to have a completely black screen, without creating a completely black splash screen and re-adding "splash" to the kernel parameters.

---

### Post by KingBongo on 2010-05-31
ibuclaw/WorMzy:
Thank you guys! Very helpful and informative, :) I will now try replacing "" with "quiet".

EDIT: Like you said most of the text disappeared. Much better :) However, since neither of my goals were completely met I cannot mark this thread as "solved" yet.

---

### Post by KingBongo on 2010-06-05
Here we go again :) Can somebody who is skilled enough create a theme for Plymouth with only the white Ubuntu logo blinking in the center of the screen on a black background? Exactly like in Ubuntu 9.10. That would be sooooo nice!

---

### Post by egalvan on 2010-06-05
herman has some excellent info on his web site...

here is a direct link to the GRUB2 stuff

[http://members.iinet.net.au/~herman546/p20.html](http://members.iinet.net.au/~herman546/p20.html)


note: this may or may not be exactly what you need... 
you'll have to do some reading...

---

### Post by KingBongo on 2010-06-05
egalvan:
Thank you!

---

### Post by echo6 on 2010-06-05
There are some others, apt-cache search plymouth-theme
They all appear to have the default ubuntu logo, I'm looking at the source code atm trying to get my head around the best way to customize.

Yep, once again a new splash with little relevant documentation :-)  Although I do think Plymouth is the way to go.

---

