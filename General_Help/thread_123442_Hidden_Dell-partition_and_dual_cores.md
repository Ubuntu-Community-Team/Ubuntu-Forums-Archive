---
title: "Hidden Dell-partition and dual cores"
date: 2006-01-30
forum: General Help
---

### Post by kaffelars on 2006-01-30
Hi,
I just ordered a Dell Dimension 9150, and as far as I can find out on various foums, Dell ship their computer with a hidden recovery partition on the hard drive. Will it be hard to install Ubuntu aside Windoze without damaging that  hidden partition? 
I forgot to mention to Dell that I wanted a Windoze-CD, so I guess I'm stuck with the recovery stuff, at least until they reply me on whether they will send me a CD or not..

I also see that people on the Ubuntu forum prefer the 32 bit version of Ubuntu. Is it possibe to utilze both cores on a Pentium D 920 with some version of the SMP-kernels in the 32 bit version..?

---

### Post by steve.horsley on 2006-01-30
No problem. You will probably find that the dell partition is /dev/hda1(vfat), and Windoze is /dev/hda2(NTFS). You will be wanting to shrink hda2 and then tell the installer to use the unused space onthe disk. I used partition magic to shrink the NTFS, but the installer probably has the ability too.

The installer will by default install a single-processor kernel. You then have to use synaptic or apt-get to install the kernel you really want - 386, 686, athlon, SMP etc. Use synaptic and search for "linux".

---

