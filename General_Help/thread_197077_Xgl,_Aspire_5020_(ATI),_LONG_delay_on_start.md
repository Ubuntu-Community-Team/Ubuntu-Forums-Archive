---
title: "Xgl, Aspire 5020 (ATI), LONG delay on start"
date: 2006-06-15
forum: General Help
---

### Post by e-gandalf on 2006-06-15
I just tried to install Xgl using
[https://wiki.ubuntu.com/CompositeManager/Xgl](https://wiki.ubuntu.com/CompositeManager/Xgl)

My machine is:
Acer Aspire 5024
ATI x700
Turion 1.8 Ghz

After installing Xgl I decided to try to run Gnome default session just to test if it'll work OK.

And what happened is that GDM starts OK, then I log in, and then it displays the wallpaper for about a minute or so before starting gnome session (which works ok then).

I stopped gdm, and tested pure "startx" with "exec gnome-session" in "~/.xinitrc" - same effect.

Any help? Where could I digg for it? It's not any of env variables, since I didn't touch starting scripts for default Gnome...

---

### Post by e-gandalf on 2006-06-15
More testing:

Xgl session has two delays.

First one appears after logging in (like in previous case) then I see the loading screen (this wide small box in the middle with loading foo,foo2,nautilius,foo3), then there's another 1 minute delay and Xgl starts.

---

### Post by e-gandalf on 2006-06-15
Next update. It seems that more apps have similar problem:

I started default Gnome session and:

1) gnome-terminal starts blank, and after 1 minute it blinks and disappears
2) alt+f2 -> gconf-editor, starts after 1 minute

Also logging out delays by one minute.

---

### Post by Lunar_Lamp on 2006-06-15
Well, on my 5024 (basically the same laptop), I couldn't get it to be stable at all - though I didn't put much effort into it.  I must say that I haven't seen anyone with these kinds of issues, but there was a fix that was specifically intedned for x-series ati cards which may be of relevance (I think it was mroe to do with stopping a hard-lock though).

---

### Post by e-gandalf on 2006-06-15
Hmm, so my problem is different. It seems that beside of this 1 minute delay of many tasks (not all, Firefox starts without this delay when I click on Firefox icon), everything works.

My problem is that I see no way to even debug what's wrong in this case :(

---

### Post by eth on 2006-06-15
I put some real effort in trying to install Xgl, but there was no way to making it start...it stopped with the wallpaper on, like yours...I'm running dapper on an Acer 5502, ATI x700. 

if it could be of any help, be sure that :
. you are running on display 1 and not 0 (buggy with ATI graphics)
. your gnome-session isn't running the wrong script (it happens, when you make it save the current session) 
. you gnome-session IS running metacity, which I don't know why disappear when I try to run Xgl.

---

### Post by e-gandalf on 2006-06-15
Did you try to wait a few minutes after the wallpaper appears?
Maybe it's exactly the same as I have...

I'll dig more, but just in case:

How can I revert to previous state if I followed Wiki steps?

---

### Post by eth on 2006-06-16
Nope, in my case nothing happens for at least 10 mins.
To turn back to your previous setting, just undo the steps made to configure it

---

