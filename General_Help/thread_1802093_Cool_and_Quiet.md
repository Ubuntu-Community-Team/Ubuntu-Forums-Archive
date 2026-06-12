---
title: "Cool and Quiet?"
date: 2011-07-11
forum: General Help
---

### Post by dzwestwindsor on 2011-07-11
Hello,

I have an AMD Athlon Regor 2.8 Ghz Dual Core CPU

About a month ago I overclocked the bad boy to 3.36 Ghz, on stock voltage.

Since I have an AMD chip, I have the Cool and Quiet feature. 

With CnQ on, it never shows more than 2.8 Ghz (my stock speed), even on Full Load. However, with it off, it shows the correct 3360 Mhz all the time. 

I would like to keep CnQ, as well as my overclock. I've read in forums that it's okay to do that, that CnQ will automatically clock up to overclock when needed.

But for me, with CnQ on, it only hits 2.8. Nothing more. 

Is this an Ubuntu problem? Is there a setting where I can change the maximum allowed speed of my CPU?

I would really like to know!

Thank you :)

---

### Post by psusi on 2011-07-11
What is the "it" in "it shows the frequency"?

What does cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies show?

---

### Post by pqwoerituytrueiwoq on 2011-07-11
[http://www.overclockers.com/forums/showthread.php?t=618115](http://www.overclockers.com/forums/showthread.php?t=618115)
that may prove useful

---

### Post by dzwestwindsor on 2011-07-11
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies

shows 2800 mhz under full load.

But I know I OC'ed to 3.36 Ghz. (cause with CnQ off, my chip is running at 3.36)

But with CnQ on, it's not hitting it. Or at least it's not showing it that way...

Is there a way I can the ceiling for CPUFreq? It says the max is only 2.8ghz now, is there a file or something I can edit to make it go up to my desired 3.36ghz?

[SIZE=1]But anyways... I'm starting to wonder if it's actually nessasary to enable QnC... I don't see much of a difference with it on anyways... (in terms of CPU temp/fan speed)[/SIZE]

---

### Post by psusi on 2011-07-12
scaling_available_frequencies shows all available frequencies, not the current one.

---

