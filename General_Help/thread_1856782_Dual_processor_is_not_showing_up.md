---
title: "Dual processor is not showing up"
date: 2011-10-09
forum: General Help
---

### Post by jsvidyad on 2011-10-09
Hello,
   I have a system with 2 pentium 4 3 GHz processors. I just found that only one processor is showing up when I looked at the system monitor or when I typed the command 'cat /proc/cpuinfo' . Why is this happening. I updated ubuntu today and a new kernel was installed. Is that the problem? The output of 'uname -r' is 2.6.32-34-generic . 

Can someone help me with this?

---

### Post by jsvidyad on 2011-10-09
I forgot to mention that I'm running ubuntu 10.04.3 LTS

---

### Post by WasMeHere on 2011-10-09
Do you have a 64-bit or 32-bit OS? Run to find out!
```
uname -a
```
There are some 32-bit kernels that support only one processor.

---

### Post by jsvidyad on 2011-10-09
I have a 32 bit os. The thing is, I was able to see and use two processors before today. I am not sure if the kernel upgrade is what caused the problem.

---

### Post by jsvidyad on 2011-10-09
The upgraded kernel is also from the ubuntu repositories obtained using the command 'sudo apt-get dist-upgrade' .

---

### Post by dcstar on 2011-10-09
> **jsvidyad said:**
> Hello,
   I have a system with 2 pentium 4 3 GHz processors. I just found that only one processor is showing up when I looked at the system monitor or when I typed the command 'cat /proc/cpuinfo' . Why is this happening. I updated ubuntu today and a new kernel was installed. Is that the problem? The output of 'uname -r' is 2.6.32-34-generic . 

Can someone help me with this?

Double check your BIOS that both CPUs are enabled.

---

