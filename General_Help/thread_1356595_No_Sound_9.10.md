---
title: "No Sound 9.10"
date: 2009-12-16
forum: General Help
---

### Post by heyniceaddress on 2009-12-16
Hi, all!

I just switched from XP to 9.10, and currently am without sound.

I checked the BIOS, and my card is on.

Thank you for the help in advance.

---

### Post by leedsdevil on 2009-12-16
hello , first thing we all need to better help you is type of computer?this would be a great start.Glad to hear that you are changing from Xp to Linux welcome.this is a great place to learn and help others..........

---

### Post by heyniceaddress on 2009-12-16
Thanks for the welcome.

It's a Dell XPS 400. I got it March 2006.

---

### Post by DaVince21 on 2009-12-16
Just switched? Phew, you'll be in for a hard time having to learn a completely new system... I wish you much luck and fun getting used to things. :)

Anyway, we need information about your sound card. Open the terminal (it's in the menu > Accessories) and run this:
```
lshw -c sound
```
This should give you information about your sound card, copy and paste that information in a new post here.

---

### Post by cqmmc on 2009-12-16
Try another drivers :guitar::guitar:

---

### Post by DaVince21 on 2009-12-16
> **cqmmc said:**
> Try another drivers :guitar::guitar:
ALSA (the sound system) already comes with almost all drivers available, ensuring that any sound hardware that has a driver will always work immediately... Though recompiling ALSA could sometimes suddenly make non-working sound hardware work.

---

### Post by heyniceaddress on 2009-12-16
Yeah. I like its philosophy. I also like its security.

I have a Ubuntu book that I'm leafing through, so hopefully I'll catch on quickly.

Here's the result of that code:

WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:16 memory:febfc000-febfffff
  *-multimedia
       description: Multimedia audio controller
       product: SB X-Fi
       vendor: Creative Labs
       physical id: 4
       bus info: pci@0000:05:04.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=SB-XFi latency=64 maxlatency=5 mingnt=4
       resources: irq:16 ioport:bce0(size=32) memory:f9600000-f97fffff memory:f4000000-f7ffffff

---

### Post by r_s on 2009-12-16
type alsamixer on the terminal to see if the sound is not too low...sometimes this is the only problem

---

### Post by heyniceaddress on 2009-12-16
All of them were up into the red, with the Master volume at 94.

---

### Post by heyniceaddress on 2009-12-16
I actually found what I did before and fixed it. I found an e-mail I'd sent to myself that I'd archived over a year ago that told me what to do in case this happened ... of course the link I had sent myself to a file was dead, so I did a Google search, and found that someone else had posted a step-by-step walkthrough of the same ordeal. It worked!

[http://ubuntuforums.org/showpost.php?p=3768914&postcount=60](http://ubuntuforums.org/showpost.php?p=3768914&postcount=60)

Now I just need to figure out how to mark this as solved ... I'm such a newbie.

---

### Post by Zoot7 on 2009-12-16
> **heyniceaddress said:**
> Now I just need to figure out how to mark this as solved ... I'm such a newbie.
Drop down the thread tools, you'll find it there. ;)

---

### Post by heyniceaddress on 2009-12-16
Thanks! haha.

---

