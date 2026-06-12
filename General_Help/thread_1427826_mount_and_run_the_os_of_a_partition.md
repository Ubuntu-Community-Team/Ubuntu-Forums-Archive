---
title: "mount and run the os of a partition?"
date: 2010-03-12
forum: General Help
---

### Post by cgb223 on 2010-03-12
is there a way to mount another partition on any OS really, and then in a window in the current os, boot and run that partition?

for example, im in Ubuntu and i mount my seperate arch-linux partition. then via some magical software, boot it and run it in a window, so now i am in ubuntu checking my email, and simultaneously in archlinux on facebook in a commandline using links or something.

does it exist?

---

### Post by jocko on 2010-03-12
You can do that with a virtualization software, such as virtualbox or vmware.
They let you install operating systems in virtual machines that you can run from within another operating system. It is possible to make a virtual machine that uses a real partition instead of a virtual one to boot into an os that is already installed on the real machine.
One drawback is that since the virtual machine only see virtual hardware instead of the real hardware of your computer, you will probably get problems with hardware drivers that you need when you boot the os from the real machine, while the virtual machine will need completely different ones (at least this will be a problem if you have proprietary graphics drivers or by some other reason have a static xorg configuration).

See the [virtualization section]("http://ubuntuforums.org/forumdisplay.php?f=308") of the forums for more info and help on how to accomplish this.

---

