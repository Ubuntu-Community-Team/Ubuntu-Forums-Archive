---
title: "Grub prompt after upgrade to Ubuntu 11.04"
date: 2011-07-19
forum: General Help
---

### Post by groston on 2011-07-19
I am a casual user of Ubuntu, which is installed in a vmware virtual machine. After upgrading to Ubuntu 11.04, and after the reboot, it just booted up to a grub prompt. 

I found a useful post about resolving this problem here: [http://aaron-kelley.net/blog/2011/04/grub-prompt-after-upgrade-to-ubuntu-11-04/](http://aaron-kelley.net/blog/2011/04/grub-prompt-after-upgrade-to-ubuntu-11-04/)

The sequence of grub shell commands to be entered are these:

[INDENT]set root=(hdX,Y)
linux /vmlinuz root=/dev/sdZ ro
initrd /initrd.img
boot[/INDENT]

where the X, Y, and Z are replaced with appropriate letters/numbers.

The problem that I am having is that TAB is not completing the commands at the grub shell, thus I have no idea what the letters/numbers to use. 

My installation is completely generic - I have not customized it in any way. Can someone please check their vmware/Ubuntu system and let me know what letters/numbers to use.

Thank you.

---

### Post by groston on 2011-07-20
The answer was the lowly ls command. This showed the hard drives and I was able to move forward from there.

---

