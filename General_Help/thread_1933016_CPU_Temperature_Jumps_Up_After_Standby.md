---
title: "CPU Temperature Jumps Up After Standby"
date: 2012-02-28
forum: General Help
---

### Post by MoeBrowne on 2012-02-28
Hi All,
I recently got an applet called sensors-applet working to show, among other things, my CPU temperature. The temperature actually come from libsensors.
This works fine until I return from standby after which it reports the temperature to be around 60C (idle). This is about double what it should be (its liquid cooled).

Couple of things to mention:

[LIST=1]
[*]The standby is the type where the computer shuts off power to everything that's not required to keep it alive, I think its called S3(STR)
[*]I'm running Ubuntu 11.04 (Gnome GUI)
[*]None of the other temperature readings are affected though they don't come from libsensors.
[*]I have a Pentium D which is a dual core. Is it some how adding the temperatures of both?
[*]If I hibernate or restart the system it reports the temperature correctly again.
[*]If I standby the system multiple times it stays at double.
[*]It appears to be offset rather than wrong, aka if I load the CPU it rises by the expected amount.
[/LIST]
Any help or thoughts are appreciated



Thanks in advance!

---

