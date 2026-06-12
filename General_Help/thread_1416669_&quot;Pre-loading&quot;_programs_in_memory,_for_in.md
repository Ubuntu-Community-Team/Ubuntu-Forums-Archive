---
title: "&quot;Pre-loading&quot; programs in memory, for instant access?"
date: 2010-02-26
forum: General Help
---

### Post by Gotaro on 2010-02-26
I'm probably not using the right terminology, but is there a way to have programs already loaded in memory, so when I open them they just instantly appear?  Specifically, I want Firefox and Thunderbird to work like that.  I can't stand having a loading cursor for ~5 seconds after they open, so if I decide I want to minimize or exit for any reason, I have to click the buttons with my loading cursor (not as easy as it sounds).

It's not necessarily that I'm impatient and can't wait, just that the illusion of instant open adds a lot to my experience, and definitely not seeing a loading cursor long after FF/Thunderbird is ready to go (I can easily do a search while something is still "loading") would make me feel like it's less buggy/more lightweight.

I was thinking I could just settle for tray icons that they minimize to when I hit the "X," if that wouldn't cause too many problems.  It might even be a better option for Thunderbird :S.

Thanks for any help anyone can give!  And pointing me to other threads is a-okay with me :).

---

### Post by ABCC on 2010-02-26
There's a package called alltray that you may find useful:

alltray - Dock any program into the system tray

You could add something like 'alltray thunderbird' to your sessions' startup applications and have them instantly available from the systray.

hth,

ABCC

---

### Post by themusicalduck on 2010-02-26
There's also a package called preload that you could give a try. It basically does what you're asking for, in that it loads the programs you use the most into the memory so that they start quicker.

I had it installed for a while, but while some programs did seem to start faster, I found that overall my system felt slower. (I only have 1 gig of ram mind.) After removing it, I didn't miss it much and my system did seem to run better.

Might work better for you though. You can find it in synaptic.

---

### Post by oldos2er on 2010-02-26
> **Gotaro said:**
>  is there a way to have programs already loaded in memory, so when I open them they just instantly appear?  

Look into the packages **preload** and **prelink**

[http://ubuntu-snippets.blogspot.com/2008/06/guide-to-faster-ubuntu.html](http://ubuntu-snippets.blogspot.com/2008/06/guide-to-faster-ubuntu.html)

---

### Post by Gotaro on 2010-02-26
alltray seems like a good alternative if nothing else works.  It works exactly like I was talking about :).

I've installed preload and prelink, but I don't see any noticeable difference as of yet.  oldos2er, I followed the instructions from the site you linked, but I don't know if it installed correctly.  When I did "sudo /etc/cron.daily/prelink," nothing happened, so I eventually just had to close out the terminal window and end whatever it was doing.  Does that mean I need to manually start a background process?

Also, I'm considering that this may or may not even solve my problem.  Firefox loads completely, and within the Firefox window my cursor is normal.  It's only when I hover over the window border or my panels that it still shows the loading cursor for a good 10+ seconds.

---

### Post by oldos2er on 2010-02-26
> **Gotaro said:**
> When I did "sudo /etc/cron.daily/prelink," nothing happened, so I eventually just had to close out the terminal window and end whatever it was doing.  Does that mean I need to manually start a background process?


No, that's all you need to do.

---

### Post by Gotaro on 2010-02-26
> **oldos2er said:**
> No, that's all you need to do.
Thanks :).  I do think FF and Thunderbird are loading faster.  Unfortunately, it didn't solve the busy cursor problem when I hover over the window border or panels.  So if I open Thunderbird and check my mail and have nothing, I'm closing with a circle cursor with no pointer :P.  And it seriously does take 10+ seconds for it to go away...:?

---

