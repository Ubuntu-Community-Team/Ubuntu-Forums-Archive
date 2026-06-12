---
title: "32 bit Ubuntu on 64 bit architecture (Installing Java)"
date: 2011-02-01
forum: General Help
---

### Post by Zalokin on 2011-02-01
Hi all,

I'm new to Ubuntu and I have a problem with  OpenJDK Java 6 Web Start and  OpenJDK Java 6 Runtime through Add/Remove facility.

The error msg in the Add/Remove facility is as follows: -

OpenJDK Java 6 Runtime cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.


My version of Ubuntu is 8.10 32-bit.

My laptop is Acer Extensa 5220

Processor architecture is 64-bit.

Full details are as follows: - 

[LIST]
[*] **Processor:** Intel® Celeron™ M processor 530SR (1.73GHz, 1MB cache, 533MHz FSB) supporting Intel® 64-bit architecture.
[/LIST]
As you may be able to realise is that I am trying to install 32-bit Java in a 64-bit machine.

First of all, is this possible?

Should I have to upgrade to 64-bit version of Ubuntu in order to run Java for 64-bit architecture?

Would I experience other problems by using 32 bit software/drivers on a 64-bit machine?

I wouldn't mind having to upgrade to 64-bit Ubuntu, but I just would like to avoid issues with 64 bit versions of Ubuntu for eg WIFI drivers, other drivers, software etc.

Thanks!

Zal

---

### Post by runeh76 on 2011-02-01
Hi

Nothing to do with ur processor! 32b ubuntu run under 64b processor.
Are u sure u are trying to install 32b java. Im not sure, does they support to 8.10 anymore...guess not.

Terminal
(change ur distro to first line link 'deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) **maverick** partner')
```
sudo add-apt-repository 'deb http://archive.canonical.com/ubuntu maverick partner'
sudo apt-get update 
sudo apt-get install sun-java6-plugin
sudo apt-get remove icedtea6-plugin openjdk-6-jre
```

---

### Post by runeh76 on 2011-02-01
Wikipedia:

Ubuntu 8.10 (Intrepid Ibex), released on 30 October 2008,[60][61] was Canonical's ninth release of Ubuntu. **_Support ended on 30 April 2010._**[62] Ubuntu 8.10 introduced several new features including improvements to mobile computing and desktop scalability, increased flexibility for Internet connectivity, an Ubuntu Live USB creator and a guest account,[63] which allowed others to use a computer allowing very limited user rights (e.g. accessing the Internet, using software and checking e-mail).[64] The guest account had its own home folder and nothing done on it was stored permanently on the computer's hard disk.[65] Intrepid Ibex also included an encrypted private directory for users,[66] the inclusion of Dynamic Kernel Module Support, a tool that allows kernel drivers to be automatically rebuilt when new kernels are released and support for creating USB flash drive images.[15][67]

---

### Post by oldos2er on 2011-02-01
> **Zalokin said:**
> My version of Ubuntu is 8.10 32-bit.


You might want to install 10.04 or 10.10, since 8.10's repositories are offline. Or try [http://atlanticlinux.ie/blog/?p=143](http://atlanticlinux.ie/blog/?p=143)

---

### Post by Zalokin on 2011-02-03
Thanks.

Zalokin

---

