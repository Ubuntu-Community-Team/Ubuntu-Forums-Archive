---
title: "I still dont understand what SElinux/apparmor is..."
date: 2009-12-08
forum: General Help
---

### Post by Cytochromec on 2009-12-08
I need an idiot proof definition of what Security Enhanced Linux is. I have read several paragraphs including the wikipedia entry and all I can understand is that its developed by the NSA and provides government style security by applying restrictions, yet people describe it as not having an effect on day to day usage. I know Fedora uses it but before I give that distro a try I thought I would enquire here. Whats the point of selinux for the non-server/non-goverment crony  and how does apparmor differ? Also, is app armor installed natively into ubuntu? Thanks.

---

### Post by Sam on 2009-12-08
Well, in short, this add an extra layer of security next to the traditional permissions. You can set rules for applications to tighten the security. Read [this](http://serverfault.com/questions/61558/real-life-selinux-security-example).

---

### Post by iponeverything on 2009-12-08
> I need an idiot proof definition of what Security Enhanced Linux is. 

There really is no simple answer to this, selinux is some very complex extensions to linux --

In short it provides a cross platform, kernel level security policy enforcement mechanism. Linux is widely used in NASA, JPL and many places. UNIX was designed primary with easy collaboration in mind, this still makes it ideal for research -- but for use with sensitive data, it needed a network wide, low level security policy enforcement mechanism -- SELinux provides this.

Apparmor makes more sense for Linux systems that are not part of LAN, and don't require complex security policies.

---

### Post by Cytochromec on 2009-12-09
So should one consider switching over to Fedora over this? Even if Ubuntu is secure, I would make the switch if Fedora was even more secure.

---

### Post by EarlW on 2009-12-27
> **Cytochromec said:**
> So should one consider switching over to Fedora over this? Even if Ubuntu is secure, I would make the switch if Fedora was even more secure.
I was able to install SELinux on Ubuntu 9.10 (32-bit).  It uninstalled AppArmor in the process.  Once I set it to be enforcing, and rebooted, the system started to get unstable and slow.  Only did this a few hours ago and haven't spent much time solving it.

So I would say SELinux can work with Ubuntu, but you will spend more time and effort on it than Fedora or CentOS, because those systems have really done a good job of making SELinux work well.

---

### Post by jmcgovern on 2009-12-27
In mhy (albeit limited) experience, SELinux is an easy way to get yourself locked out of your own system, unless you know EXACTLY what you're doing.  AppArmor has been much easier to use and at least 'feels' just as secure.   Also, as EarlW pointed out, AppArmor works better on Ubuntu.  By all means try SELinux if you want to, but make sure you read up on exactly how it's used/configured because at least in the past I've known many people who've hosed themselves using it.

---

### Post by 3rdalbum on 2009-12-27
I'll try and explain what SELinux and AppArmour do.

Normally, when you run a program, that program can do everything that your user account can do - it can unmount disks, open other programs, connect to other computers or even delete the contents of your home directory.

Normally this isn't a problem, because the program won't perform those actions. However, if the program gets taken over by an attacker, the program CAN be ordered to do those things.

AppArmour works at the kernel level to define what a program can and can't do, and it will stop a program from being able to do anything that it doesn't need to do. So, for instance with Evince PDF Reader, all it does is read files from your hard disk, access the printing system, and display a window. So AppArmour will let it do those things, but not let it do anything else. If somebody finds a vulnerability in Evince that allows it to be taken over by a remote attacker, that attacker still can't run other programs, delete data or connect to other computers.

---

