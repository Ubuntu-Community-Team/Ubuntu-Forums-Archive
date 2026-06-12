---
title: "Problems after upgrade to Ubuntu 6.06 LTS"
date: 2006-06-14
forum: General Help
---

### Post by aegypius on 2006-06-14
Hello

A few days ago i upgrade to Ubuntu 6.06 LTS with the update manager with no problems. But now the Vmware doesn't work. I run vmware in the Terminal and show this message:

> vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

I invoke the command /usr/bin/vmware-config.pl and start the configuration. Then in this step :
> What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]


I dont have this directory /usr/src/linux/include. I have the following directories: /usr/src/linux-headers-2.6.12-10 and /usr/src/linux-headers-2.6.12-10-386.

If i put one of this directories insted os /usr/src/linux show this message:

> The directory of kernel headers (version 2.6.12-10) does not match your running
kernel (version 2.6.15-23-386).  Even if the module were to compile
successfully, it would not load into the running kernel.

I need some help.

---

### Post by Ctrl+Alt+Del on 2006-06-14
Check out the Preparation section of [https://wiki.ubuntu.com/InstallingVMware?highlight=%28vmware%29](https://wiki.ubuntu.com/InstallingVMware?highlight=%28vmware%29) that should  get it up and running

---

### Post by aegypius on 2006-06-14
Thanks for help me, 

Where is the correct kernel headers?

If i reinstal the vmware i loose the virtual xp i have?

---

### Post by Ctrl+Alt+Del on 2006-06-14
The kernel header files should have been installed to /usr/src/ and vmware-config should find them, at least it did that in my case.
Your vmware images are save and unchanged as long as you don't touch the vmware folder in your homedir :)

---

### Post by aegypius on 2006-06-14
Thank you Ctrl+Alt+Del

In Terminal i instal a few dependencies

> sudo apt-get install linux-headers-`uname -r` build-essential xinetd

then i run vmware in the Terminal and complete the configuration and its OK.

Thanks

---

