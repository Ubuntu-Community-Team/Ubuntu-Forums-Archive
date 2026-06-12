---
title: "version"
date: 2011-11-18
forum: General Help
---

### Post by disabled_biscarri on 2011-11-18
hello everybody,
I'm a new linux user, excuse me for such a trivial question...
I have installed ubuntu 10.04, from caelinux2010 distro
how to ask the system what kind of linux platform it is?
debian, mandriva, red hat,...?
I want to install an application and don't know which version to download?
thank you for your comments
lluis

---

### Post by IanW on 2011-11-18
Ubuntu is based on Debian.

---

### Post by BillyBoa on 2011-11-18
It's Debian derived.

---

### Post by Elfy on 2011-11-18
debian based

You might find that the app is already in the repositories

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by the_blue_box on 2011-11-18
Well if you've installed ubuntu 10.04 then the linux platform **IS** ubuntu 10.04

---

### Post by snowpine on 2011-11-18
What is the application?

---

### Post by grahammechanical on 2011-11-18
Yes, but what is caelinux based on? In fact what is caelinx?

[http://caelinux.com/CMS/index.php?option=com_content&task=view&id=49&Itemid=40]("http://caelinux.com/CMS/index.php?option=com_content&task=view&id=49&Itemid=40")

It is based on Ubuntu 10.04 LTS! So, the package would be a deb. Oh, by the way, the 2011 version is out.

Regards.

---

### Post by disabled_biscarri on 2011-11-18
I appreciate all your comments

I want to install Salome 6.3.1 but I find 7 different versions to download at salome-platform.org, 3 of them for debian:

- debian Etch
- debian lenny
- debian squeeze

I want to know which command in a linux shell tells me which one is my ubuntu linux (which is version 10.04 and comes from caelinux 2010 distro)

or maybe I can find this info through the ubuntu GUI

---

### Post by snowpine on 2011-11-18
I haven't used Salome personally, as far as I know it is not offered by the official Ubuntu repositories.

A little further down their Download page I see this:

> Universal binaries for Linux:

    * Download a version for 32bit Linux (617Mb, md5sum)
    * Download a version for 64bit Linux (622Mb, md5sum)

This runtime packages do not need any installation. Just extract the archive and execute runSalome script. This packaging includes Debian Etch (64bit / 32bit) layer, all the pre-requisites and SALOME 6.3.1 binaries. It is known to work on Linux distributions like Ubuntu, Suse, RHEL, etc ...

---

### Post by disabled_biscarri on 2011-11-18
thank you, snowpine, that helps

but, anyway, I still would like to know which kind of debian ubuntu I have in my computer

---

### Post by snowpine on 2011-11-18
> **biscarri said:**
> thank you, snowpine, that helps

but, anyway, I still would like to know which kind of debian ubuntu I have in my computer

You're welcome!

Your "kind of debian ubuntu" is "Ubuntu 10.04" and you should be very cautious installing software that is designed for a different release of Ubuntu or Debian.

---

### Post by disabled_biscarri on 2011-11-19
OK, I think I'm on the way to understand the map of all this stuff...

1) I can download from salome-platform.org the salome runtime package, version for 64bit Linux (622Mb, md5sum) and run it in my ubuntu workstation without need for installation

2) I was thinking that one of the following binaries (found at salome-platform.org/downloads) could be installed in my ubuntu 10.04

[INDENT]Binaries for officially supported Linux platforms (Installation Wizard):
Download a complete version for Debian 4.0 Etch 32bit (1,46Gb, md5sum) or Debian Etch 4.0 64bit (1,5Gb, md5sum)
Download a complete version for Debian 5.0 Lenny 64bit (1,45Gb, md5sum)
Download a complete version for Debian 6.0 Squeeze 64bit (1,45Gb, md5sum)
Download a complete version for Mandriva 2008 32bit (1,47Gb, md5sum) or Mandriva 2008 64bit (1,46Gb, md5sum)
Download a complete version for Mandriva 2010 32bit (1,44Gb, md5sum) or Mandriva 2010 64bit (1,44Gb, md5sum)
Download a complete version for Red Hat Enterprise 4 64bit (1,48Gb, md5sum)
Download a complete version for Scientific Linux 5.1 64bit (1,47Gb, md5sum)
[/INDENT]

