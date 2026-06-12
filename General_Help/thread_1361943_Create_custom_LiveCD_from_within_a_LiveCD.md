---
title: "Create custom LiveCD from within a LiveCD?"
date: 2009-12-22
forum: General Help
---

### Post by sd_smoker on 2009-12-22
I realize this is a longshot, but would it be possible to create and burn a custom LiveCD from within an instance of a LiveCD using remastersys?

---

### Post by starcraft.man on 2009-12-22
> **sd_smoker said:**
> I realize this is a longshot, but would it be possible to create and burn a custom LiveCD from within an instance of a LiveCD using remastersys?

You need a second CD/DVD tray, as far as I'm aware, you can't remove the live CD from running. If ya used a usb boot up, then that might work. There's nothing preventing you from doing anything with a live CD instance of Ubuntu, so long as you don't reboot (everything caches to RAM). Hope that's clear.

---

### Post by sd_smoker on 2009-12-22
Hmm, okay. I was hoping I might be able to save the iso to a network folder. 

At this point I can't even get remastersys to install. Here's what I'm getting:

```
ubuntu@ubuntu:~$ sudo apt-get install remastersys
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  remastersys: Depends: dialog but it is not installable
               Depends: discover1 but it is not installable or
                        discover but it is not installable
               Depends: xresprobe but it is not installable
E: Broken packages
```

Any ideas?

---

### Post by nerdopolis on 2009-12-22
try sudo aptitude install remastersys

Aptitude is usualy more helpful then apt-get when it comes to unresolvable dependencies

---

