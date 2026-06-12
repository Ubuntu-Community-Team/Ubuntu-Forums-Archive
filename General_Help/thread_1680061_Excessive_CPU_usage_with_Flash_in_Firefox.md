---
title: "Excessive CPU usage with Flash in Firefox"
date: 2011-02-01
forum: General Help
---

### Post by Irihapeti on 2011-02-01
I am doing an online seminar using Adobe Connect vers. 8. It runs in Flash in a browser, and Ubuntu is officially supported.

Everything works properly - sound and visuals - but I noticed that CPU usage was up around 70 to 100%.

I don't like the idea of doing this for 2 hours on end. (So I took the coward's way out and booted into Windows.)

System:
Ubuntu 10.04, Firefox 3.6.13 with the Adobe flash plugin.
CPU is Pentium 4, 3.06 GHz - it's not like I'm trying to use a netbook.
1.5GB RAM.
USB audio (headset)

The visual content was slides, not movies.

Does anyone have any ideas about what I could do to get it to use less CPU?

---

### Post by no2498 on 2011-02-03
see if installing grease monkey helps fire fox/flash

---

### Post by Irihapeti on 2011-02-03
Thanks for the suggestion.

I know very little about Greasemonkey. Can you give me some specific things I could be looking for and tweaking?

BTW, I think that part of it might be that I booted with my USB headset plugged in. Even with FF not running, I was getting more CPU use than seemed reasonable. When I unplugged the headset, I got a kernel panic!

I can currently play back the (recorded) lesson in Flash with about 25-33% CPU usage, which is a bit higher than Windows but not hugely so.

---

### Post by no2498 on 2011-02-03
no i can not give insight on grease monkey it just helped me

id like to see you install htop
type it in a terminal it tells you how to install it
after installed 
type htop in a terminal click enter
look and see what is running so hard memory or cpu wise 
that gives you some thing to work with/fix

---

### Post by stalinvlad on 2011-02-03
Strange, I get that on Windows (any browser+Flash = 100% cpu)

---

### Post by Irihapeti on 2011-02-03
I had ordinary top running at the time, and the only thing showing up with big CPU use was Firefox.

I'll try htop and see what else shows up.

---

### Post by Irihapeti on 2011-02-03
> **stalinvlad said:**
> Strange, I get that on Windows (any browser+Flash = 100% cpu)

I was using Vista (SP2) and Firefox. Maybe you are running a different variety of Windows and that makes a difference.

---

### Post by gradinaruvasile on 2011-02-04
Flash uses much CPU. It is a known fact. Maybe on Windows uses less in some circumstances, but largely it hogs CPU.

---

