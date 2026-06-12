---
title: "apt-get upgrade - freeze installing udev (151-12.1)"
date: 2010-09-28
forum: General Help
---

### Post by JedMeister on 2010-09-28
This problem is occurring on a somewhat customised 10.04 Server ([TKL-Core-Lucid beta]("http://www.turnkeylinux.org/blog/core-lucid-beta")) installed from ISO under KVM ([ProxmoxVE]("http://pve.proxmox.com/")). I am accessing the VM via SHH from a Terminal on my Ubuntu 10.04 desktop.

As the title suggests apt-get upgrade froze on installing udev (151-12.1 - from my local mirror of the lucid-updates repo). FWIW its using 0% CPU according to the Proxmox VM web admin page. I waited, waited and waited some more... Eventually (after about 20 mins) I got sick of waiting and reset the VM (I know probably a bad idea right from the start). 

Anyway it sort of reboots ok. I'll explain, the VNC window (part of Proxmox which allows a remote console view of the VM via java in web browser) does not get to the command prompt, it freezes during the latter part of boot. But I can connect to the VM fine via SSH and it all seems to work ok.

But every time I try to use apt-get the system complains that: ```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
``` Running *dpkg --configure -a* (as root) just results in the freeze again (I have waited nearly an hour now and it definately doesn't appear to be doing anything).

Any ideas what I can do to work out whats going wrong? And ideally fix it? Worst case scenario I'll just reinstall and not upgrade udev (at least not to the lucid-updates version) but be nice to get to the bottom of this and either work out what is going on and lodge a bug with the relevant party.

---

### Post by linux-hack on 2010-09-28
try ```
sudo apt-get install -f
```

---

### Post by JedMeister on 2010-09-28
> **linux-hack said:**
> try ```
sudo apt-get install -f
```

Thanks for the reply linux-hack. Unfortunately that gives me a slightly different response but basically the same result.```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up udev (151-12.1) ...
```(followed by the same freeze).

Any other ideas? Even if I can just get it to stop trying to install udev?

---

### Post by JedMeister on 2010-09-28
I tried again with a clean VM but this time used official Ubuntu repo. Also I only installed udev (didn't do full upgrade). The install bit still took longer than I thought it should but it did complete. It threw up some errors though, but they seem to be non-fatal as the machine reboots fine. Here is the dialog:```
The following packages will be upgraded:
  udev
1 upgraded, 0 newly installed, 0 to remove and 56 not upgraded.
Need to get 408kB of archives.
After this operation, 4096B of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ lucid-updates/main udev 151-12.1 [408kB]
Fetched 408kB in 3s (104kB/s)
debconf: delaying package configuration, since apt-utils is not installed
(Reading database ... 21224 files and directories currently installed.)
Preparing to replace udev 151-12 (using .../udev_151-12.1_i386.deb) ...
Adding `local diversion of /sbin/udevadm to /sbin/udevadm.upgrade'
Unpacking replacement udev ...
Processing triggers for man-db ...
Setting up udev (151-12.1) ...
udev start/running, process 2628
Removing `local diversion of /sbin/udevadm to /sbin/udevadm.upgrade'
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic
.: 13: Can't open /scripts/casper-functions
.: 6: Can't open /scripts/casper-functions

```Do they look serious? Could my original issue be caused by a dodgey file on my local mirror? Also I'm guessing that its a TKL specific issue as Ubuntu don't have casper with server version (no live CD for Server).

---

### Post by JedMeister on 2010-09-30
I'm tempted to mark this solved as it actually doesn't seem to be causing me any problems now (since my last post) but as I haven't really done much more testing and I haven't had anyone knowledgeable come along to help explain the errors to me, I think its best to leave it 'unsolved' for now. 

Once I do a full upgrade (without it hanging again) and some more testing to confirm that it all continues to work ok then I'll be back to update this.

---

### Post by aplatypus on 2012-05-04
Hi JedMeister,

I logged on here to see how this discussion was going, and see if there's an answer yet.  I have noted the similar situation.

In looking at the dependencies -- **initramfs** fails due to an error with **casper**.  **Casper** also fails due to problem with the **initramfs** script.  They are breaking each other.

A look at the dependencies shows us that **udev** depends on **initramfs**.    

I seriously doubt that you **udev** can be updated it is probably sticking at the '*old*' version and aborting the upgrade due to the **casper** error with **initramfs** you have pasted above.

As I see it, I keep bumping against this same co-dependence.  I'd like it if I could just 'dump' **initramfs** and install it 'fresh'.  It looks like I also need to get casper going.

All these comments are referring to a Ubuntu turnkey appliance on VirtualBox freshly created and just looking at the initial security updates output.  If those initial updates embrace, then **udev** isn't every being updated.

A more important point here is that recover of this situation could be very messy on production or important machine.  Some improvements are requires to just plug-in a fix when package dependencies get out of wack like so.  Hope to see some suggestions (thanks in advance).

/ will

---

### Post by oldos2er on 2012-05-04
Old thread closed.

---

