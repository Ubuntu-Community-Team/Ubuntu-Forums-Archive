---
title: "Task Manager more info? (CPU history, page file size etc.)"
date: 2011-12-19
forum: General Help
---

### Post by 2009Prius on 2011-12-19
Is it possible for the Task Manager (or another application) to display more info, such as the CPU usage history graph (not just the current CPU usage), RAM and page file history graphs, etc.? Thanks!

---

### Post by jwbrase on 2011-12-19
Assuming you mean the System Monitor, yes, just click on the "Resources" tab. The page file history graph will be labeled "Swap".

EDIT: Disregard, I missed the lubuntu tag on the thread. Nevertheless, I second the recommendation from BertN45 to use gnome-system-monitor, which is the program I originally thought you were referring to.

---

### Post by BertN45 on 2011-12-19
Task manager is somewhat minimal for xubuntu and lubunty, but you always could download the system monitor from the software center.

---

### Post by pretty_whistle on 2011-12-19
System Monitor is good and can be installed since lubuntu doesn't have it normally.

---

### Post by 2009Prius on 2011-12-20
Thank you guys! I started to have a feeling that Lubuntu is just stripped down way too much.

---

### Post by 2009Prius on 2011-12-20
Sorry still need help. I went to Synaptic Package Manager and searched for "System Monitor" and couldn't find it. What is the name of the package exactly? Thanks!

---

### Post by MartijnNL on 2011-12-20
gnome-system-monitor

Like jbrase mentioned above.

---

### Post by seawolf167 on 2011-12-20
You may also way to take a look at top/htop

```
sudo apt-get install htop
```

---

### Post by pretty_whistle on 2011-12-20
I got System Monitor by 1st installing Software Center and then used this to install it.

As far as saying you're wondering if they slimmed down Lubuntu too much, all I can say is for myself I removed so many things that came with Lubuntu I feel I balanced out when I put things in that it didn't have.

---

### Post by 2009Prius on 2011-12-21
Thanks again! I got System Monitor running and the CPU usage jumped from less than 5% up to 15 ~ 20%. :-? Is it normal that the System Monitor itself consumes so much CPU time? :confused:

---

### Post by pretty_whistle on 2011-12-21
> **2009Prius said:**
> Thanks again! I got System Monitor running and the CPU usage jumped from less than 5% up to 15 ~ 20%. :-? Is it normal that the System Monitor itself consumes so much CPU time? :confused:
I hadn't thought about it actually.

---

### Post by 2009Prius on 2011-12-21
I just went back to Win 7 and looked. With both Task Manager and Resource Monitor running and both having rolling graphs, the CPU usage is less than 5%. System Monitor on Ubuntu seems much worse.

---

### Post by pretty_whistle on 2011-12-21
Plug-in container shows in system monitor as using 3-4% CPU.  More than system monitor itself which averages at 1-2%.

Wonder what plug-in container is?  Firefox plug ins?  Must be...

---

### Post by pretty_whistle on 2011-12-21
> **2009Prius said:**
> I just went back to Win 7 and looked. With both Task Manager and Resource Monitor running and both having rolling graphs, the CPU usage is less than 5%. System Monitor on Ubuntu seems much worse.
Interesting.

---

### Post by 2009Prius on 2011-12-21
> **pretty_whistle said:**
> Plug-in container shows in system monitor as using 3-4% CPU.  More than system monitor itself which averages at 1-2%.

...

I suppose you have a powerful CPU? My Intel Atom N455 in the netbook is kind of slow.

---

### Post by pretty_whistle on 2011-12-21
> **2009Prius said:**
> I suppose you have a powerful CPU? My Intel Atom N455 in the netbook is kind of slow.
I presume so.

Also, I'm using a laptop with Lubuntu on it and not a netbook.  Probably makes a difference.

---

### Post by BertN45 on 2011-12-21
yes system monitor use too much cpu time, but you can lower it by changing the update interval in the preferences. I usually set it to 2.5 seconds.

If you want a real sexy and efficient system monitor, have a look at conky. It is a fully scriptable system monitor and somewhere in this forum there are hundreds of entries with screenshots and script files. You could take one and adapt it.

---

### Post by pretty_whistle on 2011-12-21
> **BertN45 said:**
> yes system monitor use too much cpu time, but you can lower it by changing the update interval in the preferences. I usually set it to 2.5 seconds.

If you want a real sexy and efficient system monitor, have a look at conky. It is a fully scriptable system monitor and somewhere in this forum there are hundreds of entries with screenshots and script files. You could take one and adapt it.
Hey.  That's a idea I'll look into.  

This thread is helping more than the person who started it.  I like when that happens.  :)

---

### Post by pretty_whistle on 2011-12-21
> **BertN45 said:**
> yes system monitor use too much cpu time, but you can lower it by changing the update interval in the preferences. I usually set it to 2.5 seconds.

If you want a real sexy and efficient system monitor, have a look at conky. It is a fully scriptable system monitor and somewhere in this forum there are hundreds of entries with screenshots and script files. You could take one and adapt it.
I went to look for conky-it says this:

> This is a dummy package to ease transition to the new packaging scheme. It may be safely removed after upgrade/installation.

What's that supposed to mean?

Maybe I should get the one in synaptic thats called "conky-all" ??

---

### Post by pretty_whistle on 2011-12-21
> **BertN45 said:**
> yes system monitor use too much cpu time, but you can lower it by changing the update interval in the preferences. I usually set it to 2.5 seconds.

If you want a real sexy and efficient system monitor, have a look at conky. It is a fully scriptable system monitor and somewhere in this forum there are hundreds of entries with screenshots and script files. You could take one and adapt it.
Btw, that helped reduce the CPU use by changing what you said.

---

