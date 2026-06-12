---
title: "Is my Hard Drive Dying?"
date: 2009-12-16
forum: General Help
---

### Post by WinterWeaver on 2009-12-16
I have a relatively new laptop. Bought it this year.
Currently running karmic with ext4. (Note that Visa is also on another partition).

I've recently started getting error messages on the ubuntu splash screen, that it cannot mount drives or devices, when trying to do disk checks. It always finished booting however.

Today, I was working on a clients website, and whilst starting gvim, the system froze. I held down the power button, to switch off the laptop and restart.
Grub came up, selected my latest kernel to boot, ubuntu splash came up and then flashed a bit, aaaand... I was greeted by a prompt, saying that the boot device could not be mounted. O.o

I ran fsck, and it fixed a couple of linkes or something, and then after a reboot, everything was fine again, but I cannot shake the feeling that there is something Looming.

Does anyone have advice for me on how to get down to the cause of this problem?

Another anomaly, sometimes when I copy files into a folder (nautilus), those files will not show in nautilus. Refreshing doesn't help. Reloading the file browser does not help.
I will be able to see the files in the terminal via  the ls command. If I open nautilus within that folder via the terminal with "nautilus ./" ... then the files will be visible.

I hope that is enough information for now.

Thanks,

WW

---

### Post by prem1er on 2009-12-16
Hopefully common sense, but you should make sure you backup all your files asap if you feel like your drive is going bad.

---

### Post by bodhi.zazen on 2009-12-16
Hard to know if it is the file system or hardware.

See if this link helps : [http://www.cyberciti.biz/tips/linux-find-out-if-harddisk-failing.html](http://www.cyberciti.biz/tips/linux-find-out-if-harddisk-failing.html)

Otherwise, just because it is a good habit, you should back up your data (to an external device such as a flash drive of CC / DVD).

---

### Post by Yvan300 on 2009-12-16
Last i checked there is a disk checker that comes shipped with karmic koala that monitors the health of your drives. Not sure how accurate it is but it's a start :)

---

### Post by Ocxic on 2009-12-16
i get the same messages, your kernel is booting faster then it can detect/mount your hard drives and partitions.

---

### Post by WinterWeaver on 2009-12-16
Thanks guys,

I am actually making backups every night with Back in Time ... great app :)

@bohdi.zhazen, I'll have a look at the link you provided.

@Yvan300, do you by any chance remember what the name of the application was?

---

