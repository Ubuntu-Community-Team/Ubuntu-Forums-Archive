---
title: "Firefox not coming up from NX Client connection"
date: 2009-08-10
forum: General Help
---

### Post by hpark21 on 2009-08-10
Firefox will fire up (and will be running according to ps aux|grep firefox), but the screen never shows up when I connect to the computer via NX client.

I am using 3.3 NX server.

This is on a new install of 9.04 Ubuntu.

I am connected via 3.2 NX client.  (could this be the issue?)

Chromium and other X apps seems to work just fine though.

Thanks.

---

### Post by hpark21 on 2009-08-10
Just verified that this ONLY affects 3.5 version of firefox, and not 3.0.

What could be different that this may happen?

Thanks.

---

### Post by Alvin Maker on 2009-11-16
I can confirm that this still happens with NX Server 3.4.  I've determined a work around, but don't yet have an idea of why it works.  If I change the NX session to disable media support, firefox comes up fine.  I'll try to dig into things later and figure out why this changes things, but can't right now.
 
If someone has an idea, that would be helpful.

---

### Post by firehawk256 on 2009-12-11
Just thought I would throw in my 2 cents as a Debian user.  I have the same problem, but your workaround of disabling the multimedia support works for me too.  I also noticed that this problem affects eterm, but not iceweasel.  What's up with that?

---

### Post by HAARP on 2010-02-03
Same here. Thunderbird 3.x also shows this bug. Maybe someone should file a bug at Mozilla? ;)

---

### Post by mrand on 2010-02-04
> **Alvin Maker said:**
> If I change the NX session to disable media support, firefox comes up fine.I too had to unclick "enable media support" before Firefox would work.  Thank you for posting this!

For the record, I ran into this using the freely available NX server and client software, not FreeNX.  I did some quick searching and have not been able to determine why this is required... the only hints are here:

[http://www.nomachine.com/ar/view.php?ar_id=AR03D00355](http://www.nomachine.com/ar/view.php?ar_id=AR03D00355)

Random FYI: pulseaudio support appears to be coming in NX 4.0

[INDENT]Marc[/INDENT]

---

### Post by alizard on 2010-05-10
This also works for Eudora 8 beta (Thunderbird with Eudora "Penelope" extension) with nxserver. 

I'm glad this was posted, you can imagine how puzzled I was to discover that apparently nxserver would display every program I cared to run on my remote desktop *except* the program I need most.

---

### Post by avessalom on 2010-09-27
Hi people. 
I've has a same problem but found a solution on the other forum:
[http://forums.opensuse.org/english/get-help-here/applications/427669-ld_preload-keeping-mozilla-starting.html](http://forums.opensuse.org/english/get-help-here/applications/427669-ld_preload-keeping-mozilla-starting.html)

--------------

This is what LD_PRELOAD was being set to in the default login session -
LD_PRELOAD=/usr/NX/lib/libesddsp.so.0 /usr/NX/lib/libesd.so.0

----------------

The solution: unset LD_PRELOAD variable.
LD_PRELOAD="" firefox

I hope this will help you.

---

