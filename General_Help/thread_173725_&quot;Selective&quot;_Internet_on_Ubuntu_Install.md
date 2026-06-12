---
title: "&quot;Selective&quot; Internet on Ubuntu Install"
date: 2006-05-10
forum: General Help
---

### Post by GreenHawkIA on 2006-05-10
I recently dual-booted my desktop machine (I have been running Breezy (after Hoary) on my laptop for a long time now with great success).  It is an old HP Pavilion 520C with a 1.6 AMD processor with an integrated ethernet port.  However, I have run into an unusual problem, the installed firefox only lets me access certain sites, and runs slower than the internet on the windows portion.  I have 1.5 Mbs DSL through Qwest.  I cannot get at Google, but I can get at UbuntuForums, I can't read BBCNews, but I can get to my ISP site (looked there first for a solution) or [www.actiontec.com](www.actiontec.com) (my modem).  With apt-get I can get official repositories & PLF - but no Wine repos or Opera repos.  Any idea on what could be wrong or where I can look for a solution.  This is frustrating. ](*,)

---

### Post by hardXcore on 2006-05-10
ok

---

### Post by GreenHawkIA on 2006-05-11
No ideas? Just ok?
(EDIT: Sorry if that seemed rude, I just didn't understand the previous post or its purpose.)

---

### Post by cfroese on 2006-05-15
I installed Ubuntu about a week ago and found the same problem. I was able to to use all the other services, but I couldn't connect to the Internet using Qwest's DSL service. A quick search on Google (using a Mac) turned up the same problem, but no solutions. 

After struggling with modem and router settings, I finally found the answer in the  [[COLOR="RoyalBlue"]"Wired Ethernet Troubleshooting Process"[/COLOR]]("http://ubuntuforums.org/showthread.php?t=87643") post. I followed the instructions, but the  bit under _Common Application Problems_ about IPV6 did the trick and now I'm happily surfing the Internet.

By the way, this problem seems specific to Qwest but not Ubuntu.

---

