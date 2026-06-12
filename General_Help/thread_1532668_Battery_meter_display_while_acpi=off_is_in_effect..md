---
title: "Battery meter display while acpi=off is in effect..."
date: 2010-07-16
forum: General Help
---

### Post by ChosenDev on 2010-07-16
Hi, 

I recently had to turn ACPI off because of major errors like the child_rip error, but now I don't have battery support or anything like that. No battery meter, etc. Is there a way I can get this while ACPI is off?

Thanks.

---

### Post by ChosenDev on 2010-07-16
Please help me :(

I can't even get my computer working with Linux, and wasted half a day on this.

---

### Post by schulwitz on 2012-06-24
For those who have the same problem (i.e. no battery meter or shutdown ability when acpi=off) here's a solution.

Edit your Grub 2 linux boot script from terminal:
> sudo gedit /etc/grub.d/10_linux

Find the line that reads:
```
GRUB_CMDLINE_LINUX_DEFAULT="$GRUB_CMDLINE_LINUX_DEFAULT"
```
and make it
```
GRUB_CMDLINE_LINUX_DEFAULT="$GRUB_CMDLINE_LINUX_DEFAULT pci=noacpi"
```

Save changes and exit.
Then update your grub.cfg file by typing:
> sudo update-grub2
then
> sudo reboot

If setting "pci=noacpi" didn't work, try the other ACPI boot options specified at [https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI).

---

### Post by overdrank on 2012-06-24
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

