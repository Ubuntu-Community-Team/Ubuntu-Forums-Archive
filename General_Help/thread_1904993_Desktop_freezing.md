---
title: "Desktop freezing"
date: 2012-01-05
forum: General Help
---

### Post by Noamo30 on 2012-01-05
I am having a problem with my desktop freezing, and becoming pixelated, this happens almost immediately after turning on the computer. i have tried swapping out the ram and graphics card, as well as booting up from a live cd and i still get the same problems. so that leaves the processor and the motherboard. how would i test this and what new parts should i get.

AMD phonem 2 dual core
3 gb of ddr2 4200rpm RAM
nividia 8500 graphics card
ubuntu 11.10

---

### Post by dFlyer on 2012-01-05
Have you tried running disk utility to see if you have a hard drive failing, I would look there before going any further.

---

### Post by pretty_whistle on 2012-01-05
> **dFlyer said:**
> Have you tried running disk utility to see if you have a hard drive failing, I would look there before going any further.
Good advice.

---

### Post by Noamo30 on 2012-01-06
it wont stay on long enough for me to do that. which means it isnt even using the hard drive yet right? and i have tried to boot using a live cd/flashdrive and i still get the same problem.

---

### Post by Catharsis on 2012-01-06
Could be heat related.

I've also heard of ACPI giving people problems like this. Just hit 'e' during the grub prompt and add 'noacpi' after 'quiet splash'. Could also be kernel mode-setting, in which case the kernel tag to add would be 'nomodeset'.

---

### Post by Noamo30 on 2012-01-06
"Catharsis" how would i add a kernel tag and the "noacpi".
it wont even boot up without freezing and making the screen go purple. i have unplugged the hard drive and just booted up with a live flashdrive but i still get the same problem.

edit* i get the same problem even without having the live drive or hard drive inserted. i think it is because of the motherboard or the processor but i dont have one to switch with and check.

---

### Post by Catharsis on 2012-01-06
> **Noamo30 said:**
> "Catharsis" how would i add a kernel tag and the "noacpi".
it wont even boot up without freezing and making the screen go purple. i have unplugged the hard drive and just booted up with a live flashdrive but i still get the same problem.

edit* i get the same problem even without having the live drive or hard drive inserted. i think it is because of the motherboard or the processor but i dont have one to switch with and check.

[https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot](https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot)

Add them after "quiet splash", i.e. "... quiet splash noacpi".

---

### Post by Cookieh on 2012-01-06
Hmm... My PC setup is way worse than yours and my Ubuntu 11.10 very smoothly, maybe its because I have 500GB hard disk, but HDs shouldn't affect the performance...

---

### Post by pretty_whistle on 2012-01-06
Maybe heat related.  Does the computer feel really hot?

I had this once and it kept shutting off on me no matter what I did.  Till it cooled enough, that is.

---

### Post by pretty_whistle on 2012-01-06
Sounds like it's heat related.

---

### Post by Noamo30 on 2012-01-06
ive said before i started up the pc without a hard drive in and the problem still persists

---

### Post by Noamo30 on 2012-01-06
"pretty_whistle" it might be heat related because the fan on the PSU is out but it has 5 or 6 other fans on it and it feels cool. i tried switching the psu out with a stock dell one but it was for an older computer, it still had the same problem. maybe it isnt getting enough powe

---

