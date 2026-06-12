---
title: "Firefox performance"
date: 2009-07-05
forum: General Help
---

### Post by m_ad on 2009-07-05
I'm having the worst luck with 9.04. I have [another]("http://http://ubuntuforums.org/showthread.php?t=1204347") thread that I haven't resolved either.

I noticed Firefox (3.0.11) was slow to respond to some things, e.g. switching tabs, clicking links. This didn't bother me *too much*. However, what does bother me (and I'm sure it's related) is when I download a file, there is about a 20 second pause every 3 seconds, literally, in which the download freezes. A file that is supposed to take only 3 minutes ends up taking 30 minutes.

I completely removed the firefox package via Synaptic, and reinstalled it. This didn't resolve the problem.

Any recommendations?

):P

---

### Post by DeMus on 2009-07-05
> **m_ad said:**
> I'm having the worst luck with 9.04. I have [another]("http://http://ubuntuforums.org/showthread.php?t=1204347") thread that I haven't resolved either.

I noticed Firefox (3.0.11) was slow to respond to some things, e.g. switching tabs, clicking links. This didn't bother me *too much*. However, what does bother me (and I'm sure it's related) is when I download a file, there is about a 20 second pause every 3 seconds, literally, in which the download freezes. A file that is supposed to take only 3 minutes ends up taking 30 minutes.

I completely removed the firefox package via Synaptic, and reinstalled it. This didn't resolve the problem.

Any recommendations?

):P

Open a terminal (Applications > Accessories > Terminal) and type
top
To see which processes take up CPU time.
Watch carefully when downloading something. Does something change when the delay is active?

---

### Post by m_ad on 2009-07-05
Not sure how to interpret this. Things are changing pretty rapidly.

The delay is active pretty much the *whole* time I'm downloading something, except for maybe 2-3 seconds every 20-30 seconds. I'm downloading a file now, and it should only take 5 minutes. The download has been active for about 30 minutes now.

EDIT: 2 users? I'm the only one logged in!

---

### Post by lovinglinux on 2009-07-05
Reinstalling Firefox won't help. Follow the tutorials below. They are both created by me. I have increased Firefox performance benchmark 100% and my system is running a lot better.

[Tips: Things that might improve Jaunty performance](http://ubuntuforums.org/showthread.php?t=1152095)

[Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---

