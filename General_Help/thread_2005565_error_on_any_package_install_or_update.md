---
title: "error on any package install or update"
date: 2012-06-17
forum: General Help
---

### Post by cmcanulty on 2012-06-17
I suddenly get these 2 errors on anything I try to install or uninstall or update. Have done numerous searches with no luck  


```

Setting up initramfs-tools (0.99ubuntu13) ...
update-initramfs: deferring update (trigger activated)
Setting up nfs-common (1:1.2.5-3ubuntu3) ...
/usr/bin/ucf: line 520: awk: command not found
dpkg: error processing nfs-common (--configure):
 subprocess installed post-installation script returned error exit status 127
Processing triggers for initramfs-tools ...
/usr/sbin/update-initramfs: 236: /usr/sbin/update-initramfs: awk: not found
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 nfs-common
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by maverickaddicted on 2012-06-18
> **cmcanulty said:**
> I suddenly get these 2 errors on anything I try to install or uninstall or update. Have done numerous searches with no luck  


```

Setting up initramfs-tools (0.99ubuntu13) ...
update-initramfs: deferring update (trigger activated)
Setting up nfs-common (1:1.2.5-3ubuntu3) ...
/usr/bin/ucf: line 520: awk: command not found
dpkg: error processing nfs-common (--configure):
 subprocess installed post-installation script returned error exit status 127
Processing triggers for initramfs-tools ...
/usr/sbin/update-initramfs: 236: /usr/sbin/update-initramfs: awk: not found
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 nfs-common
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Check this, might help you -

[https://answers.launchpad.net/ubuntu/+source/initramfs-tools/+question/117247](https://answers.launchpad.net/ubuntu/+source/initramfs-tools/+question/117247)
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/916696](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/916696)

---

### Post by matt_symes on 2012-06-19
Hi

Let's have a look at your system and see where you are.

Open a terminal and post the output of...

```
dpkg -l | grep awk
```

(Small L after dpkg)

Due to your previous problems, please post the output of.

```
update-alternatives --display awk
```

> Things are still getting worse. This am all the menus on my panels are white letters on light background also.And neither Ubuntu tweak or gnome tweak will open.

That sounds like you may have an issue with the themes. We'll look at that later for you.

It may be worth performing a hard drive check (both fsck {run with the "perform no action, just test" switch} and SMART). I will talk you though how to do this.

You will need a LiveCD or USB handy to do this. Do you have one handy ?

Kind regards

---

### Post by cmcanulty on 2012-06-19
Yes I have a USB live image . Here is the output. Also I have been going through the alternatives in terminal and a whole bunch of them say linkgroup is broken. I am not sure if that is relevant.I tried this but it gave errors. Everything seems screwed up now I can only login to classic, the other options are there but don't work. I wanted to try unity, xubuntu etc to see if they are screwed up to but I can't.

 ```
update-alternatives yes  ''  |  update-alternatives  --force

```

```
cmcanulty@Darcy25:~$ dpkg -l | grep awk
ii  dpkg-awk                                                    1.1                                                 Gawk script to parse /var/lib/dpkg/{status,available} and Packages
ii  gawk                                                        1:3.1.8+dfsg-0.1ubuntu1                             GNU awk, a pattern scanning and processing language
ii  mawk                                                        1.3.3-17                                            a pattern scanning and text processing language
cmcanulty@Darcy25:~$ update-alternatives --display awk
awk - auto mode
  link currently absent
/usr/bin/gawk - priority 10
  slave awk.1.gz: /usr/share/man/man1/gawk.1.gz
  slave nawk: /usr/bin/gawk
  slave nawk.1.gz: /usr/share/man/man1/gawk.1.gz
/usr/bin/mawk - priority 5
  slave awk.1.gz: /usr/share/man/man1/mawk.1.gz
  slave nawk: /usr/bin/mawk
  slave nawk.1.gz: /usr/share/man/man1/mawk.1.gz
Current 'best' version is '/usr/bin/gawk'.
cmcanulty@Darcy25:~$ 
```

---

