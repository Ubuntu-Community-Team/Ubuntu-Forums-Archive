---
title: "ksoftirqd at 100% CPU on Hyper-V"
date: 2010-05-27
forum: General Help
---

### Post by daniel_szollosi-nagy on 2010-05-27
Just thought I'd share:

I installed 10.04 on a Hyper-V virtual machine and a few hours later discovered that the server was unusually sluggish. Top revealed that ksoftirqd was sucking up around 97% CPU. 

Reading up on the issue focused on earlier kernel issues, which I knew didn't apply to 10.04. I eventually discovered that I set two CPU cores in Hyper-V. Decreasing this to just one CPU solved the issue.

There may be a more elegant solution to all this, but it worked for me.

---

### Post by kosc on 2010-12-18
same problem but I have only 1 CPU.

Any ideas how to fix this ?

I use hyper-v R2 and ubuntu server LTS 10.04.1

---

### Post by daniel_szollosi-nagy on 2010-12-18
Didn't really find a solution, more like a workaround.

I've narrowed down the list of events that cause Ubuntu to start throwing up these ksoftirqd hard faults. These appear to occur whenever the Hyper-V machine state is saved, thus paused and resumed for backup or system shutdown. 

I am using DPM 2010 to back up my Hyper-V machines. After I removed my Ubuntu server from the protection group, the ksoftirqd issues went away. Then, when I patched my Windows 2008 server and it rebooted, it saved the machine state to resume after reboot. After the Hyper-V server rebooted, the ksoftirqd CPU load shot up to 100% again. I did not find a way to recover from this CPU load other than rebooting the Ubuntu machine.

It would therefore appear that this issue results from whatever happens to Ubuntu after the hypervisor resumes its operation. The way to avoid this is to decrease the opportunities for Hyper-V to save the machine state.

Right now Ubuntu is running a test intranet site, so the occasional reboots and even the CPU load on the host server are not a big deal for me. I would sure like to figure out how to resolve this once and for all.

---

### Post by Dirk Mewes on 2011-01-06
We have been working through three related issues, seen running Ubuntu 10.10 under Hyper-V R2 on a Dell T610 with Broadcom NICs.  First, when resuming from suspend, the ksoftirqd pegged the CPU at 99%.  Second, we were unable to get the synthetic network drivers to work on our hardware.  Third, we were seeing really bad clock drift. It turns out that the Hyper-V integration component modules were not properly resuming after Hyper-V suspended the VM for nightly backups.   For us a reasonable workaround was to run with the legacy network adapter, and remove  the Hyper-V integration modules from our Ubuntu VM.    We fixed the time drift by using good old ntp, and setting  &#8220;nohz=off&#8221;  in grub.  
  
Suspending Ubuntu before performing backups is normal operating procedure, and all modules are expected to be able to come back up when Ubuntu resumes.  I guess It's up to the writer of the device driver, or module to ensure that this happens correctly.  From what I understand, when a driver does not properly resume, it overloads the ksoftirqd with interrupts, resulting in the 99% CPU.  In Our case, the hv_* modules were removed, and the problem went away.  
  We removed the integration components  with the following steps:
 
1.       Log into the Hyper-V Manager, and remove the network interface, and reboot.   We found that if we didn&#8217;t do this, the network device would not show up after removing the modules.   Removing the modules when no network device is present will work better.
  
2.       Log into ubuntu using the console, since there is no longer any network.
  
3.       Edit /etc/initramfs-tools/modules, and comment-out the hv_* lines:
  #hv_vmbus
  #hv_storvsc
  #hv_blkvsc
  #hv_netvsc
  #hv_utils
  
4.       Sudo update-initramfs  -u
  
5.       Blacklist the modules by adding the following lines to the file /etc/modprobe.d/blacklist.conf
  blacklist hv_vmbus
  blacklist hv_utils
  blacklist hv_netvsc
  blacklist hv_blkvsc
  blacklist hv_storvsc
  
6.       Reboot.
  
7.       Add the legacy network driver back, reboot, and log back in to the console.  You should see the NIC interface you just added by typing &#8220; ifconfig &#8211;a&#8221; at the prompt.
  
