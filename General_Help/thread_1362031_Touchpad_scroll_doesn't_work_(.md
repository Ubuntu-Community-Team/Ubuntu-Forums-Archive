---
title: "Touchpad scroll doesn't work :("
date: 2009-12-22
forum: General Help
---

### Post by killians31 on 2009-12-22
Hey guys,

I pretty much got Ubuntu 9.10 fully working to my satisfaction!

The only issue i am currently facing is the non-ability to side scroll with my laptop's touch pad.

This seemed to work with Ubuntu 9.04, but after the upgrade it didn't even recognize my touch pad. I had to go through some hoops to get it working (it was a while ago, so i don't really remember what i did)

Also, while i am posting, i noticed that my notifications don't appear at the top left of my screen, they are appearing about an inch below the top left. Is this normal?

Any help is greatly appreciated!

Thanks!

-Ben

---

### Post by Qola on 2009-12-22
Backup your data and do a clean install of 9.10. Upgrading can cause a lot of problems.

---

### Post by killians31 on 2009-12-22
I would rather not reformat my partition if i do not have too, as i just got my laptop to function as i like it with all of my operating systems.

Is there any drivers or shell i can use to get this properly functioning?

---

### Post by rCXer on 2009-12-22
Make sure the horizontal scrolling is enabled. Go to System -> Preferences -> Mouse. On the Touchpad tab, Make sure "Enable Touchpad" and "Enable Horizontal Scrolling" are checked.

---

### Post by killians31 on 2009-12-23
> **rCXer said:**
> Make sure the horizontal scrolling is enabled. Go to System -> Preferences -> Mouse. On the Touchpad tab, Make sure "Enable Touchpad" and "Enable Horizontal Scrolling" are checked.

It seems that i only have the tabs: 'General, and Accessibility'...... I think this might be because Ubuntu didn't pick up my touchpad right away with the upgrade

Is there any other way you guys can think of?

---

### Post by orlox on 2009-12-23
> **Qola said:**
> Backup your data and do a clean install of 9.10. Upgrading can cause a lot of problems.

Reinstalling is the last option to solve a problem.

@killians31, do you have the package xserver-xorg-input-synaptics installed?

Do you have even a slight idea of what you did to enable the touchpad?

---

### Post by killians31 on 2009-12-23
> **orlox said:**
> Reinstalling is the last option to solve a problem.

@killians31, do you have the package xserver-xorg-input-synaptics installed?

Do you have even a slight idea of what you did to enable the touchpad?

After hunting through google, it looks like i performed this sequence:

```
1. Open a terminal (if you don’t have a mouse hooked up, use Alt+F2). 
2.Type “su”, press Enter, and give the root password 
3. At the prompt, type: 

echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe

4. At the next prompt, type “reboot”.
Your touchpad will come back up after rebooting.
```

I double checked my /etc/modprobe.d/psmouse.modprobe file, and it looks to have only 'psmouse proto=exps' in it.

I was looking at this howto, but it seems that i dont have a psmouse.conf file within my /etc/modprobe.d/ directory...

[HTML]http://www.ubuntugeek.com/howto-fix-touchpad-issues-after-karmic-upgrade.html[/HTML]

---

### Post by orlox on 2009-12-23
From those instructions, I'm guessing you're the one who created the file /etc/modprobe.d/psmouse.modprobe by issuing that command. It probably wasn't there before.

I'm not sure what that option (psmouse proto=exps) does though...If you comment that line in the file (putting a # before the line), you should return to the previous situation. Could you check that that effectively happens? If it happens, and you return to the case where you have no touchpad at all, try running these commands from the other guide, and put your output here:

```

dmesg | grep mouse
lsmod | grep psmouse

```

Also, on that other guide, I don't think the initial part with the menu.lst is needed.

---

### Post by orlox on 2009-12-23
The soluton on ubuntu-geek you linked is also [here at ubuntuforums]("http://ubuntuforums.org/showthread.php?t=1308857"). However, it seems almost no one had the file psmouse.conf, so you're not alone. I don't have one either...

Also, just as a check, run the "uname -a" command to ensure you're using karmics kernel

---

### Post by killians31 on 2009-12-25
So i just commented out the line within the psmouse.modprobe file, and strangely enough, the touchpad still works, and side scrolling is now enabled!!

Thanks for everyones help

---

