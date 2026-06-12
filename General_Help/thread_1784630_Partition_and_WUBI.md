---
title: "Partition and WUBI"
date: 2011-06-17
forum: General Help
---

### Post by iGThomas on 2011-06-17
Hi, I'm new here and like all new guys everyone can have question and I have two:

1. Yesterday I tried to install Ubuntu with WUBI and when I rebooted the pc it said : Try (hd0,0): NTFS5:  No wubildr and then the little _ blinks and never stops. I waited 10 min and nothing happened so I swiched to Windows.

2.Today I tried to install Ubuntu 11.04 with usb. So I've made a partition with my HD and made 8GB but when I want to install it there, Ubuntu can't see it[IMG]http://igthomas.co.cc/Screenshot.png[/IMG]

My Partition drive name is Ubuntu and it's on /dev/sda5 and I can see /dev/sda  but not /dev/sda5 
Oh and my Windows is on /dev/sda and I don't want to lose it

Thomas

---

### Post by DirtyPC on 2011-06-17
Use the freespace and create a partition there.

---

### Post by iGThomas on 2011-06-17
> **harrylucas1 said:**
> Use the freespace and create a partition there.
Will it delete my windows?

---

### Post by DirtyPC on 2011-06-17
/dev/sdb has 10000 something mb free, that means its empty, installing there won't get rid of your windows

---

### Post by iGThomas on 2011-06-17
> **harrylucas1 said:**
> /dev/sdb has 10000 something mb free, that means its empty, installing there won't get rid of your windows I have 1GB free in /dev/sdb :/

---

### Post by DirtyPC on 2011-06-17
1gb = 1000mb

you have 10gb= 10000mb

---

### Post by iGThomas on 2011-06-17
> **harrylucas1 said:**
> 1gb = 1000mb

you have 10gb= 10000mb I know it's 10GB but there are some files that I need (I have mac installed there)

---

