---
title: "Firefox slow performance"
date: 2012-01-22
forum: General Help
---

### Post by j0eb0b on 2012-01-22
I recently rebuilt an HP NC 6400 laptop using Ubuntu 11.10.  Everything works normally except Firefox.  Firefox is very slow and exhibits a strange condition.  When I type a search argument in a Google search, the keystrokes take 1 second or more from when I type them until when I see the characters in the Google search window. When Firefox takes me to a website, many times the keyboard is unresponsive.

I have loaded Google Chromium (using it now) and it works normally.  Any idea what the problem is with Firefox and how to fix it?

I found a post with changes to the following Firefox parameters which I changed and didn't help.

Network.http.pipelining = T
Network.http.pipelinng.maxrequests 8
Network.http.proxy.policy =
Network.dns.disableIPv6 = T


Network.dns.disableIPv6 = T

---

### Post by lovinglinux on 2012-01-24
That probably won't help.

First get Firefox 9, it will speed up things a lot. See [Firefox 9 & Beyond Mega Thread](http://ubuntuforums.org/showthread.php?t=1712247) for instructions.

Then make sure you have the latest video driver installed using the "Additional Drivers" application.

---

### Post by LinuxFan999 on 2012-01-24
What are the specifications of your computer?

---

### Post by j0eb0b on 2012-01-24
The laptop is a 3 year old HP NC 6400.  Dual Intel Centrino 1.8 GH CPUS and 2 GB memory.  The HD is 80 GB.

I think the fix for this one is to fall back from 11.10 to 11.04. I have another machine running 11.04 for more than a year happily and I re-imaged the laptop with 11.04 tonight.  My experience has been that any of the .10 releases of of Unbuntu have been buggy and the .04 LTS versions have been solid.  We will see.  Thanks for your response and support of the community.

Joe

---

