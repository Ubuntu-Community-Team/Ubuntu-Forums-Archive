---
title: "ubuntu crashing due to compiz"
date: 2009-09-25
forum: General Help
---

### Post by migs73 on 2009-09-25
PLEASE HELP. I have managed to crash ubuntu by asking too much of my processor in compiz. Cannot open any app although can get logged in ok.How do I disable compiz from a terminal login to allow me to start again? Exuse poor typing etc. but I am doing this on my wii.

---

### Post by NightwishFan on 2009-09-25
If you can uninstall compiz, it can be re-added later.

```
sudo apt-get remove compiz
```

---

### Post by XDevHald on 2009-09-25
> **NightwishFan said:**
> If you can uninstall compiz, it can be re-added later.

```
sudo apt-get remove compiz
```

Also remember by doing this you may end up ruining your display such as window borders (not being able to close applications) and full functional display. A warning to the thread owner should have been applied.

***Do the following below in your gnome desktop, not terminal***

Uninstall compiz **apt-get autoremove compiz** then goto your gnome menu and click on System > Administration > System Monitor (Then select the Processes tab) and locate the following and set them to **Priority -17**. 

[LIST]
[*]compiz
[*]compiz.real
[*]compiz-decorator
[/LIST]

This will set a low requirement of to the processes that are hogging the most memory. Please do this to all processes running over 10MB of usage and up to lower your RAM % and CPU % from Xorg.

---

### Post by migs73 on 2009-09-25
Thanks guys
Unfortunately I had already ran the sudo apt-get remove compiz command and yes it did cause problems with my window borders and still gave me problems with crashing. Next I went into change desktop background (right click on desktop) and selected visual effects> none. This then set all my window borders etc back to normal and everything was okay. I then went into System>Preferences and to my surprise Compiz manager was still there and was working (hadn't I uninstalled this???). Went into this and reconfigured everything back to how it was before I 'broke the camels back' and is now running fine.
XDevHald,
I will now lower the priority of my processor hungry apps as you suggested just in case I get greedy with my visual effects again in future. I have also made sure I have a force quit button on my panel!

---

### Post by migs73 on 2009-09-25
XDevHald
tried to do as you suggested, but the change priority window suggests a lower number -17 (0 is the default of all my processes) gives a higher priority to that app. Surely this is the opposite of what we want to achieve. Also compiz-real is the only one of these above 10Mb (14.4Mb). The only other apps above 10Mb are firfox and python with nautilus not far behind at 9.8Mb. Do I really want to change the priority of these apps??

---

### Post by XDevHald on 2009-09-25
The high priority means that it's running the most out of the memory and is a high priority to lower the percentage and amount of usage. I have set firefox and all compiz and every python process to -17 and not one process is running over 7MB.

Also my RAM % is always under 30% and CPU is always under 10% unless I am running a lot of applications which is never the case. Hope this helps.

---

### Post by migs73 on 2009-09-29
I have tried setting the priorities as you suggested and although it appears to change on the slider bar when I hit 'change priority' the computer works for a few seconds and then shuts down that window. When I open system monitor again the nice value is back at zero and the processes are back at the 10Mb+ that they were before. Is there another way of changing the value (I was right clicking on the process name in SysMon and then selecting change priority, adjust the priority on the slider then click 'change priority')? I have just noticed Firefox is currently running at 84Mb!!

---

### Post by XDevHald on 2009-09-29
Hey migs,

I need to know if you're running a development desktop such as Karmic 9.10 or lower. This will help troubleshoot if you're on a testing environment or not. Thanks

---

### Post by migs73 on 2009-10-20
Sorry for my delay in response, I am running the Gnome 2.26.1 desktop. Hope this helps.

---

### Post by XDevHald on 2009-10-21
> **migs73 said:**
> Sorry for my delay in response, I am running the Gnome 2.26.1 desktop. Hope this helps.

Wow, time to upgrade to 2.28.1 for your gnome development. The development of 2.28.1 is being released today in the repository for Ubuntu. Do **update-manager -d** in terminal and upgrade your development or run your Update Manager to grab the latest release of Gnome Desktop.

---

### Post by migs73 on 2009-11-23
XdevHald
I am now running 2,28,1 gnome and Karmic. Still I have the same problem when trying to change the priorities, am I doing it right??
System> Administration> System Monitor> Processes> then I right click on the process I wish to change and select Change Priority.... then move slider to value I want (-17) and click 'Change Priority'.

---

