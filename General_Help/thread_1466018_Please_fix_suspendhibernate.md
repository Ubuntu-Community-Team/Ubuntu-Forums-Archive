---
title: "Please fix suspend/hibernate"
date: 2010-04-29
forum: General Help
---

### Post by a-user on 2010-04-29
Since i installed for the first time lucid (beta 2) neither suspend to  ram nor hibbernate worked for me. now i installed release version and  same problems.

i have an amd790gx with an athlon ii x3, nvidia gt220 card. on the very  same machine and karmic all works fine.

with lucid the system prepares successful for suspend/hibernate and when  it comes to the point it should actually power off it hangs with the  black screen. no reaction on keayboard, only reset button or holding  power switch >4sec works.

tried uswsusp and same thing happens.

i had a probably similar issue when installing lucid during the  installation process. the last step in installation is the dialog  requesting to reboot the machine. when i pressed the reboot dialog  button the dialog window disapeared and the system hanged. mouse cursor  still was moveable but no reaction on anything alse, no ctrl+alt+f1, no  ctrl+alt+del ...

what has changed from karmic to not being able to poweroff for  suspend/hibarnate anymore?

please fix this. this bug has been already reported from several users  and there is still no real comment on this.

pm-suspend.log has no failors as it prints all successful and ends with  the final line pwoering off. something like that.

---

### Post by congminh1709 on 2010-04-29
I have the same problem on my laptop Toshiba L305-S5875. Suspend = Not responding.

Any solution for this?

Thanks.

---

### Post by Mike_IronFist on 2010-04-30
> **a-user said:**
> Since i installed for the first time lucid (beta 2) neither suspend to  ram nor hibbernate worked for me. now i installed release version and  same problems.

i have an amd790gc with an athlon ii x3, nvidia gt220 card. on the very  same machine and karmic all works fine.

with lucid the system prepares successful for suspend/hibernate and when  it comes to the point it should actually power off it hangs with the  black screen. no reaction on keayboard, only reset button or holding  power switch >4sec works.

tried uswsusp and same thing happens.

i had a probably similar issue when installing lucid during the  installation process. the last step in installation is the dialog  requesting to reboot the machine. when i pressed the reboot dialog  button the dialog window disapeared and the system hanged. mouse cursor  still was moveable but no reaction on anything alse, no ctrl+alt+f1, no  ctrl+alt+del ...

what has changed from karmic to not being able to poweroff for  suspend/hibarnate anymore?

please fix this. this bug has been already reported from several users  and there is still no real comment on this.

pm-suspend.log has no failors as it prints all successful and ends with  the final line pwoering off. something like that.

Two notes, first of all, Lucid is now released, so you should use the release version now, not the beta.

Second, all bugs should be reported to Launchpad. Ubuntu Forums isn't really for bug reporting, it's for tech support.

---

### Post by a-user on 2010-04-30
to the first note: i already wrote in my first post (even in the first line) that i AM using the relase version now!

second, i already wrote in my first post, that i have reported the bug on launchpad.

because this situation now holds for over two weeks without any new information about the progress i opened this thread to know if anyobdey else has some new info.

so pleease no offence, but read first the post before you reply to it.

---

### Post by Mike_IronFist on 2010-04-30
> **a-user said:**
> to the first note: i already wrote in my first post (even in the first line) that i AM using the relase version now!

second, i already wrote in my first post, that i have reported the bug on launchpad.

because this situation now holds for over two weeks without any new information about the progress i opened this thread to know if anyobdey else has some new info.

so pleease no offence, but read first the post before you reply to it.

Sorry for the mistake about the release version. However, you did not mention Launchpad, and you're asking people at the forums to "fix it", which makes it sound like you're asking us to fix a bug.

Here's my recommendation - start a new thread called something like "Suspend/Resume problems" instead. Aside from that recommendation, I'm afraid I don't know anything about this problem. Sorry!

---

### Post by a-user on 2010-04-30
you are right about my title, but i wrote it cause i feel frustrated.

anyhow, **i found a solution**:
install kernel 2.6.33 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/)

yes this fixed it. it is a bug with the official ubuntu lucid kernel. the lucid version of the 2.3.66 works fine. maybe i will try the rc of 2.6.34 sometime.

p.s. i will set the solved flag after i observed the system for some hourse to be sure no further problems occure.

edit: booting needs now about 3 times longer. i have a ssd as boot drive and from my <10 sec it needs now over 20sec. but i prefere being able to suspend than to have a shorter boot time and a splash screen.

---

### Post by a-user on 2010-04-30
well, it is not solved wihtout any sideffects... sadly:

with that kernel plymouth splash screen is missing and i get the following error message during boot:
[quote]init: ureadahead main process (349) exit with status 5 
 [     3.35860] ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00.0xb07][7uotte]
 
but beside of that all seems to be fine. the bad part of this is, that it slows the booting time a bi.

anybody knows what this means or how to fix?

---

### Post by a-user on 2010-04-30
kernel 2.6.34-rc6 works better. only the problem with ureadahead remains. if anybody knows how to fix this, i would be very thankfull.

additionally, since 2.6.33 support for k10 temperature monitoring is available. sadly the module is not build in the mainline releases. compiling it myself had bad results as the self-build kernel paniced. (tried it with the 2.6.33 source from the mainline repro).

