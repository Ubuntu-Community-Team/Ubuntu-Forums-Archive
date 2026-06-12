---
title: "Ubuntu Server LAMP 6.06 in VMWare hangs after installation"
date: 2006-06-02
forum: General Help
---

### Post by rgl on 2006-06-02
Hi:

I installed Ubuntu 6.06 Server CD in a virtual machine in VMWare (WinXP Pro as the host OS) on my laptop using the LAMP install option.  I followed through the installation procedure, using LVM with default partition settings with ext3.  However, when the installation finished and attempted to reboot, the virtual machine hangs right after the line "Uncompressing Linux... Ok, booting the kernel."  

Other than the usual timezone, machine name settings, I did not change any other settings during the text-mode installation procedure.  I have Ubuntu 5.10 installed on another virtual machine session and it runs fine with it.

The machine settings are 3.8GB disk space and 256MB RAM, NAT network, default SCSI and IDE virtual hard disk/CD-ROM respectively.  For the type of OS, I used "Other Linux 2.6.x kernel".

Any ideas on how to fix this?

---

### Post by laplinux on 2006-06-02
Same problem with me. Successful Ubuntu Server LAMP 6.06 installation but it hangs right after the line "Uncompressing Linux... Ok, booting the kernel." on my laptop with dual-boot systems. 
I bet it's a bug.

---

### Post by jstueve on 2006-06-02
I'd imagine (not sure at all) that LVM partitions on virtual disks might be problematic.

---

### Post by rgl on 2006-06-02
I tried both with traditional partitions and LVM, the result is the same - hanging at on "Uncompressing Linux... Ok, booting the kernel."

---

### Post by nihilocrat on 2006-06-02
Just chiming in that I have an Ubuntu 5.10 VM which is working excellently.

I had problems installing CentOS 4 and had to roll back to 3. Supposedly it was a problem with VMWare being picky with which kernels it will cooperate with. I don't know its specific requirements, but not being able to use CentOS 4 was probably due to the kernel being too recent or some crap like that. This might be the same situation.

---

### Post by rgl on 2006-06-03
I decided to try Xubuntu, downloaded the alternative CD and installed it under VMWare.  That one boots up without any issues.

**There is definitely something wrong with Ubuntu Server CD running as a  VMWare virtual machine under WinXP.**

---

### Post by jammond on 2006-06-03
I solved it by booting from the CD again, selecting rescue mode, and apt-get installing linux-686. That kernel boots fine.

---

### Post by trojonus on 2006-06-22
[QUOTE=jammond]I solved it by booting from the CD again, selecting rescue mode, and apt-get installing linux-686. That kernel boots fine.[/QUOTE]

Can you explain in more detail how to do this. Recue mode offers different shell enviroments and i am unfamiliar with apt-get

Trojonus

---

### Post by legacyb4 on 2006-11-30
I was having trouble installing Server 6.06 in VMWare 1.01 (on physical host running Server 6.06, ironically) where the installer was hanging while "Retrieving file xx of xx".

[This thread](http://www.vmware.com/community/thread.jspa?messageID=440067) at vmware.com suggested turning off Acceleration during the installation which seemed to do the trick.

GX620, dual core 3GHz

---

