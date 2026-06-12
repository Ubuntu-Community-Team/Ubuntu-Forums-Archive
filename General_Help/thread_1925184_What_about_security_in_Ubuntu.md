---
title: "What about security in Ubuntu?"
date: 2012-02-14
forum: General Help
---

### Post by Jayhawker on 2012-02-14
I know it is said Linux is much more secure than Windows. But, how does it work? Is there some kind of antivirus? Any system of controlling attacks? I cannot find where the antivirus is. 

PLease, can someone explain it to me?

Thank You

---

### Post by wyliecoyoteuk on 2012-02-14
Linux is much more secure than windows by default.
That said, there are tools you can use for hardening it further.
[firestarter]("https://help.ubuntu.com/community/Firestarter") is a firewall manager
[ClamAV]("https://help.ubuntu.com/community/ClamAV")is antivirus.
If you are sharing files with windows machines, the AV is a good idea.:D

---

### Post by winh8r on 2012-02-14
You will find a lot of very good information here:

[http://ubuntuforums.org/showthread.php?t=1871177]("http://ubuntuforums.org/showthread.php?t=1871177")


and also here:


[http://ubuntuforums.org/showthread.php?t=510812]("http://ubuntuforums.org/showthread.php?t=510812")


The best security tool for any computer is the operator!

---

### Post by haqking on 2012-02-14
> **wyliecoyoteuk said:**
> **Linux is much more secure than windows by default.**
That said, there are tools you can use for hardening it further.
[Firestarter**[/B]"]**firestarter**]("https://help.ubuntu.com/community/**[B) is a firewall manager
[ClamAV]("https://help.ubuntu.com/community/ClamAV")is antivirus.
If you are sharing files with windows machines, the AV is a good idea.:D

Linux is not more secure by default, it is a misconception often spread by people without specialist security knowledge.

You are less likely to encounter virus infection using Linux than windows though, however viruses often have little to do with security in general, there are however no current wild viruses for Linux.

It can suffer from other malware though such as trojans/keyloggers/backdoors etc etc but not as prolific as Windows.

Windows can be hardened by the admin/user to be as secure as any other OS, Linux can be hardened further and weakened easily also if you dont know what you are doing.

All end user OS have a security evaluation of the equal footing around EAL 4.

There is a fine line between security and ease of use and functionality which is why they are all roughly equal due to the target market.

**Firestarter** is a interface which allows you to manage the built in firewall in Linux called netfilter/IPTables and **Firestarter** is a **out of date and buggy project** and not recommended for use anymore. 
This is a guide and discusses the 3 most common ways to enable a firewall in Ubuntu [http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)


To get a better understanding of Security in general i recommend a Wiki we came up with for this purpose at [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

I suggest reading it thoroughly and its links to get a better grip on firewalls (tight inbound and outbound rules), browser security and use of tools such as NoScript, AppArmor and so on.

ENjoy

Cheers

---

### Post by HiImTye on 2012-02-14
Linux is inherently more secure because of the security design of the OS and many security holes have been closed in Ubuntu (for instance, brute forcing 'Root'). Linux doesn't assume you are a superuser, it requires elevation to gain access to those privileges, protecting core system files. also there are many differing flavors of Linux, with unique libraries and compatabilities, *propagating* a virus is more difficult in Linux. that said, anyone can allow escalation if they are not sure what they are doing to insecure items and threats that are cross platform (i.e. web bugs, etc) are not necessarily better protected against using Linux. non-system files are also not protected by the default security model (files that you have default write permissions to). your best bet is to use things like Ghostery/AdBlockPlus/FlashBlock while web browsing and not escalating permissions (entering your system password) for things you do not trust. UFW is a great tool to managing the system firewall but some people prefer firestarter. Im sure there are other options.

antivirus programs for Linux currently mainly only scan for Windows viri, so if you are networking or sharing files with other computers, it is a good idea to have them, but otherwise you may not find much use in them.

---

### Post by perspectoff on 2012-02-14
Trojans are more of a problem than viruses these days anyway. Just have a look at what is happening in Google Android. The question is where your apps are coming from. (This isn't any different an issue than in Windows, Mac, or any other OS, for that matter).

It's a relatively ridiculous notion of security to say that the core OS files can't be changed "due to inherent OS security" but some program can install itself and run happily in the background nevertheless (as part of some package the user actually desired and installed). 

Further, many developers are eschewing official repositories in favour of their own local repositories. That may actually be a good thing, rather than trusting "user" repositories that re-package applications for one distro or another.   

In regards to a firewall, many programs balk at any kind of firewall these days, anyway (since they love to spray traffic through multiple ports in the interest of speed) and Firestarter, though "out of date" (I haven't come across any "bugs") is still, IMO, one that easily allows real-time control (which most of the other firewall GUIs don't do so well, including GUFW, the GUI for UFW). Besides, most trojan programs nowadays use RPC and bypass the firewall anyway (or merely tunnel through any open port).

Further, much malware comes from Flash and Java types of apps, which are downloaded in real-time by websites. A relevant question is "How are these apps jailed in Ubuntu?" (and I don't know the answer).

Monitoring your system's in/out traffic from the net and a list of the running programs (as can be done in System Monitor) is really the best security. 

I use

 lsof -i -n -P

to see which programs are sending traffic, for example.

This is possible to do, but there isn't a single easy-to-use integrated security GUI available, AFAIK, (which would be desirable to have). There is no "magic pill" for security, no matter what you've been sold by Norton or McAfee in the past. There is no security better than a watchful eye. "Do you know where your kids have been?"

---

### Post by haqking on 2012-02-14
> **perspectoff said:**
> 

Firestarter, though "out of date" (I haven't come across any "bugs") 

indeed, its out of date in that it stop being developed like 8 years ago, but that being said it is just an interface for IPTables which hasnt changed much.

As for Buggy, it is more interoperability.  Alot of people when learning the whole Linux firewall thing end up using or playing with firestarter and UFW/GUFW.

These installed together will/can cause conflicts with each other which is the buggy thing most people refer to including me, though there are other bugs on launchpad, but due to its end of development are likely not to be fixed.

Cheers

---

### Post by JKyleOKC on 2012-02-14
> **Jayhawker said:**
> I know it is said Linux is much more secure than Windows. But, how does it work? Is there some kind of antivirus? Any system of controlling attacks? I cannot find where the antivirus is.You've had a number of answers that might seem to be a bit contradictory, but all of them are only parts of the total picture. There's no specific anti-virus as such for Linux, because there's no known virus for it free in the wild. The few av programs that are available for Linux all target Windows viruses, which won't execute on a Linux system because it doesn't recognize Windows system calls.

Of course, if you install WINE to run Windows programs, then you do need an AV that can detect Windows viruses. Those of us who are concerned with system security avoid this situation, however.

There's a part of the kernel called "netfilter" that is controlled via the "iptables" program, and the various firewalls such as FireStarter, UFW, and GUFW are simply interfaces to iptables. This is the primary method for controlling attacks. However it's not really necessary for an out-of-the-box installation since no ports are open for unsolicited incoming traffic until you install one or more servers. The major security threats for most home Linux systems are Email and web browsers, both of which are used to bypass the built-in security features. The best protection against these threats is simply to be aware of them, and to be cautious about your actions!

---

### Post by haqking on 2012-02-14
> **JKyleOKC said:**
> You've had a number of answers that might seem to be a bit contradictory, but all of them are only parts of the total picture. There's no specific anti-virus as such for Linux, because there's no known virus for it free in the wild. The few av programs that are available for Linux all target Windows viruses, which won't execute on a Linux system because it doesn't recognize Windows system calls.

Of course, if you install WINE to run Windows programs, then you do need an AV that can detect Windows viruses. Those of us who are concerned with system security avoid this situation, however.

There's a part of the kernel called "netfilter" that is controlled via the "iptables" program, and the various firewalls such as FireStarter, UFW, and GUFW are simply interfaces to iptables. This is the primary method for controlling attacks. **However it's not really necessary for an out-of-the-box installation since no ports are open for unsolicited incoming traffic until you install one or more servers**. The major security threats for most home Linux systems are Email and web browsers, both of which are used to bypass the built-in security features. The best protection against these threats is simply to be aware of them, and to be cautious about your actions!

A firewall is not just about incoming (and open ports) it is also about controlling outbound traffic.

Such as reverse connections or application exploitation where a arbitrary port is used

Everything else i agree with, well i hope so as i said it all above as well ;-)

peace

---

### Post by JKyleOKC on 2012-02-14
> **haqking said:**
> A firewall is not just about incoming (and open ports) it is also about controlling outbound traffic.Agreed, and in fact the very first time I encountered a real virus attack (back when using Win95) it was my firewall's questioning of its "phone home" message that alerted me to its presence. However if one blocks all outbound traffic, then Email and web browsing can't communicate -- and since most baddies these days operate by piggybacking mail or web connections, blocking all other ports is pretty much a waste of effort.

The only completely secure computer would be one that has absolutely no means of input or output, and is powered down. Unfortunately, such a machine would also be totally useless except as a doorstop or paperweight. In practice, security is always a compromise involving risk management and careful decisions. It's an ongoing process, not a set-and-forget program. And it's always less than perfect...

Hardening techniques such as AppArmor can help protect, but can also create confusion if applied without full understanding. To me, the best compromise involves keeping my systems up to date with security fixes, closing all ports (both inbound and outbound) except those necessary for my specific operations, and taking care not to follow unknown links or open unknown attachments.

---

