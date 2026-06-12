---
title: "Teamspeak3 Sound Issues (Driver conflicts?)"
date: 2012-05-23
forum: General Help
---

### Post by Hirobian on 2012-05-23
Hello, relatively inexperienced user here, please explain your solutions with detail.

I am currently using a Dell Inspiron 1546 with a Windows 7 (64-bit) /  Ubuntu 12.04 (64-bit) Dualboot. This laptop uses an "ATI Mobility Radeon  HD 4300 Series" graphics card and an AMD Turion(tm) X2 Dual-Core Mobile  RM-75 × 2 with 4 GB of RAM.

My problem here is that ever since I installed the newest Ubuntu OS, Teamspeak tends to stop having working sound  capabilities when I use other programs at the same time, normal sounds  or talking turn into Scritching and scratchy noises and apparently my  friends can no longer hear me either when that happens.

Example situation: I use Teamspeak to talk with friends while I play  Minecraft, I cannot do this anymore due to the current problem.

I have no idea why it does that, I'm just guessing Ubuntu 12.04 has  driver issues that still need to be fixed. Teamspeak uses ALSA.

(Note that I have previously posted this exact thread in the **Multimedia & Video **section  but no one has replied, I am trying my luck here in this less specific section. Please do reply if you have any ideas.)

---

### Post by Steven D on 2012-05-24
I've recently started using pulseaudio for Teamspeak 3 to solve said issues.

The issue I had was similar, ex: Doom3, Quake4 UT2K4 while teamspeak is running, I would either get audio from TS or the game never both. Turned out it was an ALSA issue not being able to handle resources for both programs. When I switched TS over to pulse, it started working fine.

---

### Post by Hirobian on 2012-05-24
I will see if that works for me, but last time I tried running teamspeak with pulse audio it didn't make sound. I thought Teamspeak 3 only used ALSA... am I wrong?

It seems to have worked, I will give more results in an hour.

Well that was more than an hour. Every thing seems fine, I will mark this thread as solved, however I will have to create a new one if I later find the problem persisting. Thank you for the assistance.

---

