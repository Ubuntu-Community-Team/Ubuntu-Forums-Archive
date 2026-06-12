---
title: "New to ubuntu do i need an antivirus? if so what is best?"
date: 2012-06-22
forum: General Help
---

### Post by SRJL on 2012-06-22
Do i need an antivirus? if so which is the best for ubuntu currently? Same question also applies to firewalls :)


Thanks alot for taking the time to help :)

---

### Post by sandyd on 2012-06-22
> **SRJL said:**
> Do i need an antivirus? if so which is the best for ubuntu currently? Same question also applies to firewalls :)


Thanks alot for taking the time to help :)

Generally, no and no. Windows viruses do not run in Ubuntu, and there are currently no viruses that affect Linux in the wild.

Ubuntu has a firewall by default. Some people tweak it using gufw/ufw, but you are secure even without the tweaking.

For more info about security, see [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by 3Miro on 2012-06-22
Ubuntu comes by default with all the defense well set and enabled. You can play with the firewall settings, but unless you are doing something special, I wouldn't mess with it.

There are no programs that look for Linux viruses. The few AV programs for Linux look for Windows viruses and are helpful if you share files between Windows and Linux machines. Linux AV programs contribute nothing to the security of Linux.

---

### Post by larryfroot on 2012-06-22
Anti virus for linux exists mostly on linux servers where the need to coonect windows machines means that anti-virus tools are a necessity. It's nice to show a sense of responibility *if* one is recieving and giving files to windows using friends and colleagues to make sure that you aren't inadvertently passing on infected files to them. After all, a virus can remain attached to a document and going through linux (and not affexting it) isn't going to remove it. Clam AV is a good bet for this purpose, it has a graphical front end, is pretty simple and I really should take a leaf out of my own book and re-install it.

---

### Post by sammiev on 2012-06-22
If you move files and so on from Linux to Windows, I would suggest one then. I use [BitDefender]("https://help.ubuntu.com/community/BitDefender") and it has caught one for me so far and it's free.

---

### Post by firekage on 2012-06-23
> **sandyd said:**
> Generally, no and no. Windows viruses do not run in Ubuntu, and there are currently no viruses that affect Linux in the wild.

But he could work with windows files, windows disk and windows stuff and it is a lot safer to do a full scan on Linux, than risk on windows.

Because i have ntfs disk and use stuff on ntfs disk in order to see them from Windows and Linux i use clamav and avast for Linux - works fine.

---

### Post by HiImTye on 2012-06-23
netfilter is the firewall built into the kernel. it is preconfigured with iptables rules but you can configure it easier in most situations using UFW or the GUI version GUFW (or Firestarter).
[IPTables]("https://help.ubuntu.com/community/IptablesHowTo")
[UFW]("https://help.ubuntu.com/community/UFW")
[GUFW]("https://help.ubuntu.com/community/Gufw")
[Firestarter]("https://help.ubuntu.com/community/Firestarter")

if you are sharing files with windows boxes then you likely want to scan those files for viri that can infect those computers. ClamAV is in the repos but there are other AV solutions available such as Avast! for Linux
[ClamAV]("https://help.ubuntu.com/community/ClamAV")
[Avast!]("http://www.avast.com/linux-home-edition")

you can do other things to secure your Linux box such as use SELinux (if you are feeling adventurous/extra cautious), configure AppArmor or use denyhosts to deny IPs that repeatedly fail connections. there are also some scanners for things that you are less likely to encounter such as rootkits or the like.
[SELinux]("https://wiki.ubuntu.com/SELinux")
[AppArmor]("https://help.ubuntu.com/community/AppArmor")
[SecurityTools]("https://help.ubuntu.com/community/InstallingSecurityTools")

as always you want to keep your browser secure with things such as Ghostery/NoScript, FlashBlock, AdBlockPlus (with EasyList), etc.. to protect yourself from OS independant attacks like XSS or Flash exploitation

---

### Post by 3rdalbum on 2012-06-23
> **SRJL said:**
> Do i need an antivirus? if so which is the best for ubuntu currently?

Ubuntu doesn't run Windows viruses, and there are currently no Ubuntu/Linux viruses. Every couple of years on average there's a fairly amateurish trojan for Linux... but by contrast, there's something like 120,000 new pieces of malware released for Windows every year.

I don't bother to put anti-virus on any of my computers, but if you want to waste your computer's power looking for something that isn't there, go right ahead.

> Same question also applies to firewalls :)

