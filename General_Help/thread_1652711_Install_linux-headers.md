---
title: "Install linux-headers"
date: 2010-12-25
forum: General Help
---

### Post by bjdk on 2010-12-25
Hi,

Ubuntu 11.04. 

Trying to install VMWare Server I got stuck with "What is the location of the directory of C header files that match your running kernel" with suggestion "/usr/src/linux/include".
As far as I can see - just came from Vista so I fumble a bit ;) - the suggested directory does not exists. I am unsure how to find these header-files, and do not know what they are supposed to look like.

I did try to install the headerfiles (sudo apt-get install linux-headers...), but was told that they where updated and OK.

Any help will be much obliged.

Thank You
Bjorn

---

### Post by ruben_linux on 2010-12-25
sudo aptitude install linux-headers-`uname -r` build-essential

---

### Post by bjdk on 2010-12-25
Thank you. But it installs nothing (No packages will be installed, upgraded or removed). Actually I have already installed this as part of the VMWare-installation.

I think the problem is, that the "C header files" are located elsewhere in this Ubuntu-distribution. But I am not sure what to look for.

Thanks

Bjorn

---

### Post by bjdk on 2010-12-29
Could anybody point me in the direction of where to look for "C headers", since VMWare wants them, but expects to find them in a non-existing directory.

Thanks

Best regards
Bjorn

---

### Post by havier49 on 2011-01-03
Did you ever find an answer to this problem?   I am having the same issue after upgrading to the latest version of ubuntu.

Thanks,


Tony

---

### Post by bjdk on 2011-01-03
Sorry no, I had to reverse to Vista - I need VMWare so I had to give it up for now. But when time allows it, I will try do dig a little further, and if I find the solution I will post it here. I really look forward to get away from Vista ;-)

Best regards
Bjørn

---

