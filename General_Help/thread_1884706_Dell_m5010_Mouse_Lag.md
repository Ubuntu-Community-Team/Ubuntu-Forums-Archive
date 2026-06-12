---
title: "Dell m5010 Mouse Lag"
date: 2011-11-21
forum: General Help
---

### Post by vvvvv17 on 2011-11-21
After I purchased my Dell m5010 I was really disappointed to see that Ubuntu won't install. Well, Ubuntu 11.10 seems to be working quite well except for 1 fact: the mouse laggs terribly. I have tried a different mouse, still the same issue. However, the cursor moves normally when I use the touch pad.
Is there anything I can do to solve this problem? I have tried Ubuntu, Kubuntu and Xubuntu - they all have this issue. I really, really liked Xubuntu (Gnome 2.X fan) and this mouse lag problem is the only thing that is keeping me from installing Xubuntu on my machine.

Any help is appreciated.

Cris

p.s. I forgot to mention that I am a linux noob, so please give me advice that doesn't involve me knowing any technical stuff.

---

### Post by vvvvv17 on 2011-11-22
Bump... can anyone help please??

---

### Post by vvvvv17 on 2011-11-23
Can anyone suggest something? Anything?

---

### Post by Old Driver on 2011-11-30
Not really sure what to say. I've been dual booting Ubuntu on my M5010 since I get it,Xmas 2010. Started with 9.xx Not really sure now. I've changed OS up through 11.10 now and never had a problem using usb mouse or scroll pad. It's possible you've got a problem with usb mouse itself or maybe the usb port on your board.The usb mouse I use is a Microsoft mini. Hope this helps a little.

---

### Post by krazykarl14 on 2012-09-20
I'm sorry for posting on such an old thread, however just having installed Xubuntu (Ubuntu would not work) on my M5010, I have discovered that I am having this very same issue and I hate this stupid touch pad. I am also new to the linux world, so I am not sure if it even worth noting that I can no longer even disable the touch pad but it does however work without flaw. When it comes to use of the wireless mouse (microsoft wireless mobile mouse 4000) the cursor responds to it in a very laggy way, following all the motions I make just several seconds after the fact.

---

### Post by pissedoffdude on 2012-09-20
> **krazykarl14 said:**
> I'm sorry for posting on such an old thread, however just having installed Xubuntu (Ubuntu would not work) on my M5010, I have discovered that I am having this very same issue and I hate this stupid touch pad. I am also new to the linux world, so I am not sure if it even worth noting that I can no longer even disable the touch pad but it does however work without flaw. When it comes to use of the wireless mouse (microsoft wireless mobile mouse 4000) the cursor responds to it in a very laggy way, following all the motions I make just several seconds after the fact.

Looks like other users solved this with "acpi=off".  At the grub menu, hit e to edit whichever Ubuntu entry you boot first, then look for the line that contains "kernel" and or "ro quiet".  Once you find the line, add a space and ```
acpi=off
``` Hit ctrl+x and boot.

If this works, you can  make it permanent by typing in ```
gksudo gedit /etc/default/grub
```

Then edit this line so that it includes acpi=off
```
GRUB_CMDLINE_LINUX="... acpi=off"
```

Finally run```
sudo update-grub
``` And your changes will be permanent

---