Generally no, for two reasons:

1. A default installation of Ubuntu does not listen for incoming connections. Installing a firewall would be like giving a deaf person a set of earmuffs. Ubuntu will listen for incoming connections if you install something that listens, like a web server - however, even then you probably don't want a firewall, because the only port that's listening would be the web server's port, and if that port is blocked then nothing can access your website and there's no point to running the server if nothing can access it!

2. Most forms of internet connection these days already contain some sort of perfectly-good firewall. ADSL/cable modems and routers do. I think even 3G gateways do too. If all incoming connections are being blocked at the source of your internet connection, you really don't need a firewall at your PC too. An analogy: If your water is turned off at the meter, there's no benefit to turning off your kitchen tap too.


**When should you have a firewall?** If you run server programs for your own learning (i.e. nobody will connect to them outside your own computer) and you occasionally venture outside your home network (for instance, using a 3G dongle or public wifi at a cafe), or your method of internet connection does not have a firewall already, then a PC-based firewall will be of benefit. That's pretty much the only scenario I can think of.

---

### Post by HiImTye on 2012-06-23
> **3rdalbum said:**
> If you run server programs for your own learning
let's not advocate *zero* security especially since most people don't know the difference between a server and a client, after all, Samba is a server and has been known to have security holes. many people run many different types of server software without perhaps even realizing it, such as deluged, samba, or any torrent client. a web browser can also function as a server if properly exploited

the answer is that you can use as much or as little security as you feel comfortable with but you may be exposing yourself to potential threats in the process. you can have a top level security enabled system using SELinux, properly configured firewall settings, etc.. but most people don't generally need to go that far. for most people configuring their firewall and using the proper browser extensions is enough. some people also have windows boxes on their network and scan for windows viri. others feel better covering their server ports with a port knocker or with denyhosts. everyones' needs are different and they vary by both comfort and knowledge level

---

### Post by pbrane on 2012-06-23
> **3Miro said:**
> ...

**There are no programs that look for Linux viruses.** The few AV programs for Linux look for Windows viruses and are helpful if you share files between Windows and Linux machines. Linux AV programs contribute nothing to the security of Linux.

I'm pretty sure f-prot scans for linux viruses as well as all other known viruses, malware, and adware. While there are no know linux viruses in the wild at this time you may want to install a root kit detector such as *rkhunter* or *chrootkit*.

---

### Post by 3Miro on 2012-06-23
> **pbrane said:**
> I'm pretty sure f-prot scans for linux viruses as well as all other known viruses, malware, and adware. While there are no know linux viruses in the wild at this time you may want to install a root kit detector such as *rkhunter* or *chrootkit*.

Security in Linux does not allow for viruses to exist for too long. Every virus attacks a specific vulnerability of the system, when a Linux virus is discovered, then the system is patched and the virus is killed. Nobody in the Linux world would wait for an AV program to catch a virus after it has reached your system and before it can do damage. Relying on AV software is bad security model, in Linux you don't keep your AV updated, you keep your system updated.

As for Rootkit, there is no way for rootkit to get on your system unless you run programs from outside of the trusted repository. Stick to the Software Center and you don't need rootkit detection any more than you need firewall.

---

### Post by pbrane on 2012-06-23
> **3Miro said:**
> Security in Linux does not allow for viruses to exist for too long. Every virus attacks a specific vulnerability of the system, when a Linux virus is discovered, then the system is patched and the virus is killed. Nobody in the Linux world would wait for an AV program to catch a virus after it has reached your system and before it can do damage. Relying on AV software is bad security model, in Linux you don't keep your AV updated, you keep your system updated.

