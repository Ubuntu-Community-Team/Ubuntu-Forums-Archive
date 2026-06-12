---
title: "Multiple machines, all low res screen!"
date: 2009-08-11
forum: General Help
---

### Post by HarveyBabb on 2009-08-11
I guess this is both a plea for help and a general gripe! So far I have installed Ubuntu 8.04 on 5 (wildly) different machines and all have either started out with, or reverted to, low resolution screens. In each case I have had to search through forums and blogs to come up with a "fix" that mostly doesn't stay fixed.
WHAT IS THE PROBLEM HERE??
Is there a generalized "how to" on fixing (permanently!) these video problems? I am getting so frustrated with this one single issue that I'm almost longing for Windows!

Thanks for your help and for lending an ear.

Harvey

---

### Post by oomar on 2009-08-11
well what are these pcs? > (wildly) different machines

---

### Post by ajgreeny on 2009-08-11
This will be entirely dependent on the graphics cards in the machines, so there is no way to answer your question without more info on the hardware of these computers, particularly the graphics cards installed, or what the onboard graphics are.

If you're not sure, run the command ```
sudo lshw -C display
``` on each computer and report the cards shown again here.

---

### Post by HarveyBabb on 2009-08-11
> **ajgreeny said:**
> This will be entirely dependent on the graphics cards in the machines, so there is no way to answer your question without more info on the hardware of these computers, particularly the graphics cards installed, or what the onboard graphics are.

If you're not sure, run the command ```
sudo lshw -C display
``` on each computer and report the cards shown again here.
[FONT=monospace]This is the reason for my "Gripe"! For each of these machines I've had to spend an average of an hour to search out a custom solution for the problem. In at least one case, just stopping and restarting the x-server fixed it (although a reboot did not). I have also had the problem recur for no obvious reason.
Is my experience unusual or are thousands being put off of Ubuntu because they just didn't know enough or care enough to invest this kind of time? Why is this still a problem since the same thing appears to have been going on for as long as Ubuntu has existed? (out of "Gripe" mode now, truly curious if this is an insurmountable problem)

My current problem child is a Gateway 3310, results of above follows:

*-display UNCLAIMED     
       description: VGA compatible controller
       product: 82865G Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: latency=0

Where to now?

Again, thanks for the help and place to air my frustration.

Harvey

[/FONT]

---

### Post by HarveyBabb on 2009-08-12
Any takers? Still can't get this thing to work!

Harvey

---

