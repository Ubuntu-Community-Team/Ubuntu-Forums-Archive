---
title: "Hal performance in 9.04 - scream!"
date: 2009-07-21
forum: General Help
---

### Post by bagpussnz on 2009-07-21
Hi,
I am running 9.04 on a Dell E6400. 
If the machine gets put under any stress (I usually see this running a virtual machine), I see the load average escalate (above 5). When this happens, I usually see the process hal-system-smbi hogging all resources.

Killing applications on the box doesn't seem to help - I end up having to reboot.

Is anyone else seeing this - it's driving me crazy!

Could it be power related - as I also see hal power processes (can't remember what they are) when this happens. I thought it could be my docking station (but I've also seen it at home when not on docking station - but not as much - but could be I don't stress it as much at home).

Regards,
Ian.

---

### Post by r0cketman on 2009-09-09
I see the same thing on my Dell E6500.  I recently installed 9.04 after having performance issues with openSUSE 11.1 hoping they would clear up.

I'm starting to wonder if this is a BIOS/hardware issue or a weird kernel module issue specific to our Dell machines.

---

### Post by gomzie on 2009-10-02
Were you able to fix this? Can you let me know how did you fix this?

---

### Post by r0cketman on 2009-10-02
I can't say it's completely fixed, no.  I was able to somewhat minimize the impact by changing my SATA configuration in the BIOS from AHCI to Intel's Power Management option (can't remember the actual name).  I still see the system load hop up to 6-8 when running either VirtualBox or VMware Workstation, but it doesn't completely cripple the entire system (just the VM).

---

### Post by g.a. on 2009-10-02
I guess I have the same problem with a Dell Precision M2400.

When I run a specific software that runs several graphical animations, after 10-15 minutes the system slow down and the process hal-system-smbi takes all the CPU.

The only difference with you is that I have to actually shut down the laptop, a simple reboot does not solve the problem.

I read somewhere that it was a bug with an hal package but I'm not able to find it anymore...

best
g.

---

### Post by r0cketman on 2009-10-02
I wonder if we all ought not to contact Dell and see if we can get a bug submitted against it.  IMO, this is seemingly a Dell-specific SATA driver bug, though I haven't taken the time yet to coredump the system while it's happening.  I've seen the same problem with openSUSE 11.1 and Ubuntu 9.04, so it seems to be distribution independent to me.

---

### Post by useResa on 2009-10-20
Hi, I am running on a Dell Latitude D620 and am experiencing the same.

> **bagpussnz said:**
> If the machine gets put under any stress (I usually see this running a virtual machine), I see the load average escalate (above 5). When this happens, I usually see the process hal-system-smbi hogging all resources.This is exactly the same symptoms I am having. I -- for work -- run Windows in VMware Server 2.0 and when I run heavy processes that is when things go haywire.

> **bagpussnz said:**
>  Killing applications on the box doesn't seem to help - I end up having to reboot.
Is anyone else seeing this - it's driving me crazy!I understand this very well ... also I am having the same symptoms in this area  ;-)

> **r0cketman said:**
> I can't say it's completely fixed, no. I was able to somewhat minimize the impact by changing my SATA configuration in the BIOS from AHCI to Intel's Power Management option (can't remember the actual name).I have also disabled the Power Management in the BIOS (although the factory default setting is enabled)

Additionally I have also switched off CPU scaling by disabling SpeedStep (as suggested in [this post]("http://www.linuxquestions.org/questions/showthread.php?p=3646327#post3646327") at LinuxQuestions.org. Now my CPUs are constantly at 2.16 GHz regardless of the load. Hopefully that will solve (or at least surpress) the issue.

---

### Post by bagpussnz on 2009-10-22
It's fixed now. I eventually phoned Dell (on full support with them) and told them I had CPU problems. The next day they came out and replaced my motherboard and CPU.
Since then the machine has been great - no more problems at all.

Ian.

---

### Post by useResa on 2009-10-22
> **bagpussnz said:**
> It's fixed now. I eventually phoned Dell (on full support with them) and told them I had CPU problems. The next day they came out and replaced my motherboard and CPU.
Since then the machine has been great - no more problems at all.
Thanks for the feedback. My understanding is that the issue thus was caused by hardware.

Makes me think that r0cketman may have a point when he stated:
> **r0cketman said:**
> I wonder if we all ought not to contact Dell and see if we can get a bug submitted against it.

---

### Post by g.a. on 2010-03-30
Hi,

I'm still having some hal-system-smbi problem as described above.

Before contacting Dell I would like to know if you have any update about and i would like to try to set constant CPU speed that seems to solved this trouble for some of the users. Could you please redirect me to a post where this procedure is explained?

Also, since time elapsed since your posts, did you moved to 9.10? what about this trouble?

Thanks in advance,
g.

---

### Post by r0cketman on 2010-03-30
I, for one, have updated to 9.10 (and can't wait for 10.04) but I still see the system load issue.  It seems to have been quite minimized by the aforementioned BIOS tweak, AND it seems to happen in conjunction with the screensaver kicking in (when configured for anything but blank).

---

### Post by g.a. on 2010-03-31
Hi all,

thanks for your messages.

I have contacted DELL, they can not substitute a CPU based on my (superficial) description. I agree with them. My technician was not expert in Linux.

Do you have any test I could do to verify the problem is a CPU one? do you have eventually your service tag so that I could call DELL and verify with them your description?

Finally, could you please describe more clearly the BIOS changes you did?

Thanks in advance,
g.

---

### Post by g.a. on 2010-04-15
I updated to 9.10 for other reasons and today I had the same problem again.

Dell told me that it is not possible to substitute the CPU based on my description.

Any further suggestion?

g.

---