As for Rootkit, there is no way for rootkit to get on your system unless you run programs from outside of the trusted repository. Stick to the Software Center and you don't need rootkit detection any more than you need firewall.

I agree that viruses on linux don't last too long, but new exploits are possible. Once infected, well it's too late. Not all viruses are simply removable. f-prot can detect new and unknown viruses (I assume other AV can as well). While relying on AV software may be a bad security model I disagree that simply keeping your system updated is enough to prevent exploits and attacks. 

Rootkits are not always installed by programs that you install from un-trusted sources. When you browse the web you are vulnerable if you allow java and javascript to run on all websites. Even though most good browsers are "sandboxed" this still remains true.

Just for the record I don't normally use AV software, although I recommend f-prot to those who want to. Linux is very secure. Most exploits are patched quickly. I have been using a GNU/Linux system exclusively since 1998 and have never had any issues related to malware or rootkits. I do run rkhunter and chrootkit though, just because. I have installed and run f-prot occasionally just to check my system if it seems to be running differently, or to check downloaded files but have never found anything.

In short Ubuntu is a very secure OS. There are many different viewpoints on the subject of security, from "no worries" to "you need to install every form of AV, firewall, IDS you can find, everyone is out to get you".

I don't worry too much about it and just check things now and then. Just sayin'.

---

### Post by 3Miro on 2012-06-23
> **pbrane said:**
> I agree that viruses on linux don't last too long, but new exploits are possible. Once infected, well it's too late. Not all viruses are simply removable. f-prot can detect new and unknown viruses (I assume other AV can as well). While relying on AV software may be a bad security model I disagree that simply keeping your system updated is enough to prevent exploits and attacks. 

Rootkits are not always installed by programs that you install from un-trusted sources. When you browse the web you are vulnerable if you allow java and javascript to run on all websites. Even though most good browsers are "sandboxed" this still remains true.


To catch a new virus you need to update the AV definitions, by the time this happens, you can just as well update the part of the system that is vulnerable. For generic attacks, you have SELinux and AppArmor. AppArmor is installed by default on Ubuntu.

For regular home use, if you stick to the Software Center and update often enough, extra software will not make a difference for your security.

---

### Post by sibin xavier on 2012-06-23
No Anti Virus software needed

---

### Post by sakamoto on 2012-06-23
i do not use one but never say never ;)

---

### Post by nipunshakya on 2012-06-23
> **SRJL said:**
> Do i need an antivirus? if so which is the best for ubuntu currently? Same question also applies to firewalls :)


Thanks alot for taking the time to help :)

Hi mate... ubuntu doesn't need an antivirus because it doesn't get affected by viruses... talking about firewalls, you might not need one too coz ubuntu has an inbuilt one within it...
so basically, the machine that runs ubuntu is totally secured and safe...Thats the benefit of ubuntu..


Happy Linuxing

---

### Post by sakamoto on 2012-06-23
nothing should be assumed as fully secure! even not linux!

---

### Post by nipunshakya on 2012-06-23
> **sakamoto said:**
> nothing should be assumed as fully secure! even not linux!
well that depends on how you use your computer... if you intend to crash your system, not even a super computer might survive that.... and if you intend to be a bit careful about ur machine, you can well preserve it until it gets to a museum
Generally, for an average user, ubuntu is secured by the moment it is installed... thats what i have experienced from using it over 2 years....


Happy Linuxing

---

### Post by pbrane on 2012-06-23
> **3Miro said:**
> To catch a new virus you need to update the AV definitions, by the time this happens, you can just as well update the part of the system that is vulnerable. For generic attacks, you have SELinux and AppArmor. AppArmor is installed by default on Ubuntu.

For regular home use, if you stick to the Software Center and update often enough, extra software will not make a difference for your security.

FYI, f-prot updates the virus definitions automatically using a cron job.

In general I agree though.

---