8.       Note that if you use Hyper-V&#8217;s dynamic MAC addresses, then the new interface will come up with a new name.  For instance, if you were using eth0 before, the new interface would come up as eth1.  You can rename the interface  back to its original name by editing the appropriate lines in  /etc/udev/rules.d/70-persistent-net.rules

   We originally tried to run our server with the synthetic network drivers, using the Hyper-V integration components as described here at this link: [http://www.panterlo.com/2010/10/10/ubuntu-10-10-and-hyper-v-r2/](http://www.panterlo.com/2010/10/10/ubuntu-10-10-and-hyper-v-r2/) 
  
We could not get the synthetic network drivers to work on our hardware, even after following all the instructions in the above post.  The network interface would always  crash within five minutes after booting.   We have heard reports that the integration components work well  for other hardware and systems, so I wouldn&#8217;t be surprised if we had encountered a hardware incompatibility, or an unusual setting.  Maybe a similar incompatibility is also uncovering the problems we saw with suspending and resuming the hv_* modules.  I certainly hope that the integration components will resume properly if the synthetic network is functional.  I hope to find a real fix for the synthetic network interface soon, but at least we have a reasonable Ubuntu 10.10 VM running on Hyper-V R2 now.   
  
For the time drift problem, enabling the Microsoft integration modules and using adjtimex seemed to have no effect for us.  Maybe it&#8217;s because the hv_* modules were already hopelessly broken by whatever is hexing our machine.  In any case,  we fixed it by running the ntpd on our Ubuntu VM.  
  
1.       We unchecked the &#8220;Time synchronization&#8221; checkbox in the Hyper-V settings for the VM. 
  
2.        In the /etc/ntp.conf file, we added the line &#8220;tinker panic 0&#8221; so that ntp will accept big time jumps.  
  
3.       In the /etc/default/grub file, we added the boot parameter &#8220;nohz=off&#8221;  to  the GRUB_CMDLINE_LINUX_DEFAULT entry.  
  
4.       We turned on ntp logging, and tested the ability to recover time after suspend/resume.  It does take a few minutes for the ntpd to fix the clock after resuming.  We are looking for a good way to tell the clock to re-sync right away after resuming from a suspended VM.

---

### Post by Nial6 on 2011-04-03
Hello. That's not the Ubintu problem. It;s problem with MS drivers and kernel. Try 2.6.38 kernel. 2.6.37 works, but it's slow. I was fighting this problem for two weeks, I tried many distros (Gentoo, SuSE, many lightweight ones) but It's definitely a kernel problem. Now I have Ubuntu 10.10 with 2.6.38.2 kernel and it runs great. Network card (virtual hyper-v, not legacy) is much faster than in SuSE and others - and I don't know why. It consumes less CPU.

---

### Post by eagle63 on 2011-04-05
I'm having this problem too with Ubuntu 10.10 running as a VM on Hyper-V. It's been running great for months, up until a few days ago when I started using Windows Server Backup on my Hyper-V host.  Once I did that, I'm now getting the ksoftirqd process chewing up 99% CPU.  

A few questions:
@Nial6
I'm on the latest kernel which is 2.6.35-28.  How are you getting 2.6.38?  Are you building your own??


@daniel_szollosi-nagy
Since Ubuntu is not an officially supported linux disto in Hyper-V, how were you able to set 2 CPU's?

---

### Post by kosc on 2011-08-19
Nial6 was right, new kernel solved this.
Here is what I done to fix this ksoftirqd/0 100% CPU problem:

1. Tried with /etc/ntp.conf & /etc/default/grub didn't help :(

2. Downloaded new kernel 2.6.39.4 and compiled it, problem solved
   now my Ubuntu server LTS 10.04.3 works fine on HyperV 2008 R2
   here is link which I used for compiling [http://linuxtweaking.blogspot.com/2011/02/how-to-compile-kernel-from-kernelorg-in.html](http://linuxtweaking.blogspot.com/2011/02/how-to-compile-kernel-from-kernelorg-in.html)

---

### Post by KeinUserName on 2012-06-28
Hi!
Problem before: Suspend and restart the Hyper-V maschine = 97-100% ksoftirqd

Based on the Compiling-Instruction i have compiled a 2.6.32 Kernel without Xen-Guest-Support and this worked for me.

Complete Solution: [http://social.technet.microsoft.com/Forums/en-US/winserverhyperv/thread/f598214f-b459-49f7-ab9f-64fb7b1c2f4b](http://social.technet.microsoft.com/Forums/en-US/winserverhyperv/thread/f598214f-b459-49f7-ab9f-64fb7b1c2f4b)


PS: This is my first post... please don't flame ;)

---

### Post by oldos2er on 2012-06-28
Welcome, KeinUserName. Please try not to bump old threads.

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

