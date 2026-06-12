---
title: "How to change Wirless Network????"
date: 2006-02-25
forum: General Help
---

### Post by mexlinux on 2006-02-25
Hi:
I have just installed kubuntu, during installation it detected wifi, and asked for WEP key, did manual config, and gave static IP..... That was in my office.

Now, I'm at home, on a diffrent network, and, it does not work...
BUT I do not know wehre to modify and which values???

I do not have network on the laptop, please help or point to the instructions.

Please don't point to installing packages instructions, since I have not network, so I can't install.... but everithing should already be installed since it worked at the office.

In mandriva there was a nice tool net_applet showing all the avialble conections, and allowing you to change the network, what will be the kubuntu alterative?

Thanks,
Miguel

---

### Post by reptil on 2006-03-16
hola  miguel. 

i 've a similar  situation a couple of weeks and  use other computer  to collect some  information about my net in order to modify the file named "interfaces"

re u from mexico and use prodigy infinitum o what ?

---

### Post by SeanTater on 2006-03-16
In order to get to the network control, go to:

"K" (AKA: Start) -> "System Settings" ->"Network Settings"

Should be easy from there, similar to what you did already!

[color=green][i]**_Note:**_[/color]
You should have "profiles" in the settings in the control panel. Save the current configuration as "office" and then change the config, and save it as "home", that way it only takes a couple of clicks to switch between them.
However, if you have changed the settings since you left the office, you will need to reconfigure them when you get there, and save it as 'office' again. From there, you should be golden.[/i]

If you need to be able to monitor the network, use kde system guard (in "K", -> "system" -> "KSysGuard"). It monitors everything from CPU usage to Disk throughput to Network Usage to running processes. You can remove any monitor display by right clicking it and pressing remove display. You can add any display by looking through the 'tree' of available monitors in the left pane.

---

### Post by skorange on 2006-03-16
What if you frequently connect to new networks?  From a friends to a coffee shop to a school network, etc.  Is there a way to have it simply detect an existing connection and connect to it?

---

### Post by nickle on 2006-03-19
Kwifimanager should do the job with one or two clicks...

---

