---
title: "Most recent updates messed with Grub - how to check update log?"
date: 2010-06-11
forum: General Help
---

### Post by prupert on 2010-06-11
Hi

After installing the most recent load of updates, my Grub configuration has been changed (showing the menu all the time at boot). There was no message to show that Grub was being reconfigured.

This is very bad behaviour on the part of the maintainer, as messing with your Grub config can totally bork your install.

Where can I find an update log to see what files were automatically updated so I can hunt out the cause of this issue (i.e. what update was applied) so I can then post a bug?

Cheers

---

### Post by plucky on 2010-06-11
> **prupert said:**
> Hi

After installing the most recent load of updates, my Grub configuration has been changed (showing the menu all the time at boot). There was no message to show that Grub was being reconfigured.

This is very bad behaviour on the part of the maintainer, as messing with your Grub config can totally bork your install.

Where can I find an update log to see what files were automatically updated so I can hunt out the cause of this issue (i.e. what update was applied) so I can then post a bug?

Cheers


**System > Administration > Synaptic Package Manager > File > History** will show you what packages were updated.

Did you have it set up to not show the Grub2 boot menu?

Possibly the new linux image created another entry in the boot menu caused your problem.It would have run the update-grub command.

Good Luck

---

### Post by philinux on 2010-06-11
> **prupert said:**
> Hi

After installing the most recent load of updates, my Grub configuration has been changed (showing the menu all the time at boot). There was no message to show that Grub was being reconfigured.

This is very bad behaviour on the part of the maintainer, as messing with your Grub config can totally bork your install.

Where can I find an update log to see what files were automatically updated so I can hunt out the cause of this issue (i.e. what update was applied) so I can then post a bug?

Cheers

Click the grub 2 link below to configure your desired behaviour. By default grub menu should not show if only one OS on system. If update-grub detects more then one it will then show up on reboot.

---

### Post by prupert on 2010-06-11
Thanks for the heads up Plucky.

Yup, Grub was configured to hide the boot menu, as I only have one OS installed. 

I noticed that on upgrading from Karmic to Lucid, it shows the boot menu on each boot, even if there is only one OS. I had read through [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) before in order to hide the menu. I guess I will have to do so again.

---

