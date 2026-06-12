---
title: "Disabling cpu-freq scaling"
date: 2009-09-18
forum: General Help
---

### Post by FrankYellowstone on 2009-09-18
Here is a **simple** question for which I need a **simple** answer:

How can I disable _cpu-freq scaling_ running on my desktop with *Ubuntu 9.04 Desktop*.

---

### Post by dcstar on 2009-09-18
> Here is a **simple** question for which I need a **simple** answer:

How can I disable the f?cking _cpu-freq scaling_ running on my desktop with *Ubuntu 9.04 Desktop*.

Remove whatever package that is used (CPU dependant), or remove the entry from /etc/rc2.d that starts it.

---

### Post by bruno9779 on 2009-09-18
you did not give enough details

---

### Post by gradinaruvasile on 2009-09-18
Right-click on the taskbar, select add to panel, select cpu frequency scaling monitor, click on the icon, select performance from the drop down list, tick remember authorisation.

PS. You should watch your language. People over here are not pleased to talk to someone who comes over and in his first post demands to "Just give me a f?cking solution, if you have one."

---

### Post by FrankYellowstone on 2009-09-18
Thank you gradinaruvasile.

Is there any other solution? This controls frequency monitoring. What I want is just to disable such a thing to begin with. I use this computer as a remote box, and GUI dependent solution is not a solution.

I didn't say this in my original post, because I don't think this detail is needed, as I stated "**disable**", not "**control/monitor**".

Above remark is for someone else who didn't like my original post an insulted me personally. I may be a d!ckhead, and my language may not be nice... So what! We all are after the same purpose. If you don't like me or my question, don't help me. As I stated, I am really mad about this. Let me explain why: Frequency scaling is a **feature**. It sometimes helps. Especially on laptops. But there are cases where it is an obstacle. Ex: RT applications. So, this **feature** is not good for some cases, and there must be a way to disable it for good. A work around I have is:

[INDENT]cpufreq-selector -c 0 -f 2394000
cpufreq-selector -c 1 -f 2394000
cpufreq-selector -c 2 -f 2394000
cpufreq-selector -c 3 -f 2394000
[/INDENT]
commands in rc.local. But this is not a nice solution. Whatever controls it should be wiped out of the system. I suspect it is a part of hal. So, the solution I need must be something like "apt-get remove ???" The question is what is "???".

Thank you all who bare me.

> **gradinaruvasile said:**
> Right-click on the taskbar, select add to panel, select cpu frequency scaling monitor, click on the icon, select performance from the drop down list, tick remember authorisation.

PS. You should watch your language. People over here are not pleased to talk to someone who comes over and in his first post demands to "Just give me a f?cking solution, if you have one."

---

### Post by gradinaruvasile on 2009-09-18
I suspect cpu frrequency scaling is part of the kernel. I might be wrong though.
Setting the performance governor (ex. cpufreq-selector -c 0 -g powersave) will keep max speed of the cpus.

---

### Post by FrankYellowstone on 2009-09-18
Well. I think I found the solution. Apparently, "laptop-mode" and "ondemand" services are installed automatically. And, hald-addon-cpufreq is another evil for this matter. So do this:

```
rm /etc/rc?.d/S*ondemand
rm /etc/rc?.d/S*laptop-mode
mv /usr/lib/hal/hald-addon-cpufreq /usr/lib/hal/DISABLE-hald-addon-cpufreq
```

That should do it. This seems to be the final solution. It is not elegant, but after all the troubles I had, even I will be settled with a non-elegant solution. If anyone knows a better solution to wipe out cpu scaling (meaning; nailing it down into "performance" mode) by means of command line configurations, please let me know.

I wrote these here, so users like me may find it before they get mad about it, and start bothering people on the net with bad languages.

---

### Post by trundlenut on 2009-09-18
can you disable it in the machines BIOS?

---

### Post by 3rdalbum on 2009-09-18
Dude, just turn it off in the BIOS.

---

### Post by FrankYellowstone on 2009-09-18
> **3rdalbum said:**
> Dude, just turn it off in the BIOS.

trundlenut and 3rdalbum:

YOU ARE MY HERO!

This is exactly what I wanted. A **simple** answer to a **simple** question:

***[COLOR="Blue"]Dude, just turn it off in the BIOS.[/COLOR]*** is plain simple and friendly.

I, indeed, found "SpeedStep" option in the BIOS, and turned it off. It solved the problem.

Cheers!

---

### Post by frodon on 2009-09-18
Please, let me remind you all that posting here we expect you to follow the Code of Conduct.

Thanks for your understanding.

---

