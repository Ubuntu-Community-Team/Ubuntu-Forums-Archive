---
title: "Can you disable ubuntu looking for wifi on the 5000000khz range?"
date: 2010-04-30
forum: General Help
---

### Post by solorize on 2010-04-30
Hi,

Does anyone know how to stop ubuntu (when loading) looking for
wifi signal’s in the 5000000 khz range?

I have a problem with other devices around my house that operate
on this range of frequencies and it effects ubuntu while its
booting, to the extent that it won’t load.

My wireless router is on the 2000000 khz range therefore I only
really need Ubuntu to look for devices on this range of 
frequencies.

If anyone know a way to prevent Ubuntu looking on the 5000000 khz range
by editing something I would be very greatful to know how to do this.

As at the moment I am having to boot about 5 times until
it eventually decided to load. Sometimes the only way I can get
in, is by going into recovery mode, dropping to terminal and 
typing in: "sudo gdm" and eventually I get it. Which is a right
pain.



Please see my previous post outlining my problem:

[http://ubuntuforums.org/showthread.php?t=1420422]("http://ubuntuforums.org/showthread.php?t=1420422")


Thanks in advance.

Mark

---

### Post by iponeverything on 2010-04-30
Relating to 9.10

[https://bugs.launchpad.net/ubuntu/+bug/277880](https://bugs.launchpad.net/ubuntu/+bug/277880)

Try 10.04 live-cd to see if the issue still exists. If it does not, try installing module-backports or perhaps upgrading.


If the issue does still exist with ath5k driver under 10.04, then adding you voice to the above bug report might help to get it fixed as the current status of this bug is listed as "Incomplete"

---

### Post by solorize on 2010-04-30
Thanks for you post, I will upgrade to 10.04 tonight
if the server is back online (as tried last night
and couldnt get the update to start), and see if
that fixes the problem.

Also thanks for the link.

Regards

Mark

---

### Post by iponeverything on 2010-04-30
You might hold off 1 day until the 10.04 final is up. Today is the day. If it is not up already..

---

