---
title: "Uninstalling Python crashed Jaunty"
date: 2009-09-14
forum: General Help
---

### Post by amitkhanna on 2009-09-14
Hi All

I tried to install python-qwt5-qt4 and got the following error

#sudo apt-get install python-qwt5-qt4

The following packages have unmet dependencies:
  python-qwt5-qt4: Depends: python (< 2.6) but 2.6.1-0ubuntu3 is to be installed

hence i marked python2.6 for removal and python2.5 for installation from synaptic package manager.

After installation finished many packages including network manager got removed. When i restarted the system it is running in command prompt only.

Can anyone help me in restoring my system?

Thanks
Amit

---

### Post by oldfred on 2009-09-14
If you can reinstall python 2.6. Ubuntu runs that for many internal tasks and I think that includes updates.

You can have both 2.6 and 2.5 on your system, but if you want to use 2.5 your have to specify that when you load python.

---

### Post by amitkhanna on 2009-09-15
The problem is that i'm only able to login through command prompt. The network interface is not working. I have a CD of ubuntu and want to restore my system. I don't want to reinstall ubuntu just want to install normal packages that are installed by default so that my system starts working again in GUI.

---

### Post by DRNewcomb on 2009-09-16
I just had the same problem, for the same reason (trying to install Qwt5). I ended up with a text-only login. From this I was able to run "sudo apt-get install ubuntu-desktop". Went away for a cup of coffee and the problem was fixed.

Now to figure out why Qwt5 won't install.

---

### Post by oldfred on 2009-09-17
This page has instructions on installing from live CD.

[https://help.ubuntu.com/community/AptCdrom](https://help.ubuntu.com/community/AptCdrom)

---

### Post by slakkie on 2009-09-17
Do you have a fixed network connection? Or only wireless?

If you have a fixed connection: [https://help.ubuntu.com/community/NetworkConfigurationCommandLine](https://help.ubuntu.com/community/NetworkConfigurationCommandLine)

You can also recover by using a livecd and chroot and apply the updates within the jail, use the following script to enter and disable the chroot. /dev/sdb1 is my root slice, your can be different, change it accordingly.

[http://pb.opperschaap.net/37](http://pb.opperschaap.net/37)

When in the chroot, you can reinstall python again. Python is CRUCIAL for the workings of Ubuntu, update-managers are written in python.

---

