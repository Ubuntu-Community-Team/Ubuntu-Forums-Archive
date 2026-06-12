---
title: "Problems with sound and closing programs"
date: 2009-11-27
forum: General Help
---

### Post by Nanofuture on 2009-11-27
So I have two problems which may or may not be related:

First is that when I play games (stuff downloaded from the software center like Battle for Wesnoth or the Stella Atari emulator) the sound will typically work for a little bit and then stop.

Second is that when I try to close these games, they will not close.  I end up having to kill the process to get them to stop (end process does nothing).

I think these might be related as the only programs that seem to have the closing problem also have the sound issue.  Programs that don't have any sound problems (like Firefox, empathy, etc.) also don't have any closing problems.

I am running 64 bit Ubuntu 9.10.  Any ideas?

---

### Post by Nanofuture on 2009-11-27
Ctrl B for bump

---

### Post by Ozor Mox on 2009-11-28
Sorry no help here, just to say I also have this problem. Especially noticeable with Wesnoth. If I use anything else that makes sound like Rhythmbox, Wesnoth will go silent, even if I close Rhythmbox. Started since my update to 9.10 :(

---

### Post by 542 on 2010-02-11
I have the exact same problems with Wesnoth. Tried running it from the command line to see if it output any useful info but nothing special.

9.10, 64-bit - interested if anyone has solved it.

---

### Post by 542 on 2010-02-11
sudo apt-get install libsdl1.2debian-pulseaudio

Seems to do the trick. Apparently this is fine to do in Ubuntu as it uses pulseaudio anyway, maybe not so good in K/X'buntus.

Should be fixed in Lucid.

BTW, great game!

---

### Post by Admiral_Payne on 2010-02-20
> **542 said:**
> sudo apt-get install libsdl1.2debian-pulseaudio
Having same problem, going to try this now :-)

Also 9.10 x64 edition here.

Edit: Yep it works :-) Sweet

---

### Post by Nanofuture on 2010-03-10
> **542 said:**
> sudo apt-get install libsdl1.2debian-pulseaudio

Seems to do the trick. Apparently this is fine to do in Ubuntu as it uses pulseaudio anyway, maybe not so good in K/X'buntus.

Should be fixed in Lucid.

BTW, great game!

Great fix!  Thanks!

---

