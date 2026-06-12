---
title: "Forced to re-login every day or two"
date: 2009-09-28
forum: General Help
---

### Post by shadilac on 2009-09-28
Fortunately I have a good habit of saving my work frequently, but I'm going to get caught by this eventually and it's very critical...

My desktop 9.04 installation routinely (every day or two) crashes by forcing me to re-sign in. I'll just be coding or surfing the net and the screen goes black. It shows some text (I never get a chance to read it all) for about a second that reminds me of the screen we used to see when booting linux:

some application name [OK] 
another application name [OK]
etc. [OK]

Then it returns me to the login screen. When I login everything is fine, but of course I've lost all my windows. My Ubuntu installation is reasonably new but I'm 99.99% sure this was not occurring when I first installed it, something changed in the last month. I don't know if it was an update, or when I installed the ATI driver to use compiz, or something else. 

I use this machine for software development, nothing too unusual installed. Apache, postgres, activemq, eclipse, firefox are typically always running. It's a 32-bit installation from scratch (no upgrade) of 9.04, on an 8GB RAM, quad core desktop PC.

Any help would be appreciated.

---

### Post by t0p on 2009-09-28
If you look at the file /var/log/messages, you may see error messages related to the crash.  This may give you some insight into what caused it.

This is not usual behaviour for Ubuntu, some people report uptimes of months with Ubuntu boxes.  Check out the logs.

---

### Post by shadilac on 2009-09-28
Yes that file is filled with messages... Okay, I guess I'll wait for it to happen again then check that log. I quickly scanned the last day and the only warning I see is this:

WARNING: at /build/buildd/linux-2.6.28/kernel/power/main.c:177 suspend_test_finish+0x80/0x90()

I see lots of messages about suspend/resume. Maybe I should stop using that and see if my problem goes away.

---

### Post by shadilac on 2009-09-28
So it just happened again, here is the log:

Sep 28 16:48:26 name-desktop bonobo-activation-server (name-17254): could not associate with desktop session: Failed to connect to socket /tmp/dbus-mOvxemzbtt: Connection refused
Sep 28 16:48:30 name-desktop kernel: [297781.279111] [fglrx] GART Table is not in FRAME_BUFFER range 
Sep 28 16:48:30 name-desktop kernel: [297781.347193] [fglrx] Firegl kernel thread PID: 17345
Sep 28 16:48:30 name-desktop kernel: [297781.352756] [fglrx] Gart USWC size:1570 M.
Sep 28 16:48:30 name-desktop kernel: [297781.352762] [fglrx] Gart cacheable size:60 M.
Sep 28 16:48:30 name-desktop kernel: [297781.352771] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Sep 28 16:48:30 name-desktop kernel: [297781.352776] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
Sep 28 16:48:31 name-desktop bonobo-activation-server (name-17357): could not associate with desktop session: Failed to connect to socket /tmp/dbus-mOvxemzbtt: Connection refused
Sep 28 16:48:37 name-desktop pulseaudio[17530]: pid.c: Stale PID file, overwriting.

---

### Post by shadilac on 2009-09-28
Any ideas? This has to stop...

---

### Post by DeMus on 2009-09-28
> **shadilac said:**
> Any ideas? This has to stop...

When you Google the error messages you find it has to do with the Xserver. (graphical server)
Which graphical card do you use?
Did you try switching of Compiz, because I know (also unfortunately from own experiences) it's a pain in the b*tt.

---

### Post by shadilac on 2009-09-29
Ya it started happening about the time I activated compiz with the proprietary drivers... I was worried about that. I'm using the "ATI/AMD proprietary FGLRX graphics driver" with an integrated ATI Mobility RADEON HD 3200.

---

### Post by Vaphell on 2009-09-29
they are not exactly rock solid
forced relogin = gui crashing and reloading, usually it happens because of gfx driver.

---

