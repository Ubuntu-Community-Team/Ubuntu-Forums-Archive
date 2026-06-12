---
title: "holy cow!!! what the F?  ubuntu 10.04 just uninstalled itself!!!"
date: 2010-07-03
forum: General Help
---

### Post by abedepaul81 on 2010-07-03
it was like I was watching Ubuntu slowly kill itself!!! 

I was uninstalling gimp from the synaptic manager because I initially installed GIMP from the synaptic manager but it didnt show up in my menu.....so I was going to install GIMP from command line .......  I went to click apply after checkboxing to uninstall about 5 GIMP packages ...and when I did.....

It started to say removal of ......my nvidia driver, and firefox and kept going and going slowly taking away all the menu items ....till it crashed  and now it does not even show up on my bootloader to choose if I want to book into windows or ubuntu.

could it be that I checked something in synaptic to completely remove the whole OS????
that is highly doubtable.

can someone help me understand so I dont do it again....cause I couldnt even exit synaptic when It was removing all of these files....it took 15 min to do so then it crashed and I rebooted to see I can only choose to boot into windows xp.

thank you in advance

---

### Post by Kimm on 2010-07-03
Yes, you must have accidentally checked some system critical files along with the gimp. Searching for "gimp" in synaptic yields results that are not exclusively used the gimp (such as Glib and GTK), also the gimp is only split into 2 packages (gimp and gimp-data), so the other three (you say you removed 5) have to have been something else.

Now, I'm not sure what would happen if you removed GTK and Glib, but it would wipe out most of the system (though, not sure why it would disappear from the boot loader).

Unless you know exactly what you are removing, I suggest you use the Ubuntu Software Center in the future, Synaptic can be a bit more risky (as you may have noticed).

---

### Post by jwbrase on 2010-07-03
> **Kimm said:**
> Yes, you must have accidentally checked some system critical files along with the gimp. Searching for "gimp" in synaptic yields results that are not exclusively used the gimp (such as Glib and GTK), also the gimp is only split into 2 packages (gimp and gimp-data), so the other tree (you say you removed 5) have to have been something else.

Now, I'm not sure what would happen if you removed GTK and Glib, but it would wipe out most of the system (though, not sure why it would disappear from the boot loader).

Well, if Grub depended on something he removed...

---

### Post by abedepaul81 on 2010-07-03
that is funny then ....wow I didnt know the power behind synaptic ....I will respect it more now.

Thank you for your support

---

### Post by Kimm on 2010-07-03
> **jwbrase said:**
> Well, if Grub depended on something he removed...

Well yeah, but when I did a search for gimp I didn't find anything that seemed connected to grub, the kernel or similar, I could be wrong though.

---

### Post by cgroza on 2010-07-03
Life is hard.Even Ubuntu killed itself.:lolflag:

---

### Post by ajgreeny on 2010-07-03
Just for the sake of interest you could easily find exactly what was removed by looking in the log files using a live CD and in ```
gksu nautlius
``` to get root permissions, navigating to ```
/root/.synaptic/log
``` of the installed system, if it's still there, and looking at the most recent log file.  It should contain everything that was done by synaptic at that final use.

---