...then, do you think none of those binaries will work OK with my ubuntu 10.04?

in terms of performance (salome is CPU and Graphics intensive), is a runtime package as good as having the app installed?

thanks a lot  :)

---

### Post by snowpine on 2011-11-19
> **biscarri said:**
> 2) I was thinking that one of the following binaries (found at salome-platform.org/downloads) could be installed in my ubuntu 10.04

[INDENT]Binaries for officially supported Linux platforms (Installation Wizard):
Download a complete version for Debian 4.0 Etch 32bit (1,46Gb, md5sum) or Debian Etch 4.0 64bit (1,5Gb, md5sum)
Download a complete version for Debian 5.0 Lenny 64bit (1,45Gb, md5sum)
Download a complete version for Debian 6.0 Squeeze 64bit (1,45Gb, md5sum)
Download a complete version for Mandriva 2008 32bit (1,47Gb, md5sum) or Mandriva 2008 64bit (1,46Gb, md5sum)
Download a complete version for Mandriva 2010 32bit (1,44Gb, md5sum) or Mandriva 2010 64bit (1,44Gb, md5sum)
Download a complete version for Red Hat Enterprise 4 64bit (1,48Gb, md5sum)
Download a complete version for Scientific Linux 5.1 64bit (1,47Gb, md5sum)
[/INDENT]

I don't see Ubuntu 10.04 on that list, unfortunately.


> **biscarri said:**
> in terms of performance (salome is CPU and Graphics intensive), is a runtime package as good as having the app installed?

That would be a good question for Salome developers/users. Do they have a contact us link or user forum on their site? :)

---

### Post by disabled_biscarri on 2011-11-20
I had the erroneous idea that, since ubuntu is debian based, one ot those salome debain versions should work under ubuntu 10.04

I'll work with the runtime executable, and ask salome-platform forum about performances 

thak's again for helping to spread open-source knowledge  :)

---

### Post by snowpine on 2011-11-20
> **biscarri said:**
> I had the erroneous idea that, since ubuntu is debian based, one ot those salome debain versions should work under ubuntu 10.04

I'll work with the runtime executable, and ask salome-platform forum about performances 

thak's again for helping to spread open-source knowledge  :)

You're welcome!

You are correct that Ubuntu is based on Debian. Squeeze is the most similar release to Ubuntu 10.04. However, Ubuntu developers make just enough modifications that most users don't consider Ubuntu "binary compatible" with Debian in all instances. Certainly it would vary on a case-by-case basis depending on the application, so proceed at your own risk if you decide to go this route. :)

---

### Post by C.S.Cameron on 2011-11-22
CAELinux 2011 contains the latest release of the Salome_Meca 2011.2 package developed by EDF (64bit) integrated with  two versions of the finite element solver for non-linear mechanics Code-Aster STA11.0 (both 64bits) optimized either for OpenMP or MPI parallelism. Salome_Meca 2011.2 is now based on Salome  v6.3 CAD/Pre/Post GUI and allows to run a complete FEA study directly from the SALOME graphical user interface.

---

### Post by bluexrider on 2011-11-22
In the menu go to>System>About Ubuntu

---

### Post by C.S.Cameron on 2011-11-24
> **biscarri said:**
> I appreciate all your comments

I want to install Salome 6.3.1 but I find 7 different versions to download at salome-platform.org, 3 of them for debian:

- debian Etch
- debian lenny
- debian squeeze

I want to know which command in a linux shell tells me which one is my ubuntu linux (which is version 10.04 and comes from caelinux 2010 distro)

or maybe I can find this info through the ubuntu GUI

Correct me if I am wrong but I believe CAELinux comes with Salome 6.3 pre installed.

---

