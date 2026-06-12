---
title: "Ubuntu Freezes Constantly"
date: 2010-04-23
forum: General Help
---

### Post by nSTER on 2010-04-23
I am dual booting windows 7 and Lucid RC after booting into windows then deciding to boot into ubuntu the first initial boot will freeze before the login screen appears. After a hard restart it will finally work. After I am finally able to login the system will freeze at random times which will also require a hard reboot. I am not too sure where to start on tackling this problem. This issue also exists in 9.10. I have an ATI video card(3870) and AMD cpu.

---

### Post by DawieS on 2010-04-23
Sounds that you have a hardware problem. You should tackle the problem with a process of elimination.

The first (and easiest) is to check your RAM. Run 'memtest' at the GRUB menu, to verify the health of your memory sticks. I once had a memory stick that started failing after 2 years when getting hot.

---

### Post by whistlerspa on 2010-04-23
Try checking your cable connections to your hard drives if they're SATA. I find myself having to do this every few months as the cables seem to come loose over time. I put this down to vibration caused by HD spinning.

---

### Post by nSTER on 2010-04-25
Thank you for all your suggestions. I checked my SATA cables and my memory and they are both fine. But I think I have found the problem It seems like that compiz is causing all the problems. I tried installing ati's close source drivers too and it didn't solve the problem. When I do the compiz-check script it gives me a rendering method not found error even though compiz works. I tried searching the error but I didn't find a solution.

---

