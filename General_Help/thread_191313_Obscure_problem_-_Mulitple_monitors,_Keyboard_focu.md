---
title: "Obscure problem - Mulitple monitors, Keyboard focus and Mythtv"
date: 2006-06-07
forum: General Help
---

### Post by speedsix on 2006-06-07
Hi,

My problem is a little obscure, I have a dualhead video card with multiple monitors (one is a tv). This works fine, my Xorg.conf has something like..

Screen 0 "monitor"
Screen 1 "tv" LEFTOF "monitor"

I run MythTV frontend on the tv. The problem is, if I start using the pc from the monitor MythTV loses focus and the menu stop functioning properly.

I basically want the tv to have independant keyboard focus, I have thought of running 2 seperate X servers. AFAIK this requires mulitple graphics cards and isn't possible with just a single dualhead card.

Now I know you can run multiple X 'sessions' on virtual terminals but can I run a seperate X session on the second screen which runs Mythtv that has it's own mouse focus? 
Maybe with..

xinit -- mythfrontend :1

But isn't my dual screen setup as defined in xorg.conf using the tv as "screen 1"?

Totally confused :???:

Thanks

Dom

---

### Post by theShaggy on 2008-04-29
This message was two years old with no response, and I'm having the same problem with Hardy Heron and MythTV.

It seems to only happen with Compiz enabled, which I also use "compiz --sm-disable --only-current-screen &" for Compiz since it doesn't like trying to run the eye candy on both screens at once.

It honestly didn't give me this problem (worked fine for at least three months) until February, and randomly started happening when I used Compiz.

---

