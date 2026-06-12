---
title: "Thunderbird Won't Launch Without Safe-Mode"
date: 2010-09-16
forum: General Help
---

### Post by jrolland on 2010-09-16
Hello, all!

I have a problem with Thunderbird.

I have the Lightning and Enigmail extensions added, and Thunderbird won't launch with these extensions unless I first open a terminal and give a "thunderbird --safe-mode", wait for Thunderbird to launch in safe mode, quit Thunderbird, then relaunch Thunderbird normally,

I looked at Thunderbird's man page, and was unable to find a debug mode; does anyone know if Thunderbird has a debug mode?

I am running Ubuntu 10.04 Lucid Lynx, Thunderbird 3.1.1, Lightning 1.0b2 and Enigmail 1.1.2.

(Note that, on a different computer, I am running Kubuntu 10.04, same versions of Thunderbird, Lightning, and Enigmail, and have no problems. Also, on a third computer, I am running Linux Mint 9 Isadora, same versions of Thunderbird, Lightning, and Enigmail, and also have no problems.)

Any assistance you can provide is appreciated.

---

### Post by jrolland on 2010-09-16
Update: I just updated Thunderbird to 3.1.4, same versions of Lightning and Enigmail, and have the same issues.

---

### Post by wilee-nilee on 2010-09-16
> **jrolland said:**
> Update: I just updated Thunderbird to 3.1.4, same versions of Lightning and Enigmail, and have the same issues.

So just out of curiosity I installed both in the same version of Tbird, in maverick, and without setting up the enigmail thunderbird opens as normal. I suspect it is this program that is causing them I don't know how though. I would remove one at a time to see which one is causing the problem. Then if it is enigmail then more specialized searches for you can be done and others will know where the problem lays.

I am experiencing Tbird crashing or alltray which I use to auto-open Tbird at startup, with enigmail installed. It seems to be okay now with only Lightning 1.0b2 installed. Enigmail is a beta release, so I would wonder if it just needs some more development.

---

### Post by jrolland on 2010-09-18
Thanks for replying!

I did some testing, and both Enigmail *and* Lightning force me to go through the --safe-mode routine.

And I was wrong: on my Kubuntu 10.04 box, at least, I am running Thunderbird 3.0.x (3.0.8, I believe, but I'll double-check that); that explains why, on that computer, at least, I don't observe the behavior.

Hope this helps.

---

### Post by wilee-nilee on 2010-09-18
> **jrolland said:**
> Thanks for replying!

I did some testing, and both Enigmail *and* Lightning force me to go through the --safe-mode routine.

And I was wrong: on my Kubuntu 10.04 box, at least, I am running Thunderbird 3.0.x (3.0.8, I believe, but I'll double-check that); that explains why, on that computer, at least, I don't observe the behavior.

Hope this helps.

If I wanted those addons I guess I would just purge the version you have and install the earlier described here and try it.

---

### Post by basily on 2010-10-14
I have a similar problem, except I DON'T have enigmail nor lighting installed.

Thunderbird will not start normally for me, unless I first start it in safe mode, make ANY change to a plugin (enable/disable/install, etc), then close. I can then start Thunderbird normally, and if I close it, I can restart it normally again for as long as I don't restart my computer.

When I restart my computer I have to go through the whole safe-de thing again...

Mysterious...

---

### Post by LikenBear on 2010-10-26
> **jrolland said:**
> Hello, all!

I have a problem with Thunderbird.

I have the Lightning and Enigmail extensions added, and Thunderbird won't launch with these extensions unless I first open a terminal and give a "thunderbird --safe-mode", wait for Thunderbird to launch in safe mode, quit Thunderbird, then relaunch Thunderbird normally,

I looked at Thunderbird's man page, and was unable to find a debug mode; does anyone know if Thunderbird has a debug mode?

I am running Ubuntu 10.04 Lucid Lynx, Thunderbird 3.1.1, Lightning 1.0b2 and Enigmail 1.1.2.

(Note that, on a different computer, I am running Kubuntu 10.04, same versions of Thunderbird, Lightning, and Enigmail, and have no problems. Also, on a third computer, I am running Linux Mint 9 Isadora, same versions of Thunderbird, Lightning, and Enigmail, and also have no problems.)

Any assistance you can provide is appreciated.

This problem has been bugging me (OK... corny pun) for a couple of months. I don't have a solution. But I have a work around.

I'm running Ubuntu 10.04 Lucid L and Thunderbird 3.1.2 (but Thunderbird 3.1.1 didn't work with Enigmail 1.1.2 either)

Whatever the root cause is seems to happen after Enigmail gets registered. Turns out that on first startup after installing Enigmail 1.1.2, Thunderbird runs. Of course after the first time, it's registered and the trouble begins.

Try removing

<your-path>/.mozilla-thunderbird/<path-detail>.default/xpti.dat and compreg.dat

This forces re-registration of Enigmail each time. But it seems to work.

I've ended up testing for the existence of each file at the top of the /usr/bin/thunderbird start up script and removing them if present.

Thunderbird now starts up each time.

---

