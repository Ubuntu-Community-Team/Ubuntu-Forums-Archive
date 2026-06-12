---
title: "E4rat and ureadahead"
date: 2011-10-26
forum: General Help
---

### Post by FallenUnia on 2011-10-26
Hello everyone,

My question is actually pretty short: does Ureadahead has any advantages over E4rat?

I am coming from an Arch Linux background and on Arch, I have always used E4rat with great pleasure. It cut off my boot-time with some 30% and actually, the transition from CLI to X was instant and from login to desktop as well. I am not experiencing this behavior with Ureadahead so I was looking to replace it with E4rat.

However, before doing this, I would like to hear some opinions on it. Does Ureadahead have any advantages over E4rat? Why should I use one instead of the other in your opinion?

---

### Post by aeiah on 2011-10-26
ureadahead just reads all needed files into memory at once, and accesses them when needed during boot. e4rat also does this as far as i know, but it also reshuffles all those pieces to the start of the partition, in order, so it can read them into memory more efficiently.

do a test. i found e4rat to improve boot for me

---

### Post by FallenUnia on 2011-10-26
Hmhm that is what I understood, yes. 

Are there any commands/settings I need to run/change after removing Ureadahead?

---

### Post by mips on 2011-11-02
> **aeiah said:**
> ureadahead just reads all needed files into memory at once, and accesses them when needed during boot. e4rat also does this as far as i know, but it also reshuffles all those pieces to the start of the partition, in order, so it can read them into memory more efficiently.

do a test. i found e4rat to improve boot for me

Is your plymouth splash working with e4rat though? Mine would not work when I tried it 2 or so weeks ago.

e4rat is faster than ureadahead I have found. It moves all the files loaded in the first 2min of boot to the beginning of the hard disk and defrags them to eliminate head seak time.

I'm thinking maybe I should let e4rat optimise the files/location and then revert back to ureadahead after that to gain the same benefits?

---

