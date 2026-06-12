---
title: "faster boot time desired"
date: 2012-10-13
forum: General Help
---

### Post by SuperFreak on 2012-10-13
I have an UEFI Bios and a working bootable system. My boot time is about 45 seconds which seeems slow to me as I use an SSD for my OS. Is there a way of speeding up boot time?

---

### Post by 2F4U on 2012-10-14
Which I/O scheduler are you using for the SSD? The default on Ubuntu would be CFQ, but for a SSD DEADLINE or NOOP seem to result in better performance.

[http://ubuntuforums.org/showthread.php?t=1464706](http://ubuntuforums.org/showthread.php?t=1464706)

Besides that, boot times also depend on what desktop environment you are using and what daemons/applications are automatically started.

---

### Post by TenPlus1 on 2012-10-14
To show all of the startup applications go into Terminal and type the following 2 commands:

cd /etc/xdg/autostart/
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop

Now run Startup Apps and untick the one's you dont really need.  Be sure you know what each one does beforehand...

Also, adding the noatime option and discard option in fstab for ext4 partitions will improve boot time also for your SSD drive...

---

### Post by hal8000 on 2012-10-14
Something is wrong there. I have Ubuntu 64bit on a SATA II drive and mine boots in 36 seconds. I have not tuned it yet.

Install bootchart from synaptic or Boot squence Auditing (in software centre). Next reboot will create a bootchart in /var/log/bootchart

Pybootchartgui is supposed to display bootchart but it looks for a bootchart in /var/log and the actual path is /var/log/bootchart  which can be viewed with nautilus to show what slows your system down.

---

### Post by SuperFreak on 2012-10-14
> cd /etc/xdg/autostart/
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop

Now run Startup Apps and untick the one's you dont really need. Be sure you know what each one does beforehand...


That actually shaved off 10-15 seconds on Boot time thank you. I am going to have to google what some of the remaining Startup apps do to determine if I need them

> Which I/O scheduler are you using for the SSD? The default on Ubuntu would be CFQ, but for a SSD DEADLINE or NOOP seem to result in better performance.

I have CFQ enabled.If I read this correctly it will help SSDs but what will happen when using both SSD and mechanical HDs . My SSD is the OS disk. I do have Noatime and Discard enabled on the SSD through FSTAB

---

