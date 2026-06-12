---
title: "Repeated Error Warnings Since 12.04 Install"
date: 2012-05-17
forum: General Help
---

### Post by gast0r on 2012-05-17
Ever since performing a fresh install of 12.04, I've been harassed by error messages telling me that a system problem has been detected. When I attempt to send a bug report, it tends to repeat it about two or three times more. 
[IMG]http://i.imgur.com/oqZn1.png[/IMG]
If anyone knows a fix for this or any possible reasons for it happening, I'd really appreciate the help.

I should probably also mention that with the appearance of these warnings, an app often unexpectedly quits. It's usually Compiz or Gwibber.

---

### Post by dcstar on 2012-05-18
> **gast0r said:**
> Ever since performing a fresh install of 12.04, I've been harassed by error messages telling me that a system problem has been detected. When I attempt to send a bug report, it tends to repeat it about two or three times more. 
..........

That was an issue with some of the Beta and development releases.

Have you installed the official release version?

---

### Post by gast0r on 2012-05-18
> **dcstar said:**
> That was an issue with some of the Beta and development releases.

Have you installed the official release version?

Nah, I can guarantee this is the final release version.

---

### Post by bogan on 2012-05-18
Hi!, **gastO**r,

Have you tried running```
 sudo dpkg-re-configure -a
``` ??

I had lots of those sorts of error messages during the first 10 days of 12.04 LTS; then I ran the above and they virtually stopped.

Unfortunately they have now started again, though not nearly so often,  maybe one a day, mostly gnome-panel or nautilus.

```
sudo apt-get install -f
``` is also reported to help, but I have not found it made any difference; probably depends on the source of the trouble.

Chao!, **bogan.**

---

### Post by gast0r on 2012-05-20
> **bogan said:**
> Hi!, **gastO**r,

Have you tried running```
 sudo dpkg-re-configure -a
``` ??

I had lots of those sorts of error messages during the first 10 days of 12.04 LTS; then I ran the above and they virtually stopped.

Unfortunately they have now started again, though not nearly so often,  maybe one a day, mostly gnome-panel or nautilus.

```
sudo apt-get install -f
``` is also reported to help, but I have not found it made any difference; probably depends on the source of the trouble.

Chao!, **bogan.**


Thanks for the reply. Unfortunately neither command yielded any result. The first just seemed to alert me that I don't have some GTK2 engines installed.

---

### Post by MoebusNet on 2012-05-20
I had the same problem after upgrading from 11.10 to 12.04, especially after doing a few updates. However the last batch of updates seem to have eliminated the problem for me. Perhaps that will work for you too. Best of luck.

---

### Post by gast0r on 2012-05-20
> **MoebusNet said:**
> I had the same problem after upgrading from 11.10 to 12.04, especially after doing a few updates. However the last batch of updates seem to have eliminated the problem for me. Perhaps that will work for you too. Best of luck.

My latest updates came a few hours ago and it's continued to persist:( Is there anything you done at all (other than updates) that you think could have contributed to it stopping?

---

### Post by MoebusNet on 2012-05-20
The only thing that I can think of that might apply is that I usually leave my computers shut down when I'm not using them. Perhaps the shut down & restarts had something to do with it.

---

