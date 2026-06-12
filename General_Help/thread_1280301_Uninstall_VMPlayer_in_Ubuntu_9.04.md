---
title: "Uninstall VMPlayer in Ubuntu 9.04"
date: 2009-10-01
forum: General Help
---

### Post by Steve00 on 2009-10-01
I installed VMware-Player-2.5.3-185404.i386.bundle on 9.04 and have since moved on to Virtualbox. However, despite searching in the forums, I've yet figured out how to uninstall VMPlayer. It is not in add/remove or synaptic package manager. I tried the steps mentioned at [https://help.ubuntu.com/community/VMware/Player]("https://help.ubuntu.com/community/VMware/Player"), changing the file names to reflect the 2.5.3 version. Nothing happened. 

How do I get totally rid of VMPlayer?

Thanks!

--Steve

---

### Post by vishy1618 on 2009-10-01
If I recall correctly, the VMware executables are capitalized (VMware), so try typing VM into a terminal and then tapping TAB twice. It should give you a list of all VMware commands. On of them ought to be an uninstallation command. Use that with a sudo prefix to get rid of VMware.

If this does not work, try typing 

apropos unin

into the terminal. Maybe it will find the command. Also, I think VMware stores its files in /usr/lib/vmware or something. If you get a bin/ directory in it, then you can see the executables in it.

Good luck!

---

### Post by Steve00 on 2009-10-02
> **vishy1618 said:**
>  ... If you get a bin/ directory in it, then you can see the executables in it.

Good luck!

That did it! I was able to find the uninstall executable and it took care of the problem. It wouldn't run from the default prompt when I first fired up Terminal, I had to cd to the bin/ directory and run the uninstaller from there. Thanks for your help!

--Steve

---

