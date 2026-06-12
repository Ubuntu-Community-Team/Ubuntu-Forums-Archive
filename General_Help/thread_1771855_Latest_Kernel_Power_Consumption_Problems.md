---
title: "Latest Kernel Power Consumption Problems"
date: 2011-05-30
forum: General Help
---

### Post by craig10x on 2011-05-30
I have noticed that every distro i try that uses the new kernel (including ubuntu 11.04...Kubuntu 11.04...Mint 11...Zorin 5, etc etc) on my toshiba laptop has the power problem that has been widely discussed on the internet...

Under the previous kernels, never had a problem...fan runs nice and quiet (hardly even know it is on)...But anything with the new kernel, fan goes on full blast...sometime the computer will even shut off after a few hours (must be a built in safety feature to protect the motherboard from excessive heat)...

Don't have anything to monitor it, but i have to assume that power consumption must be WAY UP...(i use the laptop as a desktop on AC only)...

I know not everyone gets it, but i understand that many have and there is no set pattern (affects netbooks, laptops, desktops, intels, amd, etc)....

Have many others here experienced the problem?
I read it is considered a high priority for ubuntu and the kernel developers to fix...

Do you think it will take a long time on this to get a fix?
Meanwhile i can't use ANY distro that had the new kernel and i read that even the kernel after this one has the same problem :(

All Feedback on this topic will be appreciated ;)

---

### Post by tgalati4 on 2011-05-30
Open a terminal:

sudo apt-get install acpitool
acpitool -B

Post the output from the above command.

Pull the AC plug, run it on battery for 10 minutes, then run it again:

acpitool -B

It will give you discharge watts (expressed in milliwatts).  Pay attention to that number when doing normal activities.  Monitor the wattage in Windows doing the same activities.  You will have to find a Windows tool as I don't use Windows, I don't know what is used to monitor power use.

---

### Post by Z06Gal on 2011-05-30
bump

---

### Post by idoitprone on 2011-05-31
that is normal. current kernels is suffering a power regression. Hope this fixed in the 2.6.40 kernel release, so the kernel team can backport it to the 2.6.38 kernel in natty. 

[http://www.phoronix.com/scan.php?page=article&item=linux_mobile_uffda&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_mobile_uffda&num=1) 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131) 

try opensuse 11.4 it uses the 2.6.37 kernel which have not affected as bad as the 2.6.38

meh, i dont care. i use arch as slim as a distro i can try. worst it can do me is add 1 w to to my usual 8w usage.

---

### Post by Z06Gal on 2011-05-31
Michael Larabel tweet this morning:


"to solve the Linux kernel power regression today?"

---

### Post by craig10x on 2011-05-31
I hope they fix it sooner then the .40 kernel...

I'm running Mint 10 on my hard install (ubuntu 10.10 underneath of course) that kernel causes NO PROBLEMS on my laptop at all...fan is quiet as a mouse...
I guess i will have to stay with it until the problem is fixed...

---

### Post by idoitprone on 2011-06-01
i hardly think that they can fix it any sooner than the 2.6.40 kernel release. it is the next kernel release and the 2.6.39 is already released.


you should read about kernel development, if wonder why it is so slow. Remember kernel development is essentially a bureaucratic process in which linus is the supreme tyrannt and companies are battling to get their code in.
[http://kerneltrap.org/Linux/Kernel_Release_Numbering_Redux](http://kerneltrap.org/Linux/Kernel_Release_Numbering_Redux)
[http://www.linfo.org/kernel_version_numbering.html](http://www.linfo.org/kernel_version_numbering.html)

[http://www.linux.com/learn/tutorials/387494:understanding-the-stable-linux-kernel](http://www.linux.com/learn/tutorials/387494:understanding-the-stable-linux-kernel)

---

