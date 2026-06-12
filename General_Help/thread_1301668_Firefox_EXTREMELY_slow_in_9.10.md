---
title: "Firefox EXTREMELY slow in 9.10"
date: 2009-10-26
forum: General Help
---

### Post by wah fun on 2009-10-26
Weird. . . 

I installed 9.10rc as a guest os in virtualbox on a windows machine and it ran blazingly fast for me and all programs functioned well. So, I installed 9.10 on a desktop machine and all programs run substantially slower than they did in virtualbox. But Firefox 3.5.3 is my real headache on the permanent install - it is extremely slow. I mean 20-30 seconds and up to open most websites! I have cleared the SQLite databases, enabled pipelining and nothing seems to help.

My machine is a dual core AMD running at 2 Ghz with 3 GB ram. I have never encountered this problem before. I have also done a reinstall with no improvement.

Any suggestions would be appreciated.

---

### Post by gjoellee on 2009-10-26
I am used to Firefox being slow on Linux.

---

### Post by rob1408 on 2009-10-26
> **gjoellee said:**
> I am used to Firefox being slow on Linux.

Ditto.  I've switched to Opera 10 and that's like lightening.

---

### Post by P4man on 2009-10-26
clearly something is wrong. Perhaps your cpu is stuck in first gear so to speak. Try adding the cpu frequency scaling monitor to your panel and check its speed.

Also try opening a terminal and run top to see if something is hogging your system/ Firefox might be slow, but not anywhere near that slow on a modern pc.

---

### Post by Uncle Spellbinder on 2009-10-26
No issues with Firefox here. Just as quick on Karmic as it is in Windows 7.

---

### Post by Z06Gal on 2009-10-26
> **wah fun said:**
> Weird. . . 

I installed 9.10rc as a guest os in virtualbox on a windows machine and it ran blazingly fast for me and all programs functioned well. So, I installed 9.10 on a desktop machine and all programs run substantially slower than they did in virtualbox. But Firefox 3.5.3 is my real headache on the permanent install - it is extremely slow. I mean 20-30 seconds and up to open most websites! I have cleared the SQLite databases, enabled pipelining and nothing seems to help.

My machine is a dual core AMD running at 2 Ghz with 3 GB ram. I have never encountered this problem before. I have also done a reinstall with no improvement.

Any suggestions would be appreciated.


I use Opera and Chrome which are extremely fast but here is a link that helped alot when I do use ff:

[http://www.boygeniusreport.com/2009/01/25/a-handful-of-firefox-tweaks-that-will-double-your-browser-speed/](http://www.boygeniusreport.com/2009/01/25/a-handful-of-firefox-tweaks-that-will-double-your-browser-speed/)

---

### Post by james_xxx on 2009-10-26
You may possibly be affected by this bug, as are a large number of other users:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417757]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417757")

If you read through this thread, you should find instructions for a workaround.

Hopefully, this bug will be addressed and corrected before final release, although Ubuntu has a bit of a reputation for sticking hard to its release schedule, and letting even show-stopper bugs like this slide.

---

### Post by lovinglinux on 2009-10-26
Have you tried to disable ipv6?

See **Solution** [*[COLOR="Red"]**FOT005**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005).

---

### Post by james_xxx on 2009-10-28
bump

---

### Post by Anonymousable on 2009-10-28
Hmm... I have heard of a memory leak...
I have 4GB RAM and it runs no problems for me though. Shouldn't be that much of a difference with 3G.

---

### Post by mitchellcipriano on 2009-11-03
This worked for me:

ipv6

Network became slow due to the unsupported ipv6 protocol, so disabling ipv6 could help.

To disable ipv6 on Firefox Preferences, set the network.dns.disableIPv6 to true.

1. Type about:config in the address bar, press Enter.
2. Find network.dns.disableIPv6 in the list.
3. Right-click -> Toggle.
4. Restart your Mozilla application and try again.

You can find all the details at: [http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005)

---

### Post by heatblazer on 2009-11-04
> **gjoellee said:**
> I am used to Firefox being slow on Linux.

It`s slow on my ubuntu 8.04 LTS too. I`ve disabled all caches off-line and memory too. Maybe there is an improvement of 50%. Try it. Here is how to:
enter in browser
about:config
browser.disk.cache.capacity > 0
browser.disk.cache.enable   > false
browser.cache.memory.enable > false
browser.cache.offline.enable > false
browser.cache.offline.capacity > 0

---

### Post by heatblazer on 2009-11-04
> **mitchellcipriano said:**
> This worked for me:

ipv6

Network became slow due to the unsupported ipv6 protocol, so disabling ipv6 could help.

To disable ipv6 on Firefox Preferences, set the network.dns.disableIPv6 to true.

1. Type about:config in the address bar, press Enter.
2. Find network.dns.disableIPv6 in the list.
3. Right-click -> Toggle.
4. Restart your Mozilla application and try again.

You can find all the details at: [http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005)

It works good here! Nice tip! ):P

---

### Post by Maximus_ARNP on 2009-11-14
> **heatblazer said:**
> It works good here! Nice tip! ):P

Worked for me. Awesome fix.

---

