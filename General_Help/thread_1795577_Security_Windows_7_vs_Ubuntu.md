---
title: "Security: Windows 7 vs Ubuntu"
date: 2011-07-02
forum: General Help
---

### Post by carmenat250 on 2011-07-02
Ubuntu may have been better then XP for security, but would it be safe to say that Ubuntu is on par with Vista/Windows 7 when it comes to security?

With the last two Microsoft OS, they have taken a page from Linux in that both require users to enter an admin password to make any system changes.

---

### Post by oldsoundguy on 2011-07-02
> **carmenat250 said:**
> Ubuntu may have been better then XP for security, but would it be safe to say that Ubuntu is on par with Vista/Windows 7 when it comes to security?

With the last two Microsoft OS, they have taken a page from Linux in that both require users to enter an admin password to make any system changes.

Windows still uses .exe files.

Comparing: ANY form of Linux is MUCH more secure than any form of Windows.  In Windows you can still install crap with a click .. in Linux .. takes a couple of serious steps .. and the stuff has to EXIST.  NOTHING in the wild at present for Linux. Nearly 2 MILLION items in the wild for Windows.

So NO, not safe to say that Ubuntu is on a par with Windows whatever .. it is WAY ahead.

---

### Post by Dangertux on 2011-07-02
> **carmenat250 said:**
> Ubuntu may have been better then XP for security, but would it be safe to say that Ubuntu is on par with Vista/Windows 7 when it comes to security?

With the last two Microsoft OS, they have taken a page from Linux in that both require users to enter an admin password to make any system changes.

In my opinion to make this any sort of fair on Microsoft you need to forget Vista ever happened. So for the sake of debate let's take Windows 7 vs Ubuntu 10.04 LTS (since both would be considered current stable releases).  We're going to assume for desktop purposes, since Windows 7 is not designed to be a server OS. 

First, while UAC does try to emulate the functionality of it's linux sudo counterpart , it is very different. Mainly in the terms that UAC is bypassed extremely easily. Research the various Windows 7 runas command vulnerabilities if you are interested in that.  While I am not saying that sudo is perfect, or uncompromisable, it just has had more room to grow then UAC. Also the fact that for some odd reason years after Vista has come out Windows developers still regularly refuse to support UAC lends to its problems.

Let's also look at other aspects of user authentication between the two operating systems , since it directly correlates to the level of security of the machine. For some odd reason Microsoft is still clinging on to slightly deprecated methods for hashing passwords, resulting in a very short recovery time for passwords. (Usually less then 10 minutes using Rainbow Crack GPU , and assuming the tables are pregenerated)

Ubuntu does a little better in this aspect, one by allow users to choose different hashing methods more easily as well as using a stronger hashing algorithm by default.

It is also very easy to get caught up in service security when it comes to the two platforms as well. By default, they both actually are not running anything too crazy. However, for some reason Windows filesharing likes to creep out and peek it's head out from under the covers. It just seems inevitable. In the past Windows Firewall was laughable, and while still not as fully featured as iptables MS is definitely going in the right direction. Especially with the Microsoft Security Essentials suite.  

I could go on with this comparison for days, however the most important thing to note in the argument is not which operating system is actually more secure. But, which operating system is more targeted. No matter how hardened you make something , someone will eventually break it, the more someone's you have looking at it the faster it will be broken. Linux is by and large ignored (although this is changing) by malware developers, and more often then not ignored for exploitation in a desktop environment. The reason being, the vast majority of attacks are designed to be quick and efficient, you can exploit dozens of vulnerable Windows machines in the time it takes to even FIND one Linux machine which will likely not even be vulnerable to the desired exploit. 

Again -- the bigger target is more likely to get hit , more often.

> 
Windows still uses .exe files.

Comparing: ANY form of Linux is MUCH more secure than any form of  Windows.  In Windows you can still install crap with a click .. in Linux  .. takes a couple of serious steps .. and the stuff has to EXIST.   NOTHING in the wild at present for Linux. Nearly 2 MILLION items in the  wild for Windows.

So NO, not safe to say that Ubuntu is on a par with Windows whatever .. it is WAY ahead.


I don't agree with this. 

.exe files are just another type of compiled binary. The extension makes little to no difference in terms of if it is exploitable. The care given when the code was written is where that comes in. Also factoring in implementation of such things as DEP and ASLR

Also I disagree with the "in the wild" statement. That tends to get thrown around a lot. It's a nice figure but isn't really relevant when calculating risk vs an APT.

Another area I meant to discuss originally in my post was virtualization.

IMO Windows handles Virtualization very poorly, in an attempt to create a little bit better backwards compatibility with older versions of Windows , Windows 7 / Vista virtualization techniques have lent to their fair share of exploitation.

Also the option to disable DEP and the fact that ASLR is not used by default in some Windows 7 installations (yes apparently security features should be something you pay more for in the Windows world). Makes me question the overall security of the OS.

---

