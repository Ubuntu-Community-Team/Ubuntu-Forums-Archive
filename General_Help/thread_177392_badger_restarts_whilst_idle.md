---
title: "badger restarts whilst idle"
date: 2006-05-16
forum: General Help
---

### Post by Nimbus_p12 on 2006-05-16
Hi All,

been using breezy badger for a few months now as my main internet/email OS, ( just stuck with XP for COD2... :( ) anyhow I noticed the other day that..

If I leave my desktop doing nothing for about 10 minutes, the whole pc reboots !
I can actually use the pc for hours on end in badger, with no problems at all, ( running mp3s, email, www, downloads etc ), but if its left idling it restarts all on its own...

Where can I get some kind of system logs, or restart data so that I can try and figure out what the problem is ?

cheers,
Nimbus

---

### Post by tseliot on 2006-05-16
Are you using proprietary drivers for your graphic card (e.g. nvidia, fglrx, etc.)?

If so, reinstall the driver and the problem (it it depends on that) should disappear.

---

### Post by Nimbus_p12 on 2006-05-16
yes, I'm using the latest Nvidia drivers for my 7900gt..

I'll give that a go, cheers :)

Nimbus

---

### Post by soze on 2006-05-16
I just started having a similar problem.
When anything 3d tries to run (game, screensaver, etc.) X crashes and logs me out.

This is a very new phenomenon (last 48 hours or so).

I'm running Dapper with the nvidia driver.

Any ideas?

---

### Post by tseliot on 2006-05-16
[QUOTE=soze]I just started having a similar problem.
When anything 3d tries to run (game, screensaver, etc.) X crashes and logs me out.

This is a very new phenomenon (last 48 hours or so).

I'm running Dapper with the nvidia driver.

Any ideas?[/QUOTE]
Reinstall the driver. I had the same problem.

---

### Post by 3rdalbum on 2006-05-16
Funny thing: This kinda happened to me on PPC Xubuntu Breezy. I was compiling a program. All the while I was actually using the computer, everything was fine. When I left the computer and kept the compiling happening, I came back to find I'd been logged off.

I was using the open-source ATI driver. Oh well, it doesn't bother me really as it's quicker to compile without the GUI anyway.

---

### Post by soze on 2006-05-16
[QUOTE=tseliot]Reinstall the driver. I had the same problem.[/QUOTE]

That worked.
Thanks!

---

### Post by Nimbus_p12 on 2006-05-17
ahh, had a quick test last night and as soon as I run glxgears it crashes the X session and relogs in...
Same with the screensaver...
So, reinstallation of the driver next :(

---

### Post by tseliot on 2006-05-17
[QUOTE=Nimbus_p12]ahh, had a quick test last night and as soon as I run glxgears it crashes the X session and relogs in...
Same with the screensaver...
So, reinstallation of the driver next :([/QUOTE]
Use my script and your life should be a bit easier ;)

---

