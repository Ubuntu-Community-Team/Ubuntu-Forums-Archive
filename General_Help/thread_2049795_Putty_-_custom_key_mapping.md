---
title: "Putty - custom key mapping"
date: 2012-08-29
forum: General Help
---

### Post by isaacjun16 on 2012-08-29
Hi, I'm trying to connect to a Telnet server with putty, so far Im able to do almost everything but some keys don't do what I need, in windows I use QVT/net with a vt220 and some custom keys mapping I would like to be able to use this custom keys on putty. I checked out the configuration file for the custom key mapping for qvt and I found this:

> 70=^[OP
71=^[OQ
72=^[OR
73=^[OS
77=^[[19~
7a=^[[23~

I don't know if this help in something, I would really appreciate any help, thanks. ):P

---

### Post by moserine on 2012-12-18
Have you been able to figure this out?

I'm somewhat stumped--I've switched from Windows to Ubuntu at work, and log into a proprietary telnet server that uses custom key mapping for the F1-F12 keys (plus the SHIFT and CTRL variations of those) that map to something like this:

$1B[17~
$1B[18~
$1B[19~

We use TeraTerm at work, which allows for custom key mapping--I cannot seem to find another telnet client usable in Linux that allows custom key mapping. I've also seen someone write that the only way they were able to get PuTTy to use their custom key mapping was to edit the source code (which is a little beyond me, at the moment).

I was looking at MUD clients (which have more features than standard telnet clients), but it doesn't seem like any of those support custom keymaps, either.

Thinking of just using wine to run TeraTerm, ugh.

---

### Post by moserine on 2012-12-18
TeraTerm works fine in wine, btw. I'm guessing QVT/net would as well.

---

