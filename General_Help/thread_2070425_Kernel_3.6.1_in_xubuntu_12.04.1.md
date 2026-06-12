---
title: "Kernel 3.6.1 in xubuntu 12.04.1?"
date: 2012-10-12
forum: General Help
---

### Post by wanderingwaste on 2012-10-12
I am looking to install the 3.6.1 kernel on my laptop, as I have heard it does significantly better with battery power than the 3.2.0 kernel present in Xubuntu 12.04.1, and I was wondering how best to go about doing so.
 
 I've looked into compiling the kernel from source, which to be honest looks like fun. This however would seem to only leave me with the stock Linux kernel, minus any specifics for Ubuntu/Xubuntu.  
 
 It would also seem that I can just download the packages from kernel.ubuntu.com and install them. This seems like it should be fairly straightforward.
 
 I've also heard that you can add the latest kernel to apt, and have it automatically pull and install the kernel and kernel headers. I have not been able to find a clear set of instructions for doing this (or maybe I'm just thick).
 
 My questions are threefold: What's the best method for upgrading the kernel? Will I have to update the kernel manually from now on (security updates, etc)? How will this effect the security of my system (vis a vis apparmor and such)?
 

 If upgrading my kernel means I'll have to update it myself manually, and the ubuntu kernel specifics aren't too necessary, I think what I'll do is compile from source, as that looks to be the most fun and educational (not to mention the nerd cred).

---

### Post by dino99 on 2012-10-12
you can download & install the vanilla one:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.1-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.1-quantal/)

you need to download into an empty folder:
- header .... all.deb
- the other header you need : 32 or 64 bits
- the 2 images related to the headers

then into a terminal:

- cd to that folder with the kernel downloads
- run : sudo dpkg -i *

thats all ):P

---

### Post by Doug S on 2012-10-12
> What's the best method for upgrading the kernel? Will I have to update the kernel manually from now on (security updates, etc)? How will this effect the security of my system (vis a vis apparmor and such)?I don't know if it's the "best" method, but I'll tell you what I do: For the pre-built kernel from Ubunutu [kernel-ppa]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") , I download the 4 .deb files into a directory, for example ~/temp-3.6.1 and end up with (for my case, 64 bit):```
doug@s15:~/temp-3.6.1$ ls -l
total 52112
-rw-rw-r-- 1 doug doug 12258644 Oct 11 18:58 linux-headers-3.6.1-030601_3.6.1-030601.201210071322_all.deb
-rw-rw-r-- 1 doug doug   943922 Oct 11 18:57 linux-headers-3.6.1-030601-generic_3.6.1-030601.201210071322_amd64.deb
-rw-rw-r-- 1 doug doug 12280194 Oct 11 18:59 linux-image-3.6.1-030601-generic_3.6.1-030601.201210071322_amd64.deb
-rw-rw-r-- 1 doug doug 27872864 Oct 11 19:01 linux-image-extra-3.6.1-030601-generic_3.6.1-030601.201210071322_amd64.deb

```Then:```
doug@s15:~/temp-3.6.1$ sudo dpkg -i *.deb
```Then re-boot.
Updates and such will still work. For example I just did updates, including dist-upgrade, on my test 12.04 server while it was running kernel 3.6.1 and it got the new 3.2.0.32-51 kernel. However, you would have to maintain the 3.6.1 series kernel yourself, i.e. if there was a 3.6.2 you wanted to try. And, of course, by default your system will boot to the 3.6.1, not the new 3.2.0.32-51.
As far as I know system security is O.K.
Now, if I get the source from kernel.org and compile and install it myself, I never figured out why (or even tried), but it runs way faster. In that case it was not clear to me if apparmour was running or not. (I didn't care because that computer is not accessible from internet, and I was busy with another issue at the time.)
 
Let us know what you decide and how you make out.
 
Oh and by the way, on an old launchpad bug, someone reported earlier today the kernel 3.2.0.32-51 has less CPU load when idle on desktops. (I only use server editions).
 
Edit: I guess I was typing forever and did not notice that dino already replied.

---

### Post by rojaasensei on 2012-10-12
I've used the method described on [http://www.upubuntu.com/2012/10/install-linux-kernel-361-on-ubuntu.html](http://www.upubuntu.com/2012/10/install-linux-kernel-361-on-ubuntu.html) and the installation was flawless.

I use kernel 3.6.1 on my lenovo laptop G770

---

### Post by amirzaim on 2012-10-12
Pardon me, Kernel 3.6 can be installed in Ubuntu 12.04, but since the Kernel 3.6 is built for 12.10, it would may have some problems like some hardwares didn't function properly. I had been facing this issue long time ago and I have to install the latest kernel via custom compilation. Even though that custom compilation is bit risky, but sooner it would be better than using the provided kernel packages.

---

### Post by pqwoerituytrueiwoq on 2012-10-12
> **dino99 said:**
> you can download & install the vanilla one:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.1-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.1-quantal/)

you need to download into an empty folder:
- header .... all.deb
- the other header you need : 32 or 64 bits
- the 2 images related to the headers

then into a terminal:

- cd to that folder with the kernel downloads
- run : sudo dpkg -i *

thats all ):P
3.6.2 is out [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.2-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.2-quantal/)

[kernel-3.6.2-installer.tar.bz2]("http://ubuntuforums.org/attachment.php?attachmentid=225480&d=1350086348")
so far it works... i think my plymouth theme takes longer to start at boot now :(
** using xubuntu 12.10

---

### Post by divino_marchese on 2012-11-13
I'd like to install 3.6.2 kernel deb packages from here

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.2-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.2-quantal/)

Is it safe for Ubuntu 12.04? Has someone try it?

Thanks.

---

