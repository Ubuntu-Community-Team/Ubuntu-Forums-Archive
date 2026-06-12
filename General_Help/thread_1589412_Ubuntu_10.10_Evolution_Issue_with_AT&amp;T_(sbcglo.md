---
title: "Ubuntu 10.10 Evolution Issue with AT&amp;T (sbcglobal) email"
date: 2010-10-06
forum: General Help
---

### Post by stad on 2010-10-06
Hey Guys,

I have had this problem with 10.04, and it seemed to be fixed with 10.10 beta. However, after downloading and install the release candidate, the problem returned.

I cannot for the life of me get my (paid) AT&T email to work with Evolution. I set it up with the correct POP and SMTP settings and it always says that there is an Error fetching mail. Here's the weird part: my inbox has email from 3 days ago and prior. So basically, this leads me to believe that it worked at one time. 

When I installed 10.10-RC, it was a fresh install, not an upgrade.

Has anyone else had an issue setting up AT&T email?

Thanks,

Ryan

---

### Post by andrewthomas on 2010-10-06
Do you still have the 10.10 beta installed? 

 FYI, there is no reason to download the RC if you already have the beta installed, just keep it updated and you will have the release on release day.

---

### Post by FahadMKS on 2010-10-06
Evolution is a bit hard to understand and not much user friendly.
Why dont you try the new Thunderbird Email client.
It is safer and much more user friendly.
Try it and you will have the issue resolved

---

### Post by stad on 2010-10-06
> **andrewthomas said:**
> Do you still have the 10.10 beta installed? 

 FYI, there is no reason to download the RC if you already have the beta installed, just keep it updated and you will have the release on release day.

I do not have beta installed anymore. I completely wiped my hard drive. I wonder what could have caused Evolution not to work.

---

### Post by stad on 2010-10-07
Hey guys, just thought I'd give an update just in case anyone else was experiencing a similar issue.

Fix: make sure that your POP port (usually 995) is open

I had to go into my router settings and allow Evolution to access the port (terminology may be incorrect as I only have a vague understanding of port forwarding).

check out [www.portforward.com](www.portforward.com)

---

