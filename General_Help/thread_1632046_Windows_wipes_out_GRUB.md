---
title: "Windows wipes out GRUB"
date: 2010-11-27
forum: General Help
---

### Post by chindichor on 2010-11-27
Hi,

I've a dual boot machine with Windows XP and Ubuntu 9.10. When I log-in to Windows and then restart (or shutdown then start) the machine, it goes into infinite reboot loop at the point when GRUB options should be shown. (I do not see the GRUB options and the machine reboots) 

The weird thing is it does not happen all the time. It's like everytime I restart Windows, 25% times, the GRUB is wiped out.

Everytime this happens, I've to re-insert Ubuntu installation CD, go to rescue mode -- pass through a long process, and reinstall GRUB... and I get things functional once again for some more time before I need to repeat the GRUB install.

Any help appreciated.

---

### Post by chindichor on 2010-11-27
Please ignore the tag Kubuntu in the title. I have Ubuntu 9.10.

---

### Post by dougalkerr on 2010-11-27
Next time you get into Kubuntu go to Terminal and enter 'sudo grub-update'. It is possible that there is a fault with the grub version you are using from the cd.

---

### Post by drs305 on 2010-11-27
There are a few Windows apps, such as HP ProtectTools and Dell Data Safe / Recovery which write information to an area in the MBR which Grub2 uses. If you boot into Windows and one of these apps runs it's possible to lose the Grub2 MBR info.

If this is the problem, you can remove/disable these apps, install G2 to another drive if you have one in your system, or possibly use a different bootloader.

---

### Post by carl4926 on 2010-11-27
Some Vendor driven anti-virus now cover the boot sector and BIOS.

There are known issues, particularly with grub 2

This may or may not apply to you

---

### Post by carl4926 on 2010-11-27
> **drs305 said:**
> There are a few Windows apps, such as HP ProtectTools and Dell Data Safe / Recovery which write information to an area in the MBR which Grub2 uses. If you boot into Windows and one of these apps runs it's possible to lose the Grub2 MBR info.

If this is the problem, you can remove/disable these apps, install G2 to another drive if you have one in your system, or possibly use a different bootloader.
:-)
Great minds think alike

---

### Post by chindichor on 2010-12-01
Thanks guys for quick response. This does look like, as suggested, probably Norton AV is deleting the files. But I have no proof of it wiping GRUB. Since this issue is intermittent I can't be sure until I restart machine in different OS for few times without Norton AV on. 

We can close this thread. If this issue resurfaces -- I will start a new one referring this thread and with new information.

Thanks again.

---

### Post by carl4926 on 2010-12-01
Just to say - I had a machine I look after with W7 on it, where a Windows update repaired it's boot code. Where you get the 'Shut Down' to install updates.
I have seen before on a Vista SP1 install, where the SP won't install because of grub. You have to do a boot sector fix for win and then re-install grub - just to install the lousy SP

---

### Post by chindichor on 2010-12-01
: ) yeah. Sometime back, I had to do mbrfix followed by bootfix followed by GRUB reintall to get auto-update install what it wanted.

---

