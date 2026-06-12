---
title: "Ubuntu Audio"
date: 2010-03-26
forum: General Help
---

### Post by rocket16 on 2010-03-26
Hello all. I am a player of Battle for Wesnoth, one of the best Ubuntu games. I have been running Wesnoth 1.6.5 (stable) on Ubuntu 9.10. But many a times, sound stops, and Wesnoth needs to be closed from System Monitor by killing processes, or using "killall -ser username" Command from Console. So, in Wesnoth Channel, they told that it is a problem of ALSA. So, what is the solution? (My friends have the same problem).

---

### Post by Ghost|BTFH on 2010-03-26
> **rocket16 said:**
> Hello all. I am a player of Battle for Wesnoth, one of the best Ubuntu games. I have been running Wesnoth 1.6.5 (stable) on Ubuntu 9.10. But many a times, sound stops, and Wesnoth needs to be closed from System Monitor by killing processes, or using "killall -ser username" Command from Console. So, in Wesnoth Channel, they told that it is a problem of ALSA. So, what is the solution? (My friends have the same problem).
Are you using pure ALSA for your sound?  If so, perhaps installing alsa-oss and setting Wesnoth to OSS instead of ALSA would help.  If you're using PulseAudio, you need to go into your sound settings and change it from ALSA to Pulse in order to resolve the problem.

Hope this helps.

Cheers,
Ghost|BTFH

---

### Post by rocket16 on 2010-03-26
Thanks for the reply. I am trying the process recommended. :)

---

