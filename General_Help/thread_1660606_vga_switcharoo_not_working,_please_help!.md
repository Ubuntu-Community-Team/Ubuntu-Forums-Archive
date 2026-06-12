---
title: "vga_switcharoo not working, please help!"
date: 2011-01-05
forum: General Help
---

### Post by Cheetah1933 on 2011-01-05
My problem is that I am trying to use switchable graphics with  vga_switcharoo. I googled "ubuntu on HP envy 14" before I started, and  all reports said that it works fine with my computer. Here are the  commands that I am using:
```

echo ON > /sys/kernel/debug/vgaswitcheroo/switch

Turns on the unused graphics card.

echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

Turns off the unused graphics card.

echo DIGD > /sys/kernel/debug/vgaswitcheroo/switch

Switches to integrated graphics

echo DDIS > /sys/kernel/debug/vgaswitcheroo/switch

```

Switches to dedicated graphics

I  can here the computer switch between cards, when the fans switch, but  it delivers no change in performance while playing games, and when I run  the command

glxinfo | grep "renderer string"

It tells me  it that it is still rendering from the battery saving intel card, rather  than the ATI gaming card. I can not get it to switch from the intel  card, no matter what I do.

Please help me. I'm so sorry if I'm making stupid mistakes, but I can't get it to work.

System Specs:
Specs:ATI Mobility Radeon 5650
500GB (7200RPM) Hard Drive (SATA)
Intel Core i5-450M processor 2.40GHz with Turbo Boost Technology up to 2.66 GHz
4gb of ram
Ubuntu 10.10 Maverick Meerkat

---

### Post by Cheetah1933 on 2011-01-05
bump.

---

### Post by Marc128000 on 2011-01-17
Perhaps the drivers for the ATI card are not installed? Also I believe that right now you still need to restart the xserver in order for the cards to switch. I'm still looking into this on my Hp Envy 14. In the near future I'll have a post detailing any info I can gather in my blog. Link can be found in my profile.

---

### Post by Marc128000 on 2011-01-17
I posted a step by step tutorial on how to enable graphics switching.
Here at my blog: [Linuxenvy]("http://linuxenvy.blogspot.com/2011/01/tackling-switchable-graphics.html")

---

