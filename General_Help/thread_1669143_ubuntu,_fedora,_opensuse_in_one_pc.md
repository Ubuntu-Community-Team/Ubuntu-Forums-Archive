---
title: "ubuntu, fedora, opensuse in one pc"
date: 2011-01-17
forum: General Help
---

### Post by salman qamar on 2011-01-17
i am currently using opensuse11.3 in my pc , but i am not happy with it, i want to try ubuntu, fedora.
my hard is 120gb, 1.66C2D processor, and 2gb ram.
how i can install all these on my pc (not using via virtual Box).
if i have to remove my currently installed OS,then which to install first?
and also how many partitions required to do so?
and which OS should be installed first?

---

### Post by wojox on 2011-01-17
Ideally you would want four partitions. openSUSE, Fedora, Ubuntu, and Swap.

Download and burn Fedora and Ubuntu.

Boot Ubuntu and "Try without installing".

Then you will need to open G-Parted from System > Admin and slice up your drive.

Start by shrinking openSUSE to about 30GB.

Then close out G-Parted and install Ubuntu. When you get to the partitioner choose "manual". Create a Primary partition as / and ext4 (60GB). Then another for swap (2GB). 

Finish installing and let Ubunntu install Grub2 to your MBR.

When that's done install Fedora. Choose the remaining free space as you partition for it. Do not install Grub. Uncheck the option.

After your done installing Fedora, reboot and and load Ubuntu and run "sudo update-grub2". You should see Fedora show up.

Reboot again and finish your Fedora install.

If you have any problems during the installs, open firefox and post back. Good luck. ;)

---

### Post by garvinrick4 on 2011-01-17
wojox hit nail on head: The reason he is doing that is fedora and openSuse use grub-legacy and Ubuntu grub2. They do not work together well at all and you will
be using grub2 from ubuntu as your grub choice. wojox will have you up and running
in no time.

---

