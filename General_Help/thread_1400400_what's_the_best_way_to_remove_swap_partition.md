---
title: "what's the best way to remove swap partition"
date: 2010-02-06
forum: General Help
---

### Post by Mia_tech on 2010-02-06
guys, I want to remove my swap partition. Probably one I would have to boot into a rescue cd and remove it, but aside from that is there any other consideration or commands that I need to be aware of?

thanks

---

### Post by samantha_ on 2010-02-06
Go into /etc/fstab
Remove the line corresponding to your swap.
Reboot and use Gparted to delete the swap.

---

### Post by warp99 on 2010-02-06
You can use gparted which you can install using Synaptic. Here's the procedure you should use:

1) Install Gparted from Synaptic
2) Open a terminal, issue the command "sudo swapoff -a"
3) Remove the swap partition using gparted
4) Edit the fstab file, use "sudo gedit /etc/fstab", then place a # in front of the swap entry like this:
```
#UUID=<$random_generation_of_numbers>    none swap defaults

```
5) Next time you reboot the swap file will no longer be available

If you use hibernate this will no longer work since the RAM is saved to the swap file.

---

### Post by dcstar on 2010-02-07
> **Mia_tech said:**
> guys, I want to remove my swap partition. Probably one I would have to boot into a rescue cd and remove it, but aside from that is there any other consideration or commands that I need to be aware of?

thanks

Start up the Partition Manager, right-click the Swap partition and select the "Swapoff" option, then you can delete it.

Take it out of /etc/fstab as per the other instructions.

---

