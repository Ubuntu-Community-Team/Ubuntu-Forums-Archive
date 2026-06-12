---
title: "Big warning on Linux kernel 3.0.0-17 kernel update!"
date: 2012-04-02
forum: General Help
---

### Post by asuastrophysics on 2012-04-02
Fellow ubuntu users,

After spending about 2 hours fixing what update manager did to my computer yesterday, I must warn you that if you have NVIDIA drivers, you should NOT update to the 3.0.0-17 kernel. Here's some information from the APT update log:
```
Start-Date: 2012-04-01  14:23:30
Commandline: aptdaemon role='role-commit-packages' sender=':1.91'
Install: linux-image-3.0.0-17-generic:amd64 (3.0.0-17.30)
[B]Upgrade: libgudev-1.0-0:amd64 (173-0ubuntu4.1, 173-0ubuntu4.2), linux-generic:amd64 (3.0.0.16.19, 3.0.0.17.20), udev:amd64 (173-0ubuntu4.1, 173-0ubuntu4.2), linux-image-generic:amd64 (3.0.0.16.19, 3.0.0.17.20), flashplugin-installer:amd64 (11.1.102.63ubuntu0.11.10.1, 11.2.202.228ubuntu0.11.10.1), libudev0:amd64 (173-0ubuntu4.1, 173-0ubuntu4.2), ca-certificates-java:amd64 (20110912ubuntu3, 20110912ubuntu3.2)
[/B]End-Date: 2012-04-01  14:25:01
```

The updates installed inflicted damage in the following areas:
1. This kernel update installed the kernel, but did not install the linux-headers-generic package (this package is required in order for the user to start an X session. Why is this not installed alongside the kernel by default?)
2. This kernel update added a nice little entry in /etc/modprobe.d/blacklist.local.conf called "**blacklist nvidia_current"**, which completely disabled my video driver without my permission.
3. The kernel update did not run dkms to build an nvidia driver module for the kernel. This had to be performed manually in a CLI prompt.

Conclusion:
These are serious bugs, and #2 on the list here could be considered by some to be malicious. How does me typing in my password for the update manager authorize it to add in code to disable my video card?
If you are running proprietary Nvidia drivers, please do not choose to install the latest kernel update (3.0.0-17) without seriously considering the possible repercussions. This needs to be fixed by upstream ASAP to prevent this happening to anyone else.
Any thoughts?

---

### Post by winh8r on 2012-04-02
Probably best to get in touch with the kernel team:

[https://bugs.launchpad.net/~ubuntu-kernel-team]("https://bugs.launchpad.net/~ubuntu-kernel-team")

Good to see you got it up and running again though ;)

---

### Post by asuastrophysics on 2012-04-02
> **winh8r said:**
> Probably best to get in touch with the kernel team:

[https://bugs.launchpad.net/~ubuntu-kernel-team]("https://bugs.launchpad.net/~ubuntu-kernel-team")

Good to see you got it up and running again though ;)

Will do, I'll file a bug report there. I just wanted to post up a warning so others can avoid the same bug. And thanks! The good thing about ubuntu is that you can recover from almost any error if you are persistent enough. :popcorn:

---

### Post by winh8r on 2012-04-02
I would imagine it will be a fairly high priority for them to get that one sorted out.

Breakable but fixable, love it!

---

### Post by Mariane on 2012-04-02
Isn't it a bit similar to what you get when you do

[code]
sudo do-release-upgrade
|/code]

? 

You get a warming that some proprietary drivers are going to be disabled and that if you want them back you'll have to activate them again using the update manager or I've forgotten what. 

But I quite agree that

1) You should get the warning
2) Reactivating the drivers should be made easy, not booby-trapped

It took you 2 hours to reactivate your nvidia driver, in such conditions it would take me 20 hours. If I'm lucky.

---

### Post by dave2001 on 2012-04-02
> **asuastrophysics said:**
> 
If you are running proprietary Nvidia drivers, please do not choose to install the latest kernel update (3.0.0-17) without seriously considering the possible repercussions. 

Thanks for the warning! 
I've got an Nvidia card on my desktop.  A kernel update screwed me in a very similar way about 2 months ago, I'm glad to avoid the headache again.

On a side note: I grew up in Boone! Great little town!

---

### Post by asuastrophysics on 2012-04-02
> **Mariane said:**
> 
You get a warming that some proprietary drivers are going to be disabled and that if you want them back you'll have to activate them again using the update manager or I've forgotten what. 

But I quite agree that

1) You should get the warning
2) Reactivating the drivers should be made easy, not booby-trapped


You are correct in that the kernel module update is similar to a do-release-upgrade command. I don't understand why the installer can't 1) detect which module it disabled before installation, 2) build a new graphics kernel module against the new kernel, and finally 3) re-enable the graphics driver by removing it from the blacklist.

More importantly, the installation **should install the appropriate kernel headers for the new kernel by default**. (Bolded because I can't stress enough how important this is!) You really can't use the kernel without kernel headers, so the linux-headers-generic package should be installed automatically. 

This would fix the problem and make kernel updates seemless for those who use proprietary graphics drivers. I bet I could write a program in java that would do this, and it probably wouldn't take more than 30 minutes to do it.

---

### Post by Frogs Hair on 2012-04-02
I didn't have any problems with 3.0.0-17 with Nvidia current drivers but I received 3.0.0-18 through proposed updates today . Nothing different to report so far.

---

