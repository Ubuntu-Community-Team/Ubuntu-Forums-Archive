---
title: "How do you find which video chipset you're using?"
date: 2010-06-06
forum: General Help
---

### Post by rainbowagent7 on 2010-06-06
Can anyone tell me where to look to find out which **chipset** my video card uses and how much **memory** it has? I also need to find out which **motherboard** I have and the **BIOS** version. I know these are fairly elementary questions, but school starts for me tomorrow and I don't have a lot of time to mess with a lengthy search. I just plan to update my BIOS, and if that doesn't solve my hardware issues I will create an xorg.conf file and force my machine to use a decent setting. I've been having researching this thoroughly and have a firm understanding of what's going on, but I'll be damned if I can't remember these basic commands. All help will be greatly appreciated, thanks in advance.

---

### Post by WorMzy on 2010-06-06
I believe the command you are looking for is lshw (list hardware)

Use it with sudo and pipe it into more or less, e.g. ```
sudo lshw | more
``` or redirect the output to a file, e.g. ```
sudo lshw >> hardware.txt
``` because it returns more information than a terminal can display by default.

EDIT: Actually, I jsut checked out my lshw output, and it makes no mention of the video memory. You may want to try sysinfo instead: ```
sudo apt-get install sysinfo && sysinfo
```

---

### Post by rainbowagent7 on 2010-06-06
Thanks, I'll have to remember to kick myself for forgetting that one!

---

### Post by clhsharky on 2010-06-06
rainbowagent7

 hardinfo  has GUI and in repository.

When installed can be found in Applicatins> System Tools> System Profiler and Benchmarks


Sharky

---

### Post by rainbowagent7 on 2010-06-07
Thanks Sharky.

---

