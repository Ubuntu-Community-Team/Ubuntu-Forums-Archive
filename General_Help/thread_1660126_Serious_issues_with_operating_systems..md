---
title: "Serious issues with operating systems."
date: 2011-01-05
forum: General Help
---

### Post by toxic9813 on 2011-01-05
I am having issues, ever since I have installed Ubuntu. Although, I don't think it's Ubuntu's fault.

Since I installed it, it ran like greased lighting. Google Chrome would be open before I even lifted my finger from the button. After a few weeks (I haven't installed any other programs) it has just slowed down.

Not only slowed down, but the important thing is: It hangs.

On Ubuntu, when I try to do anything slightly hardware-intensive... It hangs BAD. I hear the fan turn off, the HDD stop spinning. Completely silent. The screen says completely frozen, but I can move my mouse around. It stays like this for periods up to 30 mins and then miraculously unfreezes, with no fanfare. No error recovery. :confused:

And then I boot to my Windows 7 partition. And then I switch to Windows 7. It completely stops, like before, but the mouse does not move. After exactly 10 minutes it shows BSOD and reboots to Ubuntu (of course, my primary partition!)

Anything to help? I suspect it's a hardware problem...

---

### Post by edorfaus on 2011-01-05
> **toxic9813 said:**
> On Ubuntu, when I try to do anything slightly hardware-intensive... It hangs BAD. I hear the fan turn off, the HDD stop spinning. Completely silent. The screen says completely frozen, but I can move my mouse around. It stays like this for periods up to 30 mins and then miraculously unfreezes, with no fanfare. No error recovery. :confused:

And then I boot to my Windows 7 partition. And then I switch to Windows 7. It completely stops, like before, but the mouse does not move. After exactly 10 minutes it shows BSOD and reboots to Ubuntu (of course, my primary partition!)

Anything to help? I suspect it's a hardware problem...
I'm no expert, but I think you're right, this does sound like a hardware problem to me too.

I believe Linux probably *is* doing some error recovery though, it just doesn't call your attention to it... After it unfreezes, you could try looking at the output of the [FONT=Lucida Console]dmesg[/FONT] command, or near the end of the /var/log/messages log file - it might be saying something about it there.

If it does say something recognizable, that might help to pinpoint what exactly is failing, which would help in figuring out if there's anything that can be done about it past replacing/repairing the hardware...

Sorry I'm not much help, but that's all I can think of to suggest...

---

### Post by piquat on 2011-01-05
I think I'd start by doing the memtest that pops up in the grub menu.  If that fails try each stick on it's own.

I'd expect PSU or CPU overheat would just crash and not come back.  The coming back part is strange.

---

### Post by coldraven on 2011-01-05
Having seen the amount of fluff and dust that gets into PCs I always suspect that it's an overheat problem.
Try ```
sensors
```
and see how hot your chips are.

---

### Post by TBABill on 2011-01-05
> **coldraven said:**
> Having seen the amount of fluff and dust that gets into PCs I always suspect that it's an overheat problem.
Try ```
sensors
```
and see how hot your chips are.
 +1. The fact that the system will come back and work normally until the next shutdown sounds like a heat or power issue. I'd still run MEMTEST just because it's easy but the problem from the explanation sounds too intermittent to be faulty memory. However, I have seen RAM sticks glitchy if not seated properly (loose or not fully inserted) or just breaking down, but most times memory just fails in the machines I have had RAM failures occur. There are PC techs on the forums that can better diagnose this type of problem though and have far more experience.

---

### Post by deserthowler on 2011-01-05
> **TBABill said:**
> +1. The fact that the system will come back and work normally until the next shutdown sounds like a heat or power issue. I'd still run MEMTEST just because it's easy but the problem from the explanation sounds too intermittent to be faulty memory. However, I have seen RAM sticks glitchy if not seated properly (loose or not fully inserted) or just breaking down, but most times memory just fails in the machines I have had RAM failures occur. There are PC techs on the forums that can better diagnose this type of problem though and have far more experience.

I had this type problem with some older machines.  One ran about 8 hours then crashed.  I restarted and it went another 8 hours.  Memtest ran OK but I changed out memory and solved the problem.  A couple I never did find the problem with.

Earl

---

