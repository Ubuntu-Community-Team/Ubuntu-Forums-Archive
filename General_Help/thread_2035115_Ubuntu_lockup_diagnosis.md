---
title: "Ubuntu lockup diagnosis"
date: 2012-07-29
forum: General Help
---

### Post by Shawn67 on 2012-07-29
I have an AMD based system running 64 bit Ubuntu. I have had it running for about a year running 11.04. Typically, I have VirtualBox running one virtual machine. This is mainly used for file sharing (PS3 Media server), Playon (on the virtual machine) and I have started using MythTV a few weeks ago.

In the last few days the system has become unstable. It locks up hard to the point that it does not accept any keyboard input and the server does not respond to pings. The caps lock and I think scroll lock lights are flashing on the keyboard and it takes a hard power cycle to restart the system. At that point it will run for some amount of time and locks up again.

Last night I upgraded to 12.04. Sometime during the night it locked up like this again. I reset it this morning. It just happened again and there is no message on the screen, just locks up hard.

I need some guidance on trying to determine what is causing the lock ups.

Thanks,

Shawn

---

### Post by beboylips on 2012-07-29
Hi.

Try checking for bad memory. Use memtest86. Ubuntu installs it by default and it can selected from the GRUB menu (hold Shift right after POST) but since your installation is corrupted try using memtest86 bootable cd (on their website) or re-install Ubuntu and run it from the GRUB screen.

-Beboy

---

### Post by Shawn67 on 2012-07-29
Thanks, I'm running MemTest+86 v4.20 now and have had some errors. I took one chip out and am retesting to see which chip is bad.

I can't use the GRUB menu on my system. Whatever video mode it is in my Dell LCD monitor can't display it and neither can my flatscreen if I plug into it. 

Thanks,

Shawn

---

### Post by TheFu on 2012-07-29
I had the same issue with virtualbox on a 10.04 server.  Most of the VMs are not desktops, they are servers, so I switched to KVM or XEN hypervisors and see huge uptimes running 5-10 VMs (DomUs). I haven't had a crash under either Xen or KVM in over a year.

The key for stability of virtual machine hosts, i.e. Dom0s, is not to use any GUI or X/Windows running directly on the host machine. Always connect from a different box on the network to manage the VMs.  The virt-manager in 12.04 handles this nicely, much better than under 10.04.

I realize this isn't the desired answer and if you are using desktop virtualization, then VirtualBox is probably the best solution you have.

Did you look at the virtualbox log files?  Anything interesting inside?

Did you search the virtualbox.org website for solutions or report the issue there?

Does the virtualbox.org website have a troubleshooting guide?

Can you migrate to a new, better supported OS for the host and clients? 11.04 is not the pretty, new, OS around here.

---

### Post by davetv on 2012-07-29
ANY error in memtest is bad for system stability. It might not be a bad ram chip though, just a seating problem.

I spray some CRC 5-56 (many equivalent products out there) onto a rag, wipe the rag against the pads on the chip, and re-seat the ram chip a few times (cleaning the socket as well) when I get this problem. Repeat procedure for all ram chips installed.

It is a common problem and it fixes it generally.

---

