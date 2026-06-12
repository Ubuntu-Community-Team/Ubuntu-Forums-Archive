---
title: "CPU spikes every couple seconds"
date: 2011-02-05
forum: General Help
---

### Post by Jonny87 on 2011-02-05
I've noticed that my CPU keeps spiking every couple seconds. I it will jump from 2 or 3% up to 40% or even more. I've tried to find whats causing it using "top" but finding it hard to pinpoint it. any one got any ideas?

---

### Post by duanedesign on 2011-02-05
I like htop much better then top. If you install htop you should be able to see the offending process. It might be a kernel thread and that is why its not showing in top, they are hidden by default. In htop you can hide/show kernel threads with "K" (shift+k). I think htop defaults to sorting by CPU usage. You can change the order of the list with f6 and selecting from the list that pops up i.e. CPU, RAM, PID, command, etc.

Occasional spikes as long as they are not prolonged and/or effect performance i would not worry about.

good luck.
duanedesign

---

### Post by Jonny87 on 2011-02-06
> **duanedesign said:**
> I like htop much better then top. If you install htop you should be able to see the offending process. It might be a kernel thread and that is why its not showing in top, they are hidden by default. In htop you can hide/show kernel threads with "K" (shift+k). I think htop defaults to sorting by CPU usage. You can change the order of the list with f6 and selecting from the list that pops up i.e. CPU, RAM, PID, command, etc.

Occasional spikes as long as they are not prolonged and/or effect performance i would not worry about.

good luck.
duanedesign

Thanks for the tips. I have a new cli tool. "top" was like one of my favorite tools, its quicker for me to go "Ctrl+Alt+T" then type "top" enter, than it is to find system monitor in the menu. now its going to be htop. I never even knew about it till now. thanks.

there are two that seem to stand out to me the first is;
```
aptitude search ~U
```
It seems to pop up at the very top every now and then and the cpu spikes at the same time. I wasn't sure about this cause I thought aptitude was a trustworthy thing. Perhaps someone can shed some light on this?

The other which I'm really unsure of is;
```
/usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-V6eIfC/database -nolisten tcp vt7
```
This is a confusing one I'm not sure and going by what it says, i'm hoping its lagit and has something to do with gdm.

---

