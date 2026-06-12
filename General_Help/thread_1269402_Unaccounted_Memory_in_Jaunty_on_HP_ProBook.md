---
title: "Unaccounted Memory in Jaunty on HP ProBook"
date: 2009-09-18
forum: General Help
---

### Post by ephemeralDream on 2009-09-18
Greetings,

I have HP ProBook 4310s loaded with Jaunty 9.04 with all the latest updates and ATI Proprietary driver (Radeon HD 4330).

I encountered a problem with unaccounted memory usage normally around 100-300mb higher. For a normal DEFAULT (no modification) boot up, memory usage is around 350++mb which is quite high.

Example from my current system-monitor
- gnome-system-monitor and `free -m` report 725mb ram usage (minus cached).
- I calculated the total memory from each individual process which is 585mb. I already checked 'All Processes' under View in gnome-system-monitor not just my processes only.
- I wonder where the the 140mb going to.

I hope you can shed some light on this weird issue.

If further information is required, i will gladly supply.

Thank you very much,

---

### Post by vancouverite on 2009-11-01
Is this still affecting you? There is a bug like this on launchpad that was made invalid, but I'm definitely having the same problem.

[https://bugs.launchpad.net/ubuntu/+bug/432531](https://bugs.launchpad.net/ubuntu/+bug/432531)

---

### Post by P4man on 2009-11-01
Why dont you post the output of free -m. I think you're just misreading the values. Memory used as diskcache doesnt show up in system monitor afaik.

---

### Post by ephemeralDream on 2009-11-01
@P4man: I just boot my laptop. I can't provide you one right now. You can use vancouverite's meminfo first:
[http://launchpadlibrarian.net/34853191/mem_info.tar](http://launchpadlibrarian.net/34853191/mem_info.tar)

$vancouverite: idyllic is my launchpad account. I opened the bug again. I converted it to a question last time cos I think my case was an anamoly, that's why it was marked as invalid. I also confirm it is still the same for me on my fresh Karmic Kubuntu.

Cheers,

---

### Post by P4man on 2009-11-01
Ok Im looking at your screenshot from launchpad.
First of all, a memory leak is a process that keeps using more memory. It would show up in top as a process using ever more memory. Thats not what you're having.

Secondly, I dont see anything wrong with those numbers. they seem to add up correctly at first glance, keep in mind buffers used by the kernel do not show in top as a process. Why do you think there is a problem?

---

