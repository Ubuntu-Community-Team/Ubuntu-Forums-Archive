---
title: "Move hard drive to another motherboard/computer"
date: 2010-04-15
forum: General Help
---

### Post by Ebere on 2010-04-15
I decided to do a full install of kubuntu.

I tried the kubuntu over ubuntu trick, but had problems.

So I wiped a hard drive, and installed kubuntu.

Unfortunately, I wiped the wrong one, and installed. LOL

So now, this hard drive has to be installed in another computer.

I am wondering if I am going to have any problems with it ?

Should I just wipe it again, and reinstall ?

Or will it find the new hardware at startup, and adjust it's own self ? (Like my windows hard drives do. LOL)

---

### Post by dcstar on 2010-04-15
> **Ebere said:**
> 
...........
Should I just wipe it again, and reinstall ?

Or will it find the new hardware at startup, and adjust it's own self ? (Like my windows hard drives do. LOL)

[LIST=1]
[*]Yes.
[*]No, some things may work but others probably won't.
[/LIST]

---

### Post by iponeverything on 2010-04-15
I have had very good luck with moving the HD to new systems. 

More than 50% of the time everything just works for desktop installs and for server installs my success rate is more like 80%.

---

### Post by Dayofswords on 2010-04-15
as long as the hardware isnt drastically different, you probably wont see too many issues

---

### Post by coffeecat on 2010-04-15
Moving a HD from one machine to another is entirely feasible. The main issue you may face is if you have installed a proprietary video driver and the new machine has a different make of video card. Sound also may need reconfiguring. Apart from that you will probably only get minor oddities such as the ethernet card on the second machine being designated eth1. And you can get over that by editing/renaming/deleting /etc/udev/rules.d/70-persistent-net.rules.

Try it and see.

By the way, Windows gets a fit of the vapours if it detects too much new hardware (when you move a HD from one drive to the other, for example) because it is programmed so to do. It keeps some sort of score against the hardware and requires re-activation if the score goes too high.

---

### Post by Ebere on 2010-04-16
Well, I made the migration.

I haven't seen any problems that are specifically due to swapping the hard drive to a different computer. 

It found everything, and was quickly up and running.

Thanks to all.

---

