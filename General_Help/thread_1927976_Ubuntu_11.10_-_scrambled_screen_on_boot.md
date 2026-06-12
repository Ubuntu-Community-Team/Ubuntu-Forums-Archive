---
title: "Ubuntu 11.10 - scrambled screen on boot"
date: 2012-02-19
forum: General Help
---

### Post by Dusan2 on 2012-02-19
Greetings,

I have an issue with Ubuntu 11.10. I have dual OSes installed - 64bit Ubuntu and 64bit Win7Ultimate. (Ubuntu was installed second). Windows works flawlessly, but Ubuntu fails to boot - showing me a scrambled screen (mostly orange and yellow hues) and after a few seconds the monitor loses the signal (as if the cord was pulled).

I installed Ubuntu 11.04 first, about three months ago. It worked quite well, but VLC Player playing any video at 15FPS max and Firefox was scrolling slowly. After checking the forums, I understood the problem was with my video cars. (Oh yes, the config: AMD Athlon II x3 455, MSI 870-C45, AMD Radeon HD 6790). Since the regular, graphical update "Additional Drivers" failed, I found a forum post explaining how to remove the Linux open source drivers and install the AMD ones. Then, I restarted my PC before I finished all the steps in that process (misread). After that, I got the scrambled screen when I tried to boot Ubuntu.

No problems, I thought - just wipe the disk and install the new Ubuntu (11.10 came out in the meantime). I format the Ubuntu partition in Win7's disk management, boot with Win7 CD to remove GRUB (I couldn't log to Win7 after wiping the partition), put on the Ubuntu 11.10 CD, format partitions (/boot, 100 MB and /install, 10GB), install. After the install, only Win7 boots. Use EasyBCD to add GRUB - now I can boot both Win7 and Ubuntu, like before. Only, Ubuntu still fails to move past the scrambled screen.

Then, I attempted fixing that problem. Most forums agree the issue is with the GPU drivers, and seeing how my problem was created I agreed that was it. I needed to access the terminal and use commands found here - [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver) (fully remove). The only way I could get to the terminal was over the LiveCD with nomodeset enabled, try Ubuntu option. (Ubuntu recovery didn't work (except for the 4th option, text, where I was unable to execute the commands), Ubuntu with nomodeset didn't work, Ubuntu LIVECD w/o nomodeset didn't work.) Anyways, I ran the options in the text mode with the try Ubuntu livecd with nomodeset on, but they didn't have an effect - everything is still the same. I don't know if I should mount the partition where Linux is installed on the LiveCD w/o modeset try Ubuntu options, and I don't know how to do it.

Would you guys have any ideas?

---

### Post by oldfred on 2012-02-20
Instead of nomodeset have you tried other settings. Some generic also works.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

If you can get to terminal command line you should be able to run updates. If not chroot run with sudo, # is comment, do not copy comments:

#Commands once in chroot:
#if not chroot use: 
sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

---

### Post by Dusan2 on 2012-02-20
Thanks, your terminal commands worked on the recovery + shift - it boots with no issues now. :)

---

