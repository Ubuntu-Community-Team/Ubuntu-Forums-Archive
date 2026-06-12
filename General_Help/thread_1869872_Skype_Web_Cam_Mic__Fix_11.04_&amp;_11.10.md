---
title: "Skype Web Cam Mic  Fix 11.04 &amp; 11.10"
date: 2011-10-26
forum: General Help
---

### Post by Bobhuber on 2011-10-26
After reading many posts on the problems with the USB webcam microphone with Skype and other Apps I found one that worked for me in both 11.04  and 11.10. I installed the 2.6.38 Kernel (June 4 2011) final rev.
The .deb packages can be found here > [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
Download and install all three .deb files for your architecture and select the Kernel from your Grub Menu on boot. These packages are listed as the final Kernel release for Natty but seem to work fine in Onieric for those of you not familiar with Kernel releases.  Here is a good tutorial on installing a Kernel upgrade (or fallback) . Note : Heed the warnings if you are using Nvidia proprietary driver that YOU installed. If you are using xorg-edgers or packaged Nvidia drivers you wont have to do anything before installing the Kernel upgrade (11.04)  or fallback (11.10)
Cheers

---

### Post by Zeak on 2011-10-28
bobhuber. I installed the 2.6.38 Kernel (June 4 2011) final rev.  That fixed the Microsoft problem with my Logitech Webcam Pro 9000.  Can that kernel be selected as default in the boot menu?  Is it possible to remove the unused kernels?  Thanks, Zeak

---

### Post by Bobhuber on 2011-10-28
> **Zeak said:**
> bobhuber. I installed the 2.6.38 Kernel (June 4 2011) final rev.  That fixed the Microsoft problem with my Logitech Webcam Pro 9000.  Can that kernel be selected as default in the boot menu?  Is it possible to remove the unused kernels?  Thanks, Zeak
Yes
The easiest way > Install synaptic packager if you haven't already .

Mark the old (in your case newer 3.0) Kernel files for removal. Make sure you get all three.
Now find the three you just installed 2.6.38 ,  highlight them one at a time and go to the package selection in the top menu bar and put a checkmark by Lock Version. Do this for all three files. This will prevent the system from updating the Kernel in the future.
Sudo update-grub > You should only see one Kernel revision mentioned on the update. 
Reboot

---

### Post by Zeak on 2011-10-29
Great help, I can use Skype again and maybe I have learned a little about Linux in the process.

---

