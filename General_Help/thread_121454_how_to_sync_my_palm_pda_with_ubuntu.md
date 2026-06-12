---
title: "how to sync my palm pda with ubuntu?"
date: 2006-01-25
forum: General Help
---

### Post by hanzj on 2006-01-25
hello,
i'd like to sync my palm pda with my ubuntu (gnome/breezy) computer. I have a Palm Zire.
Basic PIM data is all i need synchronized: calendar, tasks, contacts, notes. In the Ubuntu Hoary days, i was able to successfully sync my visor Pro (palm os) pda with J-Pilot. I'm willing to use J-Pilot again. How do i do so? 

I have tried finding out what port my PDA connects to. I ran ```
sudo tail -f /var/log/messages
```, then plugged in my Palm Pda, and then pressed the hotsync button. I get 
> Jan 25 21:21:13 localhost kernel: [4458034.698000] usb 2-1: Handspring Visor / Palm OS converter now attached to ttyUSB0
Jan 25 21:21:13 localhost kernel: [4458034.702000] usb 2-1: Handspring Visor / Palm OS converter now attached to ttyUSB1
Jan 25 21:21:13 localhost usb.agent[17496]:      visor: already loaded

When my Palm PDA gave up trying to sync, the results on the CLI were:
> Jan 25 21:22:19 localhost kernel: [4458101.392000] usb 2-1: USB disconnect, address 25
Jan 25 21:22:19 localhost kernel: [4458101.394000] visor ttyUSB0: Handspring Visor / Palm OS converter now disconnected from ttyUSB0
Jan 25 21:22:19 localhost kernel: [4458101.400000] visor ttyUSB1: Handspring Visor / Palm OS converter now disconnected from ttyUSB1
Jan 25 21:22:19 localhost kernel: [4458101.403000] visor 2-1:1.0: device disconnected

A question: Why are 2 ports being used: ttyUSB0 and ttyUSB1?

I tried using gpilotd-control-applet to set up my device, I have tried the following ports in the "Devices Tab":
/dev/ttyUSB0
/dev/ttyUSB1
/ttyUSB0
/ttyUSB1

but none seem to work when I go to "Pilots Tab" and hit the "Get From Pilot" button.

I'm willing to try any other program if it's easier to use.


Please help a newbie.
[-o< 
:confused:

---

### Post by MartinG on 2006-01-25
Not sure if it's a great help to you if you're using gnome, but I find KPilot and the linked KDE apps work very well (Dare I say better than the Gnome or J-Pilot offerings? [-o<   )

---

### Post by hanzj on 2006-01-25
i'm running gnome. i'll look into kpilot in the future, if i can't sync with native programs. just to confirm kpilot can work in gnome, right?

---

### Post by MartinG on 2006-01-25
[QUOTE=hanzj]i'm running gnome. i'll look into kpilot in the future, if i can't sync with native programs. just to confirm kpilot can work in gnome, right?[/QUOTE]Yes, but it will want all the base KDE libraries; no problem if you're already using some KDE apps, but otherwise it will be a big install.

---

