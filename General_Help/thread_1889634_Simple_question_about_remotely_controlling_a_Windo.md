---
title: "Simple question about remotely controlling a Windows PC"
date: 2011-12-01
forum: General Help
---

### Post by TheBearNecessities on 2011-12-01
Anyone do this regularly from linux?

I'm just trying to control my windows PC from my lubuntu laptop.  They are both on the same LAN (at home).

I have installed Tight VNC server on the windows PC and tight vnc viewer on the lubuntu laptop.

I can connect great but **the bottom edge of the windows screen is not shown on my lubuntu screen (wouldn't normally mind butit's a decent chunk of the screen and it means i can't see or use the takbar)**.

**Anyone seen this issue before?  **I have reduced the windows pc screen resolution but that didn't help.

**Is there any other good software** (easy to use i.e with gui) for LAN remote control?

---

### Post by SteveDee on 2011-12-02
> **TheBearNecessities said:**
> Anyone do this regularly from linux?...Is there any other good software...for LAN remote control?

You can create a Remote Desktop session on/from a Windows machine using the Remote Desktop Protocol (RDP).

Windows server supports multi-user sessions, but desktop versions (like WinXP and Win7) only allow one session at a time.

On your Windows machine you may need to enable Remote Desktop if its not already enabled.

On your Linux machine go to Synaptic and install: rdesktop

From your Linux terminal type:-
```

rdesktop myWinBox

```
...where myWinBox is the Windows computer name.
That's all you need to get a blue Windows login screen.

You may like to extend this command to include your Windows user name, set the screen size, set the bandwidth and add local sound.

Here is an example:-
```

rdesktop -u TheBear -f -x l -r sound:local myWinBox

```

Have fun!

---

### Post by TheBearNecessities on 2011-12-04
> **SteveDee said:**
> You can create a Remote Desktop session on/from a Windows machine using the Remote Desktop Protocol (RDP).

Windows server supports multi-user sessions, but desktop versions (like WinXP and Win7) only allow one session at a time.

On your Windows machine you may need to enable Remote Desktop if its not already enabled.

On your Linux machine go to Synaptic and install: rdesktop

From your Linux terminal type:-
```

rdesktop myWinBox

```
...where myWinBox is the Windows computer name.
That's all you need to get a blue Windows login screen.

You may like to extend this command to include your Windows user name, set the screen size, set the bandwidth and add local sound.

Here is an example:-
```

rdesktop -u TheBear -f -x l -r sound:local myWinBox

```

Have fun!

You sir, are a star.  Thanks so much for taking the time to reply.  I'll give this a go today.  I managed to get remote control working (and I could see the whole screen) using teamviewer, but I really want one that doesn't go via the internet so that it's fatser.  Thanks again, will report back :)

---

### Post by SteveDee on 2011-12-04
> **TheBearNecessities said:**
> ....but I really want one that doesn't go via the internet so that it's faster....

Its certainly very quick when run on 2008 server on a fast network ([http://ubuntuforums.org/showthread.php?t=1866992](http://ubuntuforums.org/showthread.php?t=1866992)) and was still much faster than vnc when running a test at home on Win7 via a 54Mbps wifi.

I really want to get RDP to work Linux-to-Linux but have not had any success ([http://ubuntuforums.org/showthread.php?t=1860792](http://ubuntuforums.org/showthread.php?t=1860792)). So if you discover any clues on this, please let me know.

---

### Post by TheBearNecessities on 2011-12-05
Thanks Steve.

I am using rdesktop now and its very fast, and I can now see the whole of my windows screen as long as I use rdesktop in full screen mode (the -f switch).

Thanks again for taking the time to help.

Ps.  if anyone is reading this thread and is going to use the rdesktop solution then remember that you might need to change some settings in windows (right click on my computer and look at the tabs; there's a tab called sharing/remote something like that).  also to get out of full screen you press CNTRL-ALT-ENTER.

---

### Post by SteveDee on 2011-12-05
> **TheBearNecessities said:**
> ...and I can now see the whole of my windows screen as long as I use rdesktop in full screen mode...

You should also be able to see the whole Windows screen in a window by replacing "-f" with "-g 90%" or "-g 1000x740" (or what ever is appropriate). The advantage of this is that you can get to your Linux desktop or minimise the Windows window.

I'm glad its worked out for you.

---

