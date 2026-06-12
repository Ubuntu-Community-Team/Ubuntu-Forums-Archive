---
title: "Freeze after idle ubuntu 11.10 kernel 3.0.0.15.generic"
date: 2012-02-05
forum: General Help
---

### Post by jcobban on 2012-02-05
Since I applied the most recent kernel update (3.0.0.15.generic) my Ubuntu 11.10 desktop freezes every time I try to wake it up.  I haven't collected the appropriate documentation yet, so this is just a notice to the community.

---

### Post by dino99 on 2012-02-05
might be a graphic driver issue 
boot in recovery mode, remove xorg.conf & check if dkms, linux-headers & the required driver are installed, then reboot.

---

### Post by jcobban on 2012-02-05
> **dino99 said:**
> might be a graphic driver issue 
boot in recovery mode, remove xorg.conf & check if dkms, linux-headers & the required driver are installed, then reboot.

Remember this is a system that has been running for YEARS without any problems.

So far X only freezes if I am running Firefox at the time the system goes to idle.  I am sitting now listening to the sound-track of a video that I cannot see because the system went to idle and with X frozen I cannot recover to see the running video.

I am trying to follow the instructions for obtaining documentation from the frozen system.  First step is "SSH into the frozen system ...

How do I do that.  When I try to either SSH or Telnet into the system the request is rejected:

jcobban@jcobban-laptop:~$ telnet linux-server
Trying 192.168.2.103...
telnet: Unable to connect to remote host: Connection refused
jcobban@jcobban-laptop:~$ ssh linux-server
ssh: connect to host linux-server port 22: Connection refused
jcobban@jcobban-laptop:~$ 

So back to pressing the power button as the only workable recovery!

---

### Post by xyzzyman on 2012-02-05
Where are we to remember this from?

---

### Post by aasdfasdfg on 2012-02-05
> **jcobban said:**
> Since I applied the most recent kernel update  (3.0.0.15.generic) my Ubuntu 11.10 desktop freezes every time I try to  wake it up.  I haven't collected the appropriate documentation yet, so  this is just a notice to the community.

If I am understanding correctly, the system is fully functional after a fresh power cycle?
Assuming this to be the case, have you tried rolling back to the last kernel that worked for you? Simply uninstall the 3.0.0.15.generic kernel from any package manager interface, and ensure you have a previous kernel package still installed. Then reboot, and tell us if the issue persists. This is to narrow down the cause of the problem.

> **xyzzyman said:**
> Where are we to remember this from?
I do not understand what you are trying to say.

---

### Post by aasdfasdfg on 2012-02-05
> **dino99 said:**
> might be a graphic driver issue 
boot in recovery mode, remove xorg.conf & check if dkms, linux-headers & the required driver are installed, then reboot.

Unless I am confused, I thought the xorg.conf was not used at all in Oneiric?

---

### Post by jcobban on 2012-02-06
> **jcobban said:**
> 
I am trying to follow the instructions for obtaining documentation from the frozen system.  First step is "SSH into the frozen system ...

How do I do that.  When I try to either SSH or Telnet into the system the request is rejected:

jcobban@jcobban-laptop:~$ telnet linux-server
Trying 192.168.2.103...
telnet: Unable to connect to remote host: Connection refused
jcobban@jcobban-laptop:~$ ssh linux-server
ssh: connect to host linux-server port 22: Connection refused
jcobban@jcobban-laptop:~$ 

So back to pressing the power button as the only workable recovery!

I answered my own question.  I installed the recommended sshd on the target system.  For us idiots that should be part of the documented procedure for dealing with an X freeze.

---

### Post by jcobban on 2012-02-06
> **aasdfasdfg said:**
> If I am understanding correctly, the system is fully functional after a fresh power cycle?
Assuming this to be the case, have you tried rolling back to the last kernel that worked for you? Simply uninstall the 3.0.0.15.generic kernel from any package manager interface, and ensure you have a previous kernel package still installed. Then reboot, and tell us if the issue persists. This is to narrow down the cause of the problem.


I don't know if the problem was the 3.0.0.15.generic kernel or something in the last update to FF that I installed.  The freeze only happens when I am running FF, although I do not believe an application like FF should be able to freeze X.  If it can that, to me, indicates both a bug in FF and a vulnerability in X.

This is my "bleeding edge" system so it gets the latest production fixes and therefore is vulnerable to temporary problems like this.

The last five kernels are still present in the system, back to 2.6.38.11.generic.  Unlike 10.04 LTS that I am running on my other system I note that 11.10 does not seem to offer the option of booting to an earlier kernel, at least the grub2 menu that is displayed when I boot only includes the latest kernel.  I am not yet familiar with grub2 so I do not understand why the back versions appear in /boot/grub.cfg but do not appear in the boot menu.

---

