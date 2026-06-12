---
title: "okay so whats with this leak"
date: 2010-02-18
forum: General Help
---

### Post by Elcid247 on 2010-02-18
There has been posts all over the place about the ubuntu memory leak and i personally have experienced it on 32 bit and 64 bit versions of ubuntu and every one keeps giving different reasons for it.

has any1 been able so far to pin it down to a final place? i really wana know whats causing this cause its a huge performance set back

---

### Post by cariboo on 2010-02-18
What program is causing the memory leak? You should be able to check using **top** in a terminal.

---

### Post by Elcid247 on 2010-02-21
well thats the problem, nothing is taking it up, if i add the memory usage, it gives around ±500 MB, but when i see in the system monitor it says 1.4 GB :S


i have nothing but firefox and pidgin, chrome gives same result even if i don't use any, it just fills up with no reason whatsoever

---

### Post by nixclusive on 2010-02-21
you can use the command, ```
free -m
``` to display the amount of memory available. The number(s) after "-/+ buffers/cache" is the actual amount of memory used/available. :)

---

### Post by efflandt on 2010-02-21
Which Ubuntu version?  People may come up with different reasons because it is not a general issue.  It must be due to some specific software, configuration, or hardware.  Did you boot from an iso image (CD or USB) or are you using a ramdisk or tmpfs?

Does **ps aux** show anything in a zombie state or race condition, or using a significant percentage of your RAM (or cpu)?

My 64-bit 9.10 has currently been up for over 3 days, and with Firefox running, either **free** in a terminal, or System Monitor show less than 500 MB being used.

---

### Post by Elcid247 on 2010-02-25
```
free -m
             total       used       free     shared    buffers     cached
Mem:          2992       2642        350          0        454       1042
-/+ buffers/cache:       1145       1846
Swap:            0          0          0
```

i've attached a screenshot for my system monitor, showing processes from all users. u can see it shouldn't add up to like 500 MB or something

its ubuntu 9.10 now on 32-bit.

i'm using my brand new [hp dv6-1390]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01882177&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&lang=en&product=4043711")

though there are some processes which have N/A under the memory field, like ata_aux or kacpi_notify, is that normal?

i have no zombies btw its all running or sleeping processes.

---

### Post by skymera on 2010-02-25
Hello

Are you running 9.10 or 10.04?

I've found Ureadahead has a bug where it DOESN'T release memory after it profiles boot.

This pushes RAM usage to 1200MB-ish, but RAM usage goes back to normal on subsequent boots, until the boot is profiled again.

---

### Post by 2hot6ft2 on 2010-02-25
> **Elcid247 said:**
> well thats the problem, nothing is taking it up, if i add the memory usage, it gives around ±500 MB, but when i see in the system monitor it says 1.4 GB :S


i have nothing but firefox and pidgin, chrome gives same result even if i don't use any, it just fills up with no reason whatsoever
Pidgin has had memory leak problems for a long time. Maybe it still does.

[pidgin memory leak search]("http://www.google.com/search?q=pidgin+memory+leak&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a")

---

### Post by &amp;)ky#)^ on 2010-02-25
I don't usually experience any memory links on my system using Karmic.  However, Synaptic while idle just ate all my real and virtual memory.  I killed it and everything went back to normal except that Firefox hanged itself and my screen flashed black for a second and then an icon near the bottom appeared saying my display server is broken.  Anybody have anything that came close to this?

---

### Post by ubunterooster on 2010-02-25
I just read about a problem w/ firefox that devours RAM
 Turn off ALL programs, now how much is freed?

---

### Post by Elcid247 on 2010-03-02
> **ubunterooster said:**
> I just read about a problem w/ firefox that devours RAM
 Turn off ALL programs, now how much is freed?

my memory had jumped to 1.7 GB, i closed everything and now its 1.1 :S

after reopening its now 1.3 only :S

something is really screwing with my ram lol.

---

### Post by ubunterooster on 2010-03-02
bewildered...completely...
 I say back up all files. My most reasonable suspect is malware.

---

### Post by Elcid247 on 2010-03-03
> **ubunterooster said:**
> bewildered...completely...
 I say back up all files. My most reasonable suspect is malware.

um i just figured it out its my vga driver... damn ATI cards :@

i've found several posts about this but valgrinded it myself and its true, thanks for help anyways guys.

weird thing it didn't show up in xorg or compiz usage though which had me rule it out for a long time

---

