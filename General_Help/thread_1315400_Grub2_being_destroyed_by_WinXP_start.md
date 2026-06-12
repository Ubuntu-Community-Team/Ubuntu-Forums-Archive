---
title: "Grub2 being destroyed by WinXP start"
date: 2009-11-05
forum: General Help
---

### Post by teel on 2009-11-05
Hi,
I upgraded my laptop with Ubuntu 9.10 and was very surprised to notice that every time I run WinXP (by selecting it in the Grub2 list) the Grub2 installation gets corrupted (gets stuck at "Grub starting.").
To recover I have to run LiveCD, mount sda, make grub-reinstall and it works ok until I start WinXp once again.

I wonder how should I start debugging this issue. Anyone seen similar stuff before?

Best Regards,
el Tomek

---

### Post by lnxnoob on 2009-11-05
I had/have the same thing except if you leave it for awhile it does eventually load Grub, its just slow as hell.Havent managed to resolve it though.

---

### Post by teel on 2009-11-05
I guess it is somehow altered by WinXP, no clue how and why. Maybe it's identified as a virus in MBR? Next time I'll terminate WinXP starting and don't allow anything load, especially anti-virus SW.
What does `grub-install' repair so that it loads properly until next time WinXP ran?

---

### Post by sliketymo on 2009-11-05
By using the forum search tool you can find many good tutorials relating to dual-booting and on grub2.Here is a good starting point:

[http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743)

---

### Post by berman56 on 2009-11-05
Do you happen to have an HP computer with protecttools or another computer with a similar nasty habit of adjusting the MBR each boot?

Check out:

[http://ubuntuforums.org/showthread.php?t=1307042](http://ubuntuforums.org/showthread.php?t=1307042)

and

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)

---

### Post by dcstar on 2009-11-05
> **berman56 said:**
> Do you happen to have an HP computer with protecttools or another computer with a similar nasty habit of adjusting the MBR each boot?
........

And there are various other Windows programs that detect when the MBR has been "corrupted" and then try to fix it be rewriting a saved copy.

You need to find out what MBR/Boot Sector "protection" is on your Windows system and disable it.

---

### Post by wilee-nilee on 2009-11-05
> **teel said:**
> I guess it is somehow altered by WinXP, no clue how and why. Maybe it's identified as a virus in MBR? Next time I'll terminate WinXP starting and don't allow anything load, especially anti-virus SW.
What does `grub-install' repair so that it loads properly until next time WinXP ran?

I would be careful about any other then regular shut-down of any MS OS these OS are not as forgiving as the Linux one is.

---

### Post by teel on 2009-11-06
> **berman56 said:**
> Do you happen to have an HP computer with protecttools or another computer with a similar nasty habit of adjusting the MBR each boot?

Check out:

[http://ubuntuforums.org/showthread.php?t=1307042](http://ubuntuforums.org/showthread.php?t=1307042)

and

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)

Thanks, that will solve my problem!

Best Regards,
Tomek

---

### Post by teel on 2009-11-06
> **teel said:**
> Thanks, that will solve my problem!

Best Regards,
Tomek

Unfortunately it dod not :( Uninstalled every HP application (except QuickLaunch and Wireless assistant which I think are neutral) and have the same problem.

---

### Post by windowless on 2009-11-06
I had a similar problem and it turned out to be a bad ntfs file system.I think I ran chdsk -f
and that fixed it probably not your problem but interesting

---

### Post by berman56 on 2009-11-06
> **teel said:**
> Unfortunately it dod not :( Uninstalled every HP application (except QuickLaunch and Wireless assistant which I think are neutral) and have the same problem.

After you uninstalled the HP software (and recovery partition?) did you then perform a clean installation of Ubuntu with the format partition box checked?

---

### Post by teel on 2009-11-08
> **berman56 said:**
> After you uninstalled the HP software (and recovery partition?) did you then perform a clean installation of Ubuntu with the format partition box checked?

No, after I uninstalled HP software, I ran a LiveCD, made grub-install and it fixed the GRUB, until the next running of WinXP :(

---

### Post by teel on 2009-11-08
Ok, just did further investigation: neither the MBR nor boot sectors of the partitions get altered! Now I have no idea what WinXP does to GRUB, initially I supposed MBR is being overwritten, it is not :(

I found the reason, goto: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941/comments/17](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941/comments/17)

---

### Post by berman56 on 2009-11-08
> **teel said:**
> Ok, just did further investigation: neither the MBR nor boot sectors of the partitions get altered! Now I have no idea what WinXP does to GRUB, initially I supposed MBR is being overwritten, it is not :(

I found the reason, goto: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941/comments/17](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941/comments/17)

Teel, I'm confused.  I thought you said in your previous post that you uninstalled HP Protecttools without success.  But hpqwmiex.exe is a process associated with Protecttools.  In any event, it appears that you too have confirmed that Protecttools is the culprit.

---

### Post by teel on 2009-11-09
> **berman56 said:**
> Teel, I'm confused.  I thought you said in your previous post that you uninstalled HP Protecttools without success.  But hpqwmiex.exe is a process associated with Protecttools.  In any event, it appears that you too have confirmed that Protecttools is the culprit.

I did uninstall every HP application except Wireless Assistant and Quick Buttons (or sth like that), especially uninstalled ProtectTools but the service hpqwmiex.exe remained installed.

---

### Post by berman56 on 2009-11-15
Looks like this problem is due to more than one application / service / credential manager that writes to the MBR each boot (i.e. Protecttools, HP backup - PC Angel, etc.).  It seems to be particularly a problem with HP but a Dell user has also reported the same problem.

This has been just been elevated to "confirmed" status on launchpad:

[http://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](http://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)

Great job community!! =D>

---

