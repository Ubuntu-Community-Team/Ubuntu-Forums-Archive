---
title: "PPAs not updating?"
date: 2010-07-18
forum: General Help
---

### Post by tmette on 2010-07-18
So I added the Ubuntu PPA for VDPAU to get it installed on Kubuntu.  Does this not work since it's Kubuntu?  I noticed that it does say "ubuntu" in the PPA instaed of "kubuntu".  Is this something that needs changing?

I thought the software repositories worked the same way in Kubuntu that they do in Ubuntu?

---

### Post by jocko on 2010-07-18
> **tmette said:**
> So I added the Ubuntu PPA for VDPAU to get it installed on Kubuntu.  Does this not work since it's Kubuntu?  I noticed that it does say "ubuntu" in the PPA instaed of "kubuntu".  Is this something that needs changing?

I thought the software repositories worked the same way in Kubuntu that they do in Ubuntu?
Nothing needs changing. "ubuntu" in this case refers to the fact that the repo is for ubuntu (as opposed to debian or any other distro), and does not in any way refer to gnome/kde/xfce/ etc, just like the "ubuntu" in the address for the normal repositories ([http://archive.ubuntu.com/[COLOR=Blue]ubuntu[/COLOR]]("http://archive.ubuntu.com/ubuntu"))

---

### Post by tmette on 2010-07-18
> **jocko said:**
> Nothing needs changing. "ubuntu" in this case refers to the fact that the repo is for ubuntu (as opposed to debian or any other distro), and does not in any way refer to gnome/kde/xfce/ etc, just like the "ubuntu" in the address for the normal repositories ([http://archive.ubuntu.com/[COLOR=Blue]ubuntu[/COLOR]]("http://archive.ubuntu.com/ubuntu"))

Hmm..then I wonder how come it's not installing anything from the nvidia vdpau repository?  I added it, did a "sudo apt-get update", then "sudo apt-get upgrade" and it doesn't find anything.  Any ideas?

I thought this PPA was supposed to install MPlayer and SMPlayer for VDPAU support?  I kind of need VDPAU for HD videos since I'm running Kubuntu on an Intel Atom processor.

---

### Post by jocko on 2010-07-18
> **tmette said:**
> I thought this PPA was supposed to install MPlayer and SMPlayer for VDPAU support?  I kind of need VDPAU for HD videos since I'm running Kubuntu on an Intel Atom processor.
mplayer in the standard repos already have vdpau support (which is working great on my nvidia card), so I don't see why you would need anything from the ppa for that (unless the newer version of libvdpau in the ppa solves some problem with the one in the standard repos).
Just install mplayer (and whatever gui you want with that) and libvdpau1:
```
sudo apt-get install mplayer smplayer libvdpau1
```
The fact that apt-get upgrade doesn't find anything to upgrade probably just means that none of your already installed packages have newer versions in the ppa.

---

### Post by tmette on 2010-07-18
> **jocko said:**
> mplayer in the standard repos already have vdpau support (which is working great on my nvidia card), so I don't see why you would need anything from the ppa for that (unless the newer version of libvdpau in the ppa solves some problem with the one in the standard repos).
Just install mplayer (and whatever gui you want with that) and libvdpau1:
```
sudo apt-get install mplayer smplayer libvdpau1
```
The fact that apt-get upgrade doesn't find anything to upgrade probably just means that none of your already installed packages have newer versions in the ppa.

Installing it now...thanks!

---

### Post by lkjoel on 2010-07-18
> **tmette said:**
> Hmm..then I wonder how come it's not installing anything from the nvidia vdpau repository?  I added it, did a "sudo apt-get update", then "sudo apt-get upgrade" and it doesn't find anything.  Any ideas?

I thought this PPA was supposed to install MPlayer and SMPlayer for VDPAU support?  I kind of need VDPAU for HD videos since I'm running Kubuntu on an Intel Atom processor.
Try:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

