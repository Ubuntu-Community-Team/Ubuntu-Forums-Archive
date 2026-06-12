---
title: "My pc is getting slower and slower"
date: 2010-09-26
forum: General Help
---

### Post by octohedra on 2010-09-26
Hello, 

Well the thing is, that the first month of my fresh linux install was full of wonders, working perfect, fast, smooth.
But now... a few days ago, the computer started to go slower and slower, now it freezes even watching youtube videos, and its overall very slower than when i installed everything. I didnt install any new software these days so i dont know what could be the problem, i was wondering if maybe there is a way of cleaning the temp files or cache any other way of speed things up...

Thank you very much for your answers.

---

### Post by Ultra_Man on 2010-09-26
sudo apt-get autoclean removes old .debs.

---

### Post by Dr. C on 2010-09-26
Are you visiting a lot of sites with Flash? If so one thing to try is getting rid of the Local Stored Objects or "Flash Cookies". Installing the [Better Privacy]("https://addons.mozilla.org/en-US/firefox/addon/6623/") extension in Firefox in an easy way to deal with LSOs. I have noticed a marked improvement in performance after deleting the LSOs in some cases over 300 were removed.

---

### Post by dirghrabadia on 2010-09-26
You might want to run memtest 86+ when you boot your PC, just in case to check if your RAM is the culprit.

---

### Post by rajohns08 on 2010-09-26
im having a problem similar to this also. if i have a couple things running like pandora, and a hulu video, the video will get choppy. but even after i exit everything but the video, it will still be choppy in full screen.

---

### Post by decoherence on 2010-09-26
Bring up the System Monitor window (System -> Administration) and click the Resources tab. Look at the memory area and see if there is any swap space being used. Ideally, there shouldn't be any. If there is, click the Processes tab and click the title of the Memory column twice. This will put the memory hog at the top of the list (click it once and it'll be at the bottom of the list.) That (or something close to the top of the list) will be your culprit, if indeed a memory shortage is your problem (that would be my first guess.) 

Another thing to check is if your hard drive is filling up. But really, you'll have to check with System Monitor to get an idea.

---

### Post by octohedra on 2010-09-26
Thanks everyone for your responses, already did what you said:
Installed the firefox add-on
Did sudo apt-get autoclean
And checked the Resourses tab, and i notice something quite strange:

[IMG]http://img709.imageshack.us/img709/5135/screenshot1cz.png[/IMG]

even the CPU usage is @ 100% (Core 1) when i check the processes tab nothing will be using more than 6% of the CPU, so what is using the rest of the cpu?
Also notice there was some usage of the Swap space, even i was only using firefox. and still have 1.6gb of ram free.

---

