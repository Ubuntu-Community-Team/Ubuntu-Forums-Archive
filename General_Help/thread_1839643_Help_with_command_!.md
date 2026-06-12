---
title: "Help with command !"
date: 2011-09-06
forum: General Help
---

### Post by draco2011 on 2011-09-06
I'm using an acer aspire one (A150)

How can I do this 

***"Add this to your /etc/rc.local to enable Acer Aspire One Fan driver fan control: ***
***echo -n "enabled" > /sys/class/thermal/thermal_zone0/mode"***

Please mention step by step instructions :)

---

### Post by nothingspecial on 2011-09-06
One thread on one subject please.

---

### Post by 3rdalbum on 2011-09-06
> **draco2011 said:**
> I'm using an acer aspire one (A150)

How can I do this 

***"Add this to your /etc/rc.local to enable Acer Aspire One Fan driver fan control: ***
***echo -n "enabled" > /sys/class/thermal/thermal_zone0/mode"***

Please mention step by step instructions :)

[SIZE="3"]**READ ALL THIS.**[/SIZE]

Install Ubuntu 11.04 and see if the fan is controlled to your satisfaction. This is a netbook with an older Atom CPU, so don't expect it to be totally silent. If the fan works okay, then you don't need to mess with anything.

If you're sure you need this thing done, then I'd suggest a trial run. Go into the terminal and run this command:

```
sudo echo -n "enabled" > /sys/class/thermal/thermal_zone0/mode
```

This will apply that setting **until you reboot** so you can check that it works safely. If your computer crashes, **DO NOT CONTINUE THE INSTRUCTIONS**.

If you find that there's an improvement and you want to be using this setting all the time, you need to open up the file /etc/rc.local as root (administrator): 

```
gksudo gedit /etc/rc.local
```

(in the terminal)

and then paste in the line "echo -n "enabled" > /sys/class/thermal/thermal_zone0/mode" (without the quote marks) on a line of its own, before the "exit 0" line. Save your changes. When you reboot, the setting will be applied at the end of the boot sequence.

---

