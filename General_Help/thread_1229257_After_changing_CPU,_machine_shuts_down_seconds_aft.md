---
title: "After changing CPU, machine shuts down seconds after turning on."
date: 2009-08-01
forum: General Help
---

### Post by anthony62490 on 2009-08-01
This is Part II of [a previous thread]("http://ubuntuforums.org/showthread.php?t=1224125") I started. Anyway, after a bit of hunting, I found a replacement AMD Athlon. This time, I was VERY careful not to yank it out of the CPU bed or bend the pins. I reconnected everything that had been previously pulled out (video card, RAM, network card, hard drive) and started it up. If the problem is not with my CPU, then it must be getting worse, because now the machine starts up and within 5 seconds, it shuts itself down. This happens before the monitor displays anything at all.

---

### Post by Kai Summers on 2009-08-01
Have you checked your PSU?

---

### Post by shp on 2009-08-01
What happens when you start it up without a cpu?

---

### Post by metalf8801 on 2009-08-01
can you get into the bios? and if so does the computer stay on if you do?

---

### Post by adamitj on 2009-08-01
I really think this isn't an Ubuntu problem :)

Well... maybe it should be your AT/ATX power supply. I had this problem after a electric lightning discharge on my house's power line. Probably the voltage is not right, it can't send the needed voltage to the motherboard.

If it's not the power supply, remove the motherboard battery and try to boot your computer (some motherboards just left the blank screen). Press reset button a few times and power off. Then put the battery in the same place you removed, and power on.

Oh... just a suggestion: You might look for a hardware technician if you can't deal with this problem. This forum is for Ubuntu related issues, and maybe you can't find a solution for your hardware problems.

---

### Post by aesis05401 on 2009-08-02
I am almost afraid to ask.. but did you be sure to apply thermal transfer goop appropriately?  Sounds like thermal shutdown.

---

### Post by anthony62490 on 2009-08-03
You know, you are right. This is not an Ubuntu question. Regardless, I finally managed to get the computer working again. I found another compatible motherboard with an AMD Athlon and transferred all components into the new box. This way, the thermal gel was never broken (i don't have any more on hand). everything works properly with just a few performance issues. Thank you very much for the suggestions.

---