thus, if someone know how to fix the follwoing 2 things:
1. fixing ureadahead for kernel 2.6.34-rc6
2. adding the kernel module k10temp for that kernel release.

---

### Post by a-user on 2010-04-30
ok, hier my temporary solution:

i followed this instructions to build latest upstream kernel with ubuntu lucid install scripts:
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)

before building i applied the ureadahead patch needed
(use google to find that one)

the booting time is still a bit slower than with the lucid default kernel and boot up splash screen plymouth is not working but that's all.

befre i compiled the kernel i also activated the k10temp module that is now in the kernel. hence i finally have cpu temps although they seem to be about 10°C too low. so what ;)

for all gt210/gt220 gt240 nvidia users: with this new kernel the hdmi audio out support seems to be better working.

p.s. i will set status to solved, although it isn't really as this is only a partial and temporary fix.

---

### Post by congminh1709 on 2010-05-05
I don't know the solution to fix the time of boot up, but I recommend you to do this for protecting the system

[http://ohioloco.ubuntuforums.org/showthread.php?t=1305081&page=2](http://ohioloco.ubuntuforums.org/showthread.php?t=1305081&page=2)

I tried this successfully.

---

### Post by a-user on 2010-05-05
i know this tool already, but what do you mean by "protecting the system"?

btw. i also found the solution to speed up boottime again. it is releated to getting plymouth working with my new kernel.
solution one worked for me:
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

and regarding the k10temp... well i dont know why but suddently k10temp shows only 0° everytime. don't know what changed. thus k10temp is still not working reliable.

---

### Post by Pjotr123 on 2010-05-05
Better not use Ubuntu Tweak, but do it like this:
[http://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Hibernate-and-suspend-don-t-always-](http://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Hibernate-and-suspend-don-t-always-)
(number 4)

Ubuntu Tweak is risky:
[http://sites.google.com/site/easylinuxtipsproject/fatalmistakes#TOC-High-danger-level-orange-alert-:-Ub](http://sites.google.com/site/easylinuxtipsproject/fatalmistakes#TOC-High-danger-level-orange-alert-:-Ub)

---

### Post by a-user on 2010-05-05
now i understand what was ment by protecting...
as i described above i now use a selfcompiled kernel 2.6.34. and with that one suspend and hibernate works.

in fact it works also with 2.6.33 and 2.6.31. only with the lucid 2.6.32 it does not work. this must be a kernel bug in 2.6.32 or at least in the ubuntu lucid version of it.

i opened a launchpad bug report for this long time before and i updated it with this informations. but it seems no one of the devs care about this or has time for it. others already posted that they have the same issue.

so, if anybody wants to fix this i can tell them how (or look some post above where i already have given a short explenation).

---

### Post by Pjotr123 on 2010-05-05
> **a-user said:**
> now i understand what was ment by protecting...
as i described above i now use a selfcompiled kernel 2.6.34. and with that one suspend and hibernate works.


Risky business. Lucid has been built and stabilized around 2.6.32. Using another kernel means heavily increasing the chance of instability.

The better solution is either to disable suspend/hibernate, or temporarily switch to another distro that has a newer kernel.

---

### Post by a-user on 2010-05-06
no, disabling suspend/hibernate is NO option!
th better solution (with your logic) would be not using lucid at all and keeping barmic.
edit2: lucid has numerous bugs anyway. there are a bunch of thinks i discovered not working (also before i switched the kernel)
it is probably the worst ubuntu release for a long time.

kernel 2.6.33 is stable and there is only ureadahead and apparmor that is missing if you do it yourself. ureadahead support is easy applied. apparmor i dont find the patches.

but i'm using 2.6.34 without any issues. everything but apparmor is running flawless. that's what i wanted, that's what i now have.

edit: and btw. the new 2.6.32.22 they just released in ubuntu didn't fixed suspend/hibernate

---

### Post by Pjotr123 on 2010-05-06
> **a-user said:**
> 
it is probably the worst ubuntu release for a long time.


No, it's not. Your perception is wrong. When you're an early adopter, you'll run a rather high risk of experiencing bugs. That's the price of early adoption. Has always been so. For every operating system under the sun, including LTS'ses. You should know that.

When you want a (near) flawless experience, you wait a couple of months after the release. The ideal adoption moment for an LTS, for people who want to avoid (nearly) all bugs, is the first point release. Which for Lucid is scheduled in July: [https://launchpad.net/ubuntu/lucid](https://launchpad.net/ubuntu/lucid)

See also this:
[http://www.ubuntu.com/products/ubuntu/release-cycle](http://www.ubuntu.com/products/ubuntu/release-cycle)

---

### Post by a-user on 2010-05-06
i was early adopter for the last two ubuntu releases before lucid and if i compare to them it is the worst.

that's all i said.

---

### Post by sigurnjak on 2010-05-06
I have just updated to a Linux 2.6.34-1-generic kernel and now i my Lucid shots down  completely .  I did not try sleep yet but i like it better already .

---

### Post by a-user on 2010-05-06
if you need help getting ureadahead and plymouth working with that one just pm me.
i now managed to get the full boot speed with my self compiled 2.6.34. and this fixed several problems i had with the official so called stable lucid kernel, that in fact is causing many problems.

---

