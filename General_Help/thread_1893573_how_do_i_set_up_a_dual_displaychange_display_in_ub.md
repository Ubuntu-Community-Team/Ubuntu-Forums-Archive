---
title: "how do i set up a dual display/change display in ubuntu?? help"
date: 2011-12-10
forum: General Help
---

### Post by heycoa on 2011-12-10
I need to connect a different monitor to my laptop which is running ubuntu 11.10, but it seems that it is a more difficult task than just plug and play. Can anyone please give me some direction?

---

### Post by zero2xiii on 2011-12-10
Oka,

There is NO details, so I am just going to dump some information on you and maybe it might help.

First off, it is fairly easy, even with no drivers installed. Go to:
System > Preferences > Monitors
Click detect monitors,
Now you should have to monitors. Set them up as clone's or dual screens, just as you wish.

If you have drivers installed, There is to many options, but you should then use the driver vendor tool instead.

Good luck

---

### Post by heycoa on 2011-12-10
thank you very much for your response. I can not see another monitor available under display in system settings.  Even after i hit "detect displays".  The only display available is the default laptop screen.  I have tried plugging my other monitor into the HDMI port and the VGA port with no luck. I am using an acer mini pc. The graphics card is a dedicated nVidia ion 2nd generation.  I dont know what drivers i have nor do i know how to install them.  any other ideas?

---

### Post by heycoa on 2011-12-11
any more suggestions?

---

### Post by zero2xiii on 2011-12-11
Hay,

Them you might need drivers.

I suggest backing up your /home folder if its not on a seperate partition as nvidia drivers sometimes causes issues on linux computers (mostly due to ill configurations but it might happen)

This process should be reversable, just dont fiddle around with settings manualy please:

GO to System > Administration > Hardware Drivers
Select the "RECOMMENDED" package and install the drivers, after install go to terminal and run "sudo nvidia-xconfig" and then reboot the laptop. Now you should have the nvidia drivers installed and activated.

Now check the System > Administration > Nvidia X server settings

See if you can configure multi screens under the "X server display configuration" settings (left hand side, second option on my system)

Good luck

---

