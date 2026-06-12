---
title: "Ubuntu 10.10 Hibernation issues...."
date: 2010-10-19
forum: General Help
---

### Post by garuda10 on 2010-10-19
Hi All,
   Similar threads have been often posted but then I was unable to find a solution to my problem following those threads. I've just upgraded ubuntu to the latest version {10.10}. My Ram is 3GB and swap memory is 8GB. So, I guess that is not the issue. I run ubuntu on a HP pavilion dv6t and whenever I put it to hibernation there is "_" that keeps on blinking and it refuses to go into hibernation. If I try to close the lid of my laptop, it would not hibernate. Not only hibernation is an issue but also at times shutting the system down takes really long time. Can someone advise me what to do. Thanks.

---

### Post by garuda10 on 2010-10-20
Also, if it helps, today I've noticed that my hibernation says that ubuntu had to force "render head to zero" and I have absolutely no idea what it means...

---

### Post by Langsdorf on 2010-10-21
yeah, same problem here with lenovo g560. everything worked before and after upgrade it (usually) just blinks endless

nvidia g310m, 2gb ram (5gb swap), i3 core

any ideas?

---

### Post by garuda10 on 2010-10-24
Anyone out there with at least a hint of solution? this thing is really irritating and I never faced a problem with ubuntu till I upgraded to Maverick....

---

### Post by XMica on 2010-10-26
Hi I've got the same issue after having upgraded from 10.04 to 10.10 (i686) on a Dell latitude E6410 with Nvidia NVS 3100M card.
Hibernate does not work at all (blinking cursor as well) and I have to power off.
Just after the upgrade to 10.10 I also faced an issue while going to  standby but it has been fixed by adding "acpi_sleep=nonvs" to grub  (GRUB_CMDLINE_LINUX).
However hibernate issue is still there.
According to some other posts it could be related to the nvidia driver, what kind of video card do you have ?
Michael

---

### Post by Langsdorf on 2010-10-27
ok, it works for me (at least it worked 5 hibernate tests) with this solution: [http://tgpo.org/?p=345](http://tgpo.org/?p=345)

basically edit
```
/etc/default/acpi-support
``` and search for SUSPEND_METHODS. set "hibernate" as first entry ```
SUSPEND_METHODS=”hibernate dbus-pm dbus-hal pm-utils”
``` and restart :guitar:

---

### Post by netipot on 2010-10-27
My issue is really with suspend. 10.04 worked beautifully when I closed the lid on my T60. I had it set in power management to suspend and no problem but with upgrade to 10.10 it would show an error message upon wake up. No way around it but to unplug my thinkpad T60 and remove the battery and reboot. I reset it to hibernate instead and there is no problem now except suspend is easier and faster and I miss that. I also had a problem with opening docs or pictures or almost anything in nautilus except my computer & trash, when I did, it opened f-spot to import.  I unistalled f-spot and all is fine now except I do miss f-spot :(. I do love ubuntu and will never go back to windows. All this messing around has made me a better computer user and windows never lets you do anything.

---

### Post by garuda10 on 2010-10-27
> **Langsdorf said:**
> ok, it works for me (at least it worked 5 hibernate tests) with this solution: [http://tgpo.org/?p=345](http://tgpo.org/?p=345)

basically edit
```
/etc/default/acpi-support
``` and search for SUSPEND_METHODS. set "hibernate" as first entry ```
SUSPEND_METHODS=”hibernate dbus-pm dbus-hal pm-utils”
``` and restart :guitar:

I tried the above method... But the problem seems to be with the kernel update that we had few weeks ago. Usually when I click hibernate, it is a silent process. But off late, there is an error which goes something like this "Error render head not set to zero" and there are two lines... Anyone knows how to work around this?

---

### Post by garuda10 on 2010-10-28
Bump

---

### Post by greenprell on 2010-10-31
> **Langsdorf said:**
> ok, it works for me (at least it worked 5 hibernate tests) with this solution: [http://tgpo.org/?p=345](http://tgpo.org/?p=345)

basically edit
```
/etc/default/acpi-support
``` and search for SUSPEND_METHODS. set "hibernate" as first entry ```
SUSPEND_METHODS=”hibernate dbus-pm dbus-hal pm-utils”
``` and restart :guitar:

This did not work for me.

I have an Asus G73JW-A1 laptop, and when I try to go into Suspend mode (either by closing the lid or clicking Suspend in the top-right menu), I just get a blinking cursor. I can get to the other ttys by hitting Alt+F[1-6], but I can't type into any of them.

---

### Post by greenprell on 2010-11-01
Looking at [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/653843"), it seems like some people are having success installing a new - mainline - kernel. I have not had this success. The behavior is different, but still not what is expected.

---

### Post by Langsdorf on 2010-11-01
as my "fix" apparently didn't work (despite my previous post), i was able to fix the hibernate issue by installing a new kernel 2.6.35-23 (instead of...-22)

[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=10038853&postcount=30](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=10038853&postcount=30)

---

### Post by XMica on 2010-11-03
I confirm that kernel 2.6.35-23-generic fixed this issue on my laptop.:P
Thank you !

---

### Post by garuda10 on 2010-11-04
Unfortunately, even this does not solve my issue... I added those lines and then went into update manager installed the new kernel, restarted, deleted the old kernel and still the problem persists :(... Is there something I am missing? Thanks

---

### Post by garuda10 on 2010-11-09
I dont know what went right, or wrong... But all of a sudden my ubuntu goes into hibernation perfectly... But when it is coming out of hibernation I still get those two lines saying "Render ring head not set to zero" and "render ring head forced to zero"

---

### Post by bobstay on 2010-11-26
My hibernate didn't work until I found _**[this post]("http://ubuntuforums.org/showthread.php?p=10112888")**_ - it appears someone has forgotten to install the "hibernate" package by default in 10.10 ](*,)

I installed it, and my hiberante now works perfectly.

---

### Post by SecretCode on 2010-11-26
The package called "hibernate" is not installed on my system, but I can hibernate. It's not a requirement.

Glad it helped you, though!

---

