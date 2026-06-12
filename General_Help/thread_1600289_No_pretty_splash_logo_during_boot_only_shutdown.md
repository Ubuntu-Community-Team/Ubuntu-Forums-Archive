---
title: "No pretty splash logo during boot only shutdown"
date: 2010-10-18
forum: General Help
---

### Post by vexorian on 2010-10-18
Last week I upgraded directly from 9.04 to 10.10 had tons of package issues and yadda yadda, now I have something close to a fully working system, besides of hibernation and what I think is an issue, so I have to ask...

When I boot ubuntu 10.10, it has this pink screen that says "Ubuntu 10.10" in pixelated letters. What can I say, it is like eighties computing. I thought to myself "hmnn what an odd selection of a boot splash". However, just when I reached a state in which I was able to shut the system down through valid ways. I noticed that the shut down splash looks exactly the same bit with the difference that it has a pretty white logo instead of the letters. So I think that me not being able to see the logo during start up splash is an issue  , and was wondering about a good starting point to figure out how to fix it...

---

### Post by Fender89 on 2010-10-18
I have the same problem both on boot and shutdown. It looks aweful.

---

### Post by Stanver on 2010-10-19
It may be because of proprietary video drivers; Grub is not configured to handle these. For instructions see here:
[http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html]("http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html")

---

### Post by dcstar on 2010-10-20
> **Stanver said:**
> It may be because of proprietary video drivers; Grub is not configured to handle these. For instructions see here:
[http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html]("http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html")

And using a better bootloader like BURG that makes using the various VESA resolutions easier to select also helps.

---

