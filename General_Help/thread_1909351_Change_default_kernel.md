---
title: "Change default kernel"
date: 2012-01-15
forum: General Help
---

### Post by TheNEScollector on 2012-01-15
When I power my computer on and GRUB loads up, I am prompted with a few options:

Ubuntu 11.04 with a broken kernel
Ubuntu 11.04 with a broken kernel (Recovery Mode)
Previous Linux Versions
Memory Test
Memory Test
Windows XP

Obviously, those aren't the exact words it uses, but you get the idea. Because my default kernel is broken. When I turn on my computer, I need to select "Previous Linux Versions". Then, a new screen appears where I can see all of my old kernels. I then have to select kernel 2.6.38-13. This is a really big pain to do every time I boot my computer. How can I change the default kernel to boot to be 2.6.38-13? I know you can change the default OS in /etc/defults/grub, but this doesn't help me because I first need to select "Previous Linux Versions" to be able to boot the older kernel. Please help! Thanks!

---

### Post by dino99 on 2012-01-15
Each time a new kernel is available, it is installed but the older ones are not removed (that why you can find them as "previous kernel" into grub menu.
So if you want to be secured and always have a cleaned install, then you have to make some maintenance via synaptic:

sudo apt-get install synaptic
sudo synaptic
- search for your broken kernel
- purge it (image + 2 headers)

Its a good idea to have, at least, 2 kernels choice to boot on in case one is broken (often due to graphic driver conflict. That said, always install the driver from archive for better usability if you cant solve yourself issues). So with synaptic: purge the kernel(s) you dont need, then close synaptic and finally:

sudo update-grub
sudo reboot

then:
sudo synaptic
and update the repo (via synaptic menu icon) and reinstall the latest kernel (image + 2 headers), note that dkms have to be installed first.

---

### Post by odonnell on 2012-05-05
I have a similar problem, but I want to run the 3.2.0-23-lowlatency kernel, while there is a 3.2.0-24-generic, which works fine. It seems foolish to remove 3.2.0-24-generic as a backup version, just to get 3.2.0-23-lowlatency to the top of the menu.

I tried editing the default in /etc/default/grub. Neither the item number, nor the title (found in /boot/grub/grub.cfg) seemed to work, presumably because of the submenu of Previous Versions.

I haven't tried using the "saved" default. I am remembering to invoke the Grub menu and select the kernel.

I hope that the Grub configuration will improve significantly. If someone knows a good approach, please clue me in. I can edit /boot/grub/grub.cfg, but then everything will break on the next relevant package install.

---

### Post by mansonfan78 on 2012-05-05
You could also try installing Grub Customizer from the repos and see if it can help you out.

---

### Post by odonnell on 2012-05-05
I am still too timid to try the general-purpose Grub configuration interface. I found that I could make Grub make each kernel that I select from the menu default for the next boot. This isn't my favorite behavior, but it's better than using the menu for each boot.

Edit /etc/default/grub, replacing the single line:

GRUB_DEFAULT=0

with the 2 lines:

GRUB_DEFAULT="saved"
GRUB_SAVEDEFAULT="true"

Then execute "sudo update-grub"

It's interesting to look at /boot/grub/grub.cfg before and after to see what happened.

So far, I have not found a way to set the GRUB_DEFAULT variable to select a kernel from a submenu (which is where the desired kernel usually appears). I tried numerical entry based on Grub's sorting of the kernels, and the name of the entry cut and pasted from /boot/grub/grub.cfg. It looks as though the value of saved_entry and/or ${chosen} in grub.cfg could provide a string that would accomplish this, but I haven't figured it out yet.

---

### Post by odonnell on 2012-05-05
I strongly recommend an audit trail of every edited system configuration file. If you don't know your own favorite way, do this:

install the rcs package

cd /etc/default
sudo mkdir RCS
sudo ci -l grub

now edit the grub file

sudo ci -l grub

RCS (in the "ci -l" command) will insist on a comment, but for this purpose the comment is not nearly as important as the audit trail, and you may just type "." or "CTL-D" for an empty comment.

Side benefit of RCS: when I update a system, I can find my customizations easily by searching for RCS directories.

---

