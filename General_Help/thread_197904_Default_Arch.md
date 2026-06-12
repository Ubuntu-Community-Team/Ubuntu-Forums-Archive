---
title: "Default Arch"
date: 2006-06-16
forum: General Help
---

### Post by Koybe on 2006-06-16
Hi there,

I installed dapper... great... updated to k7 kernel... great...

Today dapper asked me for a kernel upgrade and want to install the 386 one. How can i set the default arch for my pc so it won't download this arch anymore but the good one?

---

### Post by Ramses de Norre on 2006-06-16
sudo aptitude purge linux-386

---

### Post by Koybe on 2006-06-16
[quote=Ramses de Norre]sudo aptitude purge linux-386[/quote] 
it was more something like linux-*386, but it worked. So i guess the new kernel for the current arch will be upgraded in fews days or this was only for 386 kernel?

The security annoucement tells it's out... but it's not found as an upgrade for apt

---

### Post by Ramses de Norre on 2006-06-16
You mean you don't get the k7 updates? I thought you got both.. What version is the k7 now?

---

### Post by Koybe on 2006-06-16
```
dpkg -l linux*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                             Version                          Description
+++-================================-================================-================================================================================
pn  linux-386                        <none>                           (no description available)
un  linux-doc-2.6.15                 <none>                           (no description available)
un  linux-image                      <none>                           (no description available)
un  linux-image-2.6                  <none>                           (no description available)
pn  linux-image-2.6.15-23-386        <none>                           (no description available)
ii  linux-image-2.6.15-23-k7         2.6.15-23.39                     Linux kernel image for version 2.6.15 on AMD K7 SMP/UP
pn  linux-image-386                  <none>                           (no description available)
un  linux-kernel-log-daemon          <none>                           (no description available)
pn  linux-restricted-modules-2.6.15- <none>                           (no description available)
ii  linux-restricted-modules-2.6.15- 2.6.15.11-1                      Non-free Linux 2.6.15 modules on AMD K7
pn  linux-restricted-modules-386     <none>                           (no description available)
ii  linux-restricted-modules-common  2.6.15.11-2                      Non-free Linux 2.6.15 modules helper script
ii  linux-sound-base                 1.0.10-4ubuntu4                  base package for ALSA and OSS sound systems
un  linux-source-2.6.15              <none>                           (no description available)

``` 
```
uname -a
Linux cormyr 2.6.15-23-k7 #1 SMP PREEMPT Tue May 23 14:20:54 UTC 2006 i686 GNU/Linux

``` 
> 
Ubuntu 6.06 LTS:
  linux-image-2.6.15-25-386                         2.6.15-25.43
  linux-image-2.6.15-25-686                         2.6.15-25.43
  linux-image-2.6.15-25-amd64-generic               2.6.15-25.43
  linux-image-2.6.15-25-amd64-k8                    2.6.15-25.43
  linux-image-2.6.15-25-amd64-server                2.6.15-25.43
  linux-image-2.6.15-25-amd64-xeon                  2.6.15-25.43
  linux-image-2.6.15-25-k7                          2.6.15-25.43
... 
```
sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
``` 
So where is the    linux-image-2.6.15-25-k7 ?

```
apt-cache search linux-image | grep k7
linux-image-2.6.15-23-k7 - Linux kernel image for version 2.6.15 on AMD K7 SMP/UP
linux-image-2.6.15-25-k7 - Linux kernel image for version 2.6.15 on AMD K7 SMP/UP
linux-image-k7 - Linux kernel image on AMD K7.

``` 
There... then why isn't it upgraded automatically?
Maybe i need this package : linux-k7 ??

---

### Post by Koybe on 2006-06-16
That's it... i didn't know about these packages...

---

