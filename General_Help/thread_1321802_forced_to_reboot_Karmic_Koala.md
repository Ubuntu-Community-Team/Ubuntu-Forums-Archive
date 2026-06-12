---
title: "forced to reboot Karmic Koala"
date: 2009-11-10
forum: General Help
---

### Post by 2blue on 2009-11-10
I have had Karmic since a few weeks before official release. I installed it on my laptop, a Siemens Fujitsu Amilo L1310G with 1GB RAM, and only 1,7GHz processor. Now all laptops for sale are at least 2GB RAM and with the Intel core duo processor. 

I have problems with Karmic, running very slow a short time after starting up. I cannot figure out what causes it. If I use VLC media player or Totem, it can get messed up, and run very jerky, sound goes bad, and nothing will fix it except a reboot. Closing all windows and applications will not work. 

I also have a problem with Firefox and almost any web-page can lock up my computer, or make it very slow. I often get a message asking me if I want to stop a script running that can make computer unresponsive. Computer sometimes get unresponsive and screen locks and goes gray for a shorter or longer period of time. Reboot helps. 

I am also wondering of Ubuntu is controlling fan and ventilation of computer. This is usually run by BIOS, but is Ubuntu overriding BIOS some how? When I reboot after using the machine for a while, fan goes on and stays on. If I don't reboot fan goes mostly on low no matter if it gets hot or stays cold. 

To sum it up, I think there are mainly two issues; I. computer goes slow, unresponsive and applications stops working properly, like media player and browser. II. Fan doesn't step up to cool the system properly. 

Is there anything I can do about this? Any thoughts on the problems?

---

### Post by prshah on 2009-11-10
> **2blue said:**
> I installed it on my laptop, a Siemens Fujitsu Amilo L1310G with 1GB RAM, and only 1,7GHz processor. 

I have problems with Karmic, running very slow a short time after starting up.

Is there anything I can do about this? Any thoughts on the problems?

I'm using Karmic without problems on a Fujitsu Lifebook 1Gb, 0.9Ghz Centrino.

From what you describe, I'd suspect that 
either
[indent] a. you have some logical damage to the filesystem structure[/indent]
or
[indent] b. You have a rogue / runaway process eating up CPU cycles.[/indent]

First, I suggest you give the following command in a terminal (Applications-Accessories-Terminal), and then reboot. This will trigger a filesystem check. Any problems should be fixed automatically, please post back with details otherwise. ```
sudo touch /forcefsck
```

If that does not prove the be the case / solve the problem, check for any processes using high CPU values. You can do this from the GUI by System-Administration-System Monitor-Processes (Click twice on the "%CPU" column to sort processes based on CPU usage), and look for any processes consistently using over 50~60% of your CPU. If you would like to post this information here, it can be better garnered from the terminal```
top -b -n 1 | head -10
```

Please post back with details if you require further help.

---

