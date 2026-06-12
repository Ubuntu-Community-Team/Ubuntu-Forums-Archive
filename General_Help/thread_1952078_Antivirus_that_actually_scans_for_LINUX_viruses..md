---
title: "Antivirus that actually scans for LINUX viruses."
date: 2012-04-03
forum: General Help
---

### Post by Dugachug on 2012-04-03
I know, people say there aren't any viruses for linux in the wild, but i want to make sure my system is secure. :p Are there any antivirus programs for linux that scan for linux viruses? i hear AVG Avast, and others only scan for windows viruses. Thanks in advance.

---

### Post by PhantomTurtle on 2012-04-03
Have you tried ClamAV? I'm not an expert at this since I do not use an AV on Linux, BUT ClamAV is one of the more popular and open source ones available for Linux. Also see here for more AV software for Linux - [http://www.codefear.com/linux/5-best-free-antivirus-software-for-linux/]("http://www.codefear.com/linux/5-best-free-antivirus-software-for-linux/")

---

### Post by Habitual on 2012-04-03
> **Dugachug said:**
> ...i want to make sure my system is secure....

I commend you.
Just remember Security is a process, not a goal.  :wink:
Check rkhunter in a repo near you, (or should be).

and a good read is [http://serverfault.com/questions/146906/any-security-tips-for-my-first-server-complete-beginner](http://serverfault.com/questions/146906/any-security-tips-for-my-first-server-complete-beginner)

HTH

---

### Post by pbrane on 2012-04-03
You should look into f-prot. It will scan for all viruses, adware, even those it can't ID. There is a free for home use linux version available on their website.

And I second what Habitual pointed out. Root kits are more of a problem than viruses on linux. Currently there are no known viruses in the wild that are a problem for linux. That's not to say that there are no linux viruses, there have been some reported in the past.

---

### Post by 3rdalbum on 2012-04-03
They all scan for Linux viruses, but since none of the viruses work on a modern Linux distro anyway its a bit pointless.

---

### Post by 3Miro on 2012-04-03
"Scanning" for viruses is the wrong way to do security, if a virus can exploit a vulnerability, then the vulnerability should be fixed, not patched by some external program. If you have a hole in the wall of your house, you will fix the hole, not hire a guard to stand there and keep out people that are on the police's list of known criminals.

There is no program to look for Linux viruses, you can have viruses only on a system that is too slow to react to vulnerabilities. Windows and MacOSX are "closed" systems and you have to wait on MS or Apple to react, Linux is "open" so the community can fix the problem at the source rather than release a temporary fixes.

AV software under Windows provided some extra functionality, which under Linux is handled by SELinux or AppArmor (AppArmor is installed by default on Ubuntu).

The default install of Ubuntu is as secure as it gets, just keep your system updated. The biggest vulnerability of your system is you, if you want to improve your security, read up and be careful of your actions.

---

### Post by dcstar on 2012-04-05
> **pbrane said:**
> 
........
That's not to say that there are no Linux viruses, there have been some reported in the past.

Really?, like to cite some - ANY - of them?

I have been in these forums since 4.10 was released and have not seen **one** credible report of a Linux "virus", just pure FUD from people who seem to dig up ancient myths.

---

### Post by bkratz on 2012-04-05
> **dcstar said:**
> Really?, like to cite some - ANY - of them?

I have been in these forums since 4.10 was released and have not seen **one** credible report of a Linux "virus", just pure FUD from people who seem to dig up ancient myths.



Remember this one?  It was related to a screensaver.

[http://lwn.net/Articles/367874/](http://lwn.net/Articles/367874/)

---

### Post by Grenage on 2012-04-05
> **bkratz said:**
> Remember this one?  It was related to a screensaver.

[http://lwn.net/Articles/367874/](http://lwn.net/Articles/367874/)

That's not a virus.

---

### Post by 3rdalbum on 2012-04-05
> **bkratz said:**
> Remember this one?  It was related to a screensaver.

[http://lwn.net/Articles/367874/](http://lwn.net/Articles/367874/)

Not a virus. It's a Trojan horse, and any old idiot can write one.

It also poses no threat to anyone anymore as it used to download the payload from a site that no longer exists.

I haven't come across any honest-to-goodness Linux viruses. Apparently there was one in 2007 but nobody would be able to catch it these days. I only heard about it recently.

---

### Post by Paqman on 2012-04-05
> **dcstar said:**
> Really?, like to cite some - ANY - of them?

I have been in these forums since 4.10 was released and have not seen **one** credible report of a Linux "virus", just pure FUD from people who seem to dig up ancient myths.

[List of Linux viruses](http://en.wikipedia.org/wiki/Linux_malware#Viruses).

I haven't waded through the references, so feel free to cast aspersions on their credibility. All of these were patched out of existence some time around the mesozoic era AFAIK, and at least some were merely proof-of-concept and never actually infected anyone in the wild.

So yes, Linux viruses have been written. They're just software after all, and Linux has got to be the platform of choice for experimenting with unusual code. Is the threat big enough for desktop users to really be worried about it IMO? Hell no.

---

