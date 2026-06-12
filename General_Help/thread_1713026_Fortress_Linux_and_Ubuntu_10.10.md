---
title: "Fortress Linux and Ubuntu 10.10"
date: 2011-03-23
forum: General Help
---

### Post by dgriggs on 2011-03-23
Has anyone tried to install Fortress Linux OVER an existing Ubuntu 10.10? Would I have to install as a dual boot? What is this Palatinux, from what I understand this is what runs Fortress. Is there a way to get the security aspects from this Palatinux and use it on Ubuntu? I was reading about Fortress and was intrigued. Please, any info is greatly appreciated.

---

### Post by mr_y82 on 2011-06-27
I am also curious about Palatinux... I'm a windows wizard just beginning to learn about linux, esp. how to ramp up my security a bit.

---

### Post by Dangertux on 2011-06-27
Palatinux is basically a pre-hardened distro. Meaning they integrate several different hardening methods into the kernel as well they add a few applications. IDS , advanced iptables configuration utility and several other security centric applications. 

As far as installing it over Ubuntu I am not really sure that would work as both distros use highly modified kernels. However there are measures you can take to make a ubuntu system as secure if not more secure. 

Some examples include using apparmor/selinux, hardening your kernel both through configuration files and downloading a secure kernel, adding IDS, creating spi firewalls using iptables , installing a third party dpi firewall solution, and many others. I won't get into too many details because I am only phone , I will post more info when I am at a computer.

---

### Post by palatinux on 2011-07-12
Fortress Linux cannot be ported to Ubuntu. A dual-boot is required. The reasons are:

* Ubuntu software is not compiled with a hardened toolchain (Stack Smashing Protector, Position Independent Executables, Read-Only Relocation Tables, Binding Policy Now etc.) but Fortress Linux is.

* Running Fortress Linux software in Ubuntu will cause the Fortress Linux software to kill  misbehaving Ubuntu software with too many child processes, illegal memory actions, accessing off-limit system resources etc.

* Ubuntu software has included support for everything but the kitchen sink. This means that Ubuntu software supports bindings with with unused applications or deprecated kernel functions which can be (easily) exploited. Fortress Linux does not support this and so the Ubuntu software may not work at all.

* Ubuntu does not have a tight security policy by default and even if you're system is protected by SE-Linux; Only a Linux guru can write decent SE-Linux policies and even they make mistakes. One little mistake and your system can be owned. SE-Linux is not supported by FL since it provides less security when compared to GrSecurity and PAX.

I guess you rather use the better Fortress Linux' self-learning hardening function then spending four weeks writing policies, tweaking and locking yourself out of your system to achieve the same.

Most DDOS and hacker attacks we face daily are coming from hacked Debian and Ubuntu servers. Still,  Ubuntu is a nice OS for the mainstream market.


ps. Board admin, please don't spin my post again by editing it. We are just helping users on your board.

---

