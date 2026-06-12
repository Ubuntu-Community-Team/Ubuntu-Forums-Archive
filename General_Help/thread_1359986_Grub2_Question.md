---
title: "Grub2 Question"
date: 2009-12-20
forum: General Help
---

### Post by Vince N on 2009-12-20
Hey Folks,

So far I'm loving Ubuntu 9.10.  By biggest gripe with it is the overheating issues with my laptop, an Acer Aspire 5315, which is caused by [this bug.]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337")

I've been using the workaround for the kernel described in the bug report which resolved the issue and the -15 kernel seemed to be unaffected at all but the bug reappeared after upgrading to the -16 Kernel.

So my question is with the new Grub2 how do I configure it to boot from a specific kernel every time?  I knew how to do this under legacy grub but apparently the menu.lst trick is no longer effective.

---

### Post by drs305 on 2009-12-20
Learn about Grub 2 from the Ubuntu community doc:
[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

You can designate a specific kernel to boot or use the "saved" option, which will store the one you last booted. It's an improvement over Grub's "saved" which simply stored the "DEFAULT=" number. G2 stores the actual string value of the "saved" kernel.

The "G2-Tasks" in my signature line also discusses how to set the default OS/kernel.

And if you are really, really anal, you can create the specific menuentry in /etc/grub.d/40_custom and then rename it 06_custom. Make it executable, update grub with "sudo update-grub" and it will always be the first entry in your menu and will never change unless you manually make changes to it.

---

### Post by oldfred on 2009-12-20
You can select which number entry to boot from:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
see #5

You could add a copy to 40_custom and make it 09_custom with your own entry. It will then be the first entry after you update-grub

Or you could do this with any entry, my example is for windows but the entry just has to exactly match the text of any bootable line:

If you refer to Windows by its number, you will have to edit on every update. But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)". Then you can use in /etc/default/grub, and you won't have to edit Grub after kernel updates.
to copy entry from:
gedit /boot/grub/grub.cfg
To paste entry into ( I have to have both windows open for the copy/paste to work):
gksudo gedit /etc/default/grub
Change GRUB_DEFAULT=0 to your windows entry like this as example
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"

update-grub

---

### Post by Vince N on 2009-12-21
Thanks for the info guys.  Really helpful :-D

---