### Post by WasMeHere on 2011-10-09
Please check with
```
uname -[COLOR="Red"]a[/COLOR]
```
My lucid system has an [COLOR="Red"]i686[/COLOR] kernel and it manages two cpus. It is also shown with [COLOR="Red"]SMP[/COLOR]. But there are i386 and i486 kernels that don't. They are sometimes used for compatibility with very old computers. ```
Linux April-2008 2.6.32-33-generic #72-Ubuntu [COLOR="Red"]SMP[/COLOR] Fri Jul 29 21:08:37 UTC 2011 [COLOR="Red"]i686[/COLOR] GNU/Linux
```

---

### Post by jsvidyad on 2011-10-09
> **dcstar said:**
> Double check your BIOS that both CPUs are enabled.

I didn't change any BIOS settings and I was able to see the two processors earlier. Though, I will check that the next time I boot my computer. But, I don't think that's the problem.

---

### Post by jsvidyad on 2011-10-09
> **Olle Wiklund said:**
> Please check with
```
uname -[COLOR="Red"]a[/COLOR]
```
My lucid system has an [COLOR="Red"]i686[/COLOR] kernel and it manages two cpus. It is also shown with [COLOR="Red"]SMP[/COLOR]. But there are i386 and i486 kernels that don't. They are sometimes used for compatibility with very old computers. ```
Linux April-2008 2.6.32-33-generic #72-Ubuntu [COLOR="Red"]SMP[/COLOR] Fri Jul 29 21:08:37 UTC 2011 [COLOR="Red"]i686[/COLOR] GNU/Linux
```

The output for uname -a is :
Linux condor 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:40:53 UTC 2011 i686 GNU/Linux

  I just noticed that you still haven't updated the kernel on your lucid system to the latest version. I'd like to know what happens once you do that. I made the kernel update also on another computer, but I didn't check to see if the os on that computer could see the two cores. I'll do that the next time I have the opportunity.

---

### Post by WasMeHere on 2011-10-09
```
Linux condor 2.6.32-34-generic #77-Ubuntu [COLOR="Red"]SMP[/COLOR] Tue Sep 13 19:40:53 UTC 2011 i686 GNU/Linux
``` You should have support for two cpus: [COLOR="Red"]SMP[/COLOR].

> **jsvidyad said:**
> The upgraded kernel is also from the ubuntu repositories obtained using the command 'sudo apt-get dist-upgrade' .
Maybe you shouldn't have *dist*-upgraded. I think the safe thing to do with an LTS version is to wait until the next LTS and accept the automatic prompt to upgrade maybe 4 months after its release (this time maybe July 2012).

Do you have a good backup? Otherwise I suggest that we [COLOR="Red"]call for qualified help about kernels for lucid[/COLOR].

Good luck
Olle

---

### Post by jsvidyad on 2011-10-09
> **Olle Wiklund said:**
> ```
Linux condor 2.6.32-34-generic #77-Ubuntu [COLOR="Red"]SMP[/COLOR] Tue Sep 13 19:40:53 UTC 2011 i686 GNU/Linux
``` You should have support for two cpus: [COLOR="Red"]SMP[/COLOR].


Maybe you shouldn't have *dist*-upgraded. I think the safe thing to do with an LTS version is to wait until the next LTS and accept the automatic prompt to upgrade maybe 4 months after its release (this time maybe July 2012).

Do you have a good backup? Otherwise I suggest that we [COLOR="Red"]call for qualified help about kernels for lucid[/COLOR].

Good luck
Olle


I have no backup at all. Is this such a big problem that I will have to re-install?

---

### Post by WasMeHere on 2011-10-09
It would have been handy to have a fresh backup at a dist-upgrade. But it is not that bad. After all, you can run your computer with one cpu much better than a two-engine airplane with one engine ;-)

I think there are people around at this forum, who can advice how to get the second cpu back to work. If no-one shows up soon, I suggest that you *post a new thread with a good title to attract the experts* on kernel versions and how to install the one you need.

By the way, I just received a prompt to update lucid. It was only a security update (flash-installer) and nothing else. How come you started the dist-upgrade?

---

### Post by jsvidyad on 2011-10-09
> **Olle Wiklund said:**
> It would have been handy to have a fresh backup at a dist-upgrade. But it is not that bad. After all, you can run your computer with one cpu much better than a two-engine airplane with one engine ;-)

I think there are people around at this forum, who can advice how to get the second cpu back to work. If no-one shows up soon, I suggest that you *post a new thread with a good title to attract the experts* on kernel versions and how to install the one you need.

By the way, I just received a prompt to update lucid. It was only a security update (flash-installer) and nothing else. How come you started the dist-upgrade?

The first thing I do when I turn on the computer is to update it.

---

### Post by jsvidyad on 2011-10-11
Hello, 

  I just checked the 2nd desktop running ubuntu 10.04.3.LTS. Both the processors are showing up for this computer. But, this is a core 2 duo machine, whereas the other desktop has dual pentium4  processors. Not sure why the two processors don't show up for the other machine.

---

### Post by mcduck on 2011-10-11
> **Olle Wiklund said:**
> ```
Linux condor 2.6.32-34-generic #77-Ubuntu [COLOR="Red"]SMP[/COLOR] Tue Sep 13 19:40:53 UTC 2011 i686 GNU/Linux
``` You should have support for two cpus: [COLOR="Red"]SMP[/COLOR].


Maybe you shouldn't have *dist*-upgraded. I think the safe thing to do with an LTS version is to wait until the next LTS and accept the automatic prompt to upgrade maybe 4 months after its release (this time maybe July 2012).

Do you have a good backup? Otherwise I suggest that we [COLOR="Red"]call for qualified help about kernels for lucid[/COLOR].

Good luck
Olle
A dist-upgrade does not upgrade you to next Ubuntu release version, it's simply a bit more powerful version of normal apt-get upgrade, with the ability to remove package if necessary to complete the updates. For example updating Ubuntu using the Synaptic Package Manager works the same way. (This is as opposed to normal upgrade, or using the Update Manager, which are only allowed to replace an existing package with a new version).

You *can* use dist-upgrade to upgrade to new release version, but to do that you'd fist have to manually edit your software sources to point to the new release's repositories. The preferred way for release upgrades is to run "sudo update-manager -d" (using the Update Manager) or "sudo do-release-upgrade" (for command-line).

---

### Post by WasMeHere on 2011-10-11
> **mcduck said:**
> A dist-upgrade does not upgrade you to next Ubuntu release version, it's simply a bit more powerful version of normal apt-get upgrade, with the ability to remove package if necessary to complete the updates. For example updating Ubuntu using the Synaptic Package Manager works the same way. (This is as opposed to normal upgrade, or using the Update Manager, which are only allowed to replace an existing package with a new version).

You *can* use dist-upgrade to upgrade to new release version, but to do that you'd fist have to manually edit your software sources to point to the new release's repositories. The preferred way for release upgrades is to run "sudo update-manager -d" (using the Update Manager) or "sudo do-release-upgrade" (for command-line).

Thanks *mcduck*,
What do you suggest to do now to help?

---

### Post by foureyesboy on 2011-10-11
Could you post what do you see when executing:
```
 dmesg | grep -i smp 
```

---

