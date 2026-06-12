---
title: "HELP how to FORMAT or wipe my hD.?"
date: 2011-10-12
forum: General Help
---

### Post by CooZey on 2011-10-12
Help Ok right now im having a bad day guys. i just upgraded ubuntu 10.10 to ubuntu 11.04 and i mess up.. it hangs up with in the loading page of ubuntu and cant go on any further. right now im using recovery mode and try to fix it. but no luck.

Can someone help me how can i format may HD? i want switch may older laptop back to windowsXP?  and  BTW i dont have any partition..  when i install ubuntu i just press next next next until it install. so please help me.. teach me how to wipe or format my HD so i could go back to windows. thanks.

and does someone know what is the keyboot for usb in gateway laptop? may laptop doesn't boot from USB.

THANKS

---

### Post by Basher101 on 2011-10-12
step 1: Download a 11.04 .iso

step 2: burn a 11.04 Live CD (or make a live USB)

step 3: boot the Live CD (USB)

step 4: choose install on the screen, not "try ubuntu"

step 5: when given some options (Upgrade Ubuntu, Something else) choose **_[COLOR="Red"][SIZE="2"]Replace Ubuntu[/SIZE][/COLOR]_**

step 6: wait until install finishes.

---

### Post by coffeecat on 2011-10-12
> **CooZey said:**
> teach me how to wipe or format my HD so i could go back to windows. thanks.

If you are wanting to get rid of Ubuntu entirely and re-install Windows, you can do this from the Windows installer. Simply tell the installer to delete all existing partitions and then create your partition(s) for Windows. Or you can delete partitions from the Ubuntu live CD. Choose "try Ubuntu" rather than the installer and open Gparted where you can delete all partitions. If you use the Ubuntu live CD and Gparted you need to click on the swap partition and choose "swapoff" first otherwise you won't be able to delete one or more partitions.

**EDIT**: just realised you may be wanting to use a manufacturer's restore disc rather than the Microsoft install disc. Depending on the restore disc, you may need to delete Linux partitions with Gparted first, or the restore disc may simply wipe the whole disc anyway before re-installing Windows. It depends on the make of laptop.

---

### Post by CooZey on 2011-10-12
> **Basher101 said:**
> step 1: Download a 11.04 .iso

step 2: burn a 11.04 Live CD (or make a live USB)

step 3: boot the Live CD (USB)

step 4: choose install on the screen, not "try ubuntu"

step 5: when given some options (Upgrade Ubuntu, Something else) choose **_[COLOR=Red][SIZE=2]Replace Ubuntu[/SIZE][/COLOR]_**

step 6: wait until install finishes.


Thanks. will this still work even my ubuntu11.04 doesn't start up? i have a bad update. i upgrade my ubuntu tru update manager. and suddenly in the middle of the upgrade there was a black out for 30mins. and thats seems to happen that my ubuntu is not good right now. right now i can access through recovery menu and low graphics.

---

### Post by CooZey on 2011-10-12
Thanks.. i just followed what you guy said. and poof it became koko krunch.. good as new thanks guys.:P

---

