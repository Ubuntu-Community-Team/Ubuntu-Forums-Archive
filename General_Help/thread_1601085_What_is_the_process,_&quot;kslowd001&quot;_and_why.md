---
title: "What is the process, &quot;kslowd001&quot; and why can't I kill it?"
date: 2010-10-19
forum: General Help
---

### Post by HTML-insane on 2010-10-19
**EDIT: Please look this way -- [http://ubuntuforums.org/showthread.php?p=9995980](http://ubuntuforums.org/showthread.php?p=9995980)**

So in Ubuntu 10.10 on a REALLY old laptop, everything works fine - except the system occasionally gets a lag spike, where the CPU is suddenly being throttled. This wouldn't be a problem, except my mother's using the laptop to play backing music for her choir and the CPU spikes are causing the music to stutter.

After much searching and eventually resorting to TOP, I found that the CPU was being throttled every 10-20 seconds or so by a process called, "kslowd001". "sudo kill -9 `pidof kslowd001`" did nothing, nor did, "sudo killall -9 kslowd001". It doesn't want to die, it just wants to throttle the CPU, and I just want it to stop.

So: what does this process actually do? Why can't I kill it? How do I switch it off, or otherwise stop it from throttling the CPU every couple of seconds so that we can actually listen to music or watch videos from the laptop?

---

### Post by HTML-insane on 2010-10-19
D'oh! Late night rookie mistake. Good old Google revealed that kslowd is a kernel process, which would explain why I can't kill it - and also revealed this forum post: [http://ubuntuforums.org/showthread.php?p=9995980](http://ubuntuforums.org/showthread.php?p=9995980)

On that note, I'm going to try the suggestion (downgrading the kernel) and move the discussion over there.

---

