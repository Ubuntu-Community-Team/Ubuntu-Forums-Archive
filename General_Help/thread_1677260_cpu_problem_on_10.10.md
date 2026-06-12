---
title: "cpu problem on 10.10"
date: 2011-01-28
forum: General Help
---

### Post by aeon.flux on 2011-01-28
hi there, i have a problem with my ubuntu, here's some description and i hope, that somebody will be able to help me

i have HP Elitebook 9540w with intel i7 720QM 1.7GHz and 8GB ddr3 ram ( some more specs can be found here [http://www.alza.sk/hp-elitebook-8540w-d162490.htm](http://www.alza.sk/hp-elitebook-8540w-d162490.htm) you can use google translate) and i have dual boot windows 7 professional and ubuntu 10.10 (the cpu is 64-bit and i have 32-bit ubuntu 10.10, kernel 2.6.35-23 with gnome 2.32.0
i did upgrade from 10.04 when 10.10 came out and was very pleased by fast booting. but after a while (maybe by the updates) the system was so slow and the CPU cooling system was so loud.
i was not using ubuntu so much but now i want to solve this and use ubuntu every day again.
when i open system monitor, there are 2 CPU cores, the first is permanently working on 95-98%, the second aroud 15%. (there should by 8 cores, because i have i7 quad core with HT technology), but when i look on processes, there a lot of processes, the most consuming process is gnome-system-monitor and it takes only 6%, compiz takes 2%..
the notebook is hot, so the cooling system is very loud and the battery life is much shorter than with windows. even when i have just browser opened.. do you have any ideas, how do solve this? what does the CPU doing?! it really looks like a system problem..

---

### Post by silvagroup on 2011-01-28
Try some of [http://ubuntuforums.org/showthread.php?t=597998]("http://ubuntuforums.org/showthread.php?t=597998")first post and see what happens.

---

### Post by wormyblackburny on 2011-01-28
I'm having a hard time figuring out why you would be running 32 bit instead of 64 with that nice of a machine? Is there something in particular that you use that isn't supported in 64bit?

---

### Post by aeon.flux on 2011-01-29
> **wormyblackburny said:**
> I'm having a hard time figuring out why you would be running 32 bit instead of 64 with that nice of a machine? Is there something in particular that you use that isn't supported in 64bit?

i had no experience with 64 systems when i was moving from hp pavilion 32bit to elitebook 64 and when i installed 64 ubuntu, i had some problems with drivers and some programs was not working correctly. when i tryed 32bit, everything was just ok.

---

### Post by aeon.flux on 2011-01-29
> **silvagroup said:**
> Try some of [http://ubuntuforums.org/showthread.php?t=597998]("http://ubuntuforums.org/showthread.php?t=597998")first post and see what happens.

it seems like problem is not in cpu. i had NO problems few months ago, also the windows is running without any problems. I've did some changes in bios last weekend, and i was searching for changes and tried to restore the exact settings, but windows is still running the same and ubuntu does still the same problems, so i think that problem is not here. I'm actually downloading 64bit ubuntu and I'll try to install it and I will write back, what happened. Thanks for help guys :)

---

### Post by aeon.flux on 2011-01-29
so i've just installed ubuntu 64-bit version. after few problem with runnings systems and using recovery mode i'm finally online, i have installed all the latest updates and drivers (just nvidia driver for quadro fx 880m).

the system monitor shows me 8 CPU cores. the 1st is working on 50-80%, 3rd core is around 20% and other less than 5%. the last 3 cores works on 0%. it looks like ubuntu can't use my CPU properly

the fan is still so loud and the pc is quit warm. but when i look on processes, the app that use most of a CPU is system monitor - around 8%.

after all this, im asking myself: Why is ubuntu better than windows, when there's less working drivers, shorter battery life and more cpu usage?

im going to look at the cpu frequency scalling..

edit: i've just used that frequency scalling and from that second, the fan is totally quiet. i can't hear it. the first core is working almost on 100%, but the pc is getting colder...

---

