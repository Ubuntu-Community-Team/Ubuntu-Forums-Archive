---
title: "Restore Functionality after /home partition fills up"
date: 2010-05-17
forum: General Help
---

### Post by tom.swartz07 on 2010-05-17
Over the course of the past few weeks, I have noticed that a number of people have had their /home partitions inexplicably fill up after upgrading to Lucid or after installing many new programs that they did not expect. This would sometimes leave their systems in an unbootable state.


In order to fix this, you simply need a LiveCD or a LiveUSB version of Ubuntu (preferably the version that you are currently running)


Boot up and open Gparted. Its in the System>Administration menu

Once it's loaded, look for your /home partition and note the partition number: In this image- it is /dev/sda6

[IMG]http://lh6.ggpht.com/_tORug_uHNu4/S_HfXAj80RI/AAAAAAAAAcE/AHO9FDiuPkM/s800/Screenshot-1.png[/IMG]

Next, assure that ALL of the partitions are unmounted. **This is very important. You will lose all of your data if there are any mounted partitions while you are working on the drive!**

You might have to "Swapoff", meaning, clear the swap file for Ubuntu, so that it is free to move. Just right click and do so:
[IMG]http://lh3.ggpht.com/_tORug_uHNu4/S_HfXLFhZzI/AAAAAAAAAcM/_Gp4ZFtHEPo/s800/Screenshot-3.png[/IMG]

Now, its time to move the partitions. You will need to give yourself some space around the /home partition, so that you could 'grow' it larger. 

Be sure to 'grab' the corner on the side, rather than 'drag' the partition around.

Add more space, Apply using the checkmark on the top bar.


BE PATIENT!!!! The process of moving your data can be very time intensive. If you hurry it, you will only end up breaking your system and losing all of your data.


Once it's completed, reboot, and youre all set!

---

