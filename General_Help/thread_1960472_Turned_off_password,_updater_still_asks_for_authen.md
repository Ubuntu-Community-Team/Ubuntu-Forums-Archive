---
title: "Turned off password, updater still asks for authentication"
date: 2012-04-17
forum: General Help
---

### Post by KristofferAG on 2012-04-17
So, I turned off my password as I was using the computer to play music during a party, and wanted people to be able to get back on if it shut down or went into sleep mode or anything like that.

My issue is that I'm still asked to authenticate whenever I try to run updates, and it asks for a password. I have no idea what password it's asking for, as I haven't used any other passwords than the one I removed on this computer.

Anyone know what's wrong? I'm a complete scrub with Ubuntu, only using it on my laptop as I can't really use any other OS on it.

Thanks

---

### Post by HiImTye on 2012-04-17
you shouldn't be able to remove your password, I'm sure you just made Ubuntu automatically log you in.
try your 'old' password.

Ubuntu will always ask for your password when performing administrative duties (such as modifying the core file system, when you install a new package). Update Manager will not ask for your password, most of the time.

---

### Post by KristofferAG on 2012-04-17
When I check User accounts, under Login Options, it Says Password: None. I've tried using the only password I've ever had on this laptop, or at least since I installed Ubuntu about 2 4 months ago, and it says it's the wrong password. Tried with and without capslock and such.

I am absolutely certain that none of my friends are tech savvy enough to change my password, as none of them use Ubuntu, I'd be surprised if they'd even heard of it. And besides, they'd need my password for it, which I have never given out, so is there any other solution to it? I don't have to reinstall Ubuntu to get a new password or anything, do I?

---

### Post by asuastrophysics on 2012-04-17
> **KristofferAG said:**
> When I check User accounts, under Login Options, it Says Password: None. I've tried using the only password I've ever had on this laptop, or at least since I installed Ubuntu about 2 4 months ago, and it says it's the wrong password. Tried with and without capslock and such.

I am absolutely certain that none of my friends are tech savvy enough to change my password, as none of them use Ubuntu, I'd be surprised if they'd even heard of it. And besides, they'd need my password for it, which I have never given out, so is there any other solution to it? I don't have to reinstall Ubuntu to get a new password or anything, do I?

You may not have actually set an administrative password then. To do so, open a terminal and enter the following:
```
passwd
```
It will ask you to type a password. Re-enter it when it asks. Let me know if this works.

---

### Post by KristofferAG on 2012-04-17
It worked, excellent! It's weird though, I can't remember having done that before, only time I input the password was when I installed it. Either way, thanks a bunch for the help!

---

### Post by asuastrophysics on 2012-04-17
> **KristofferAG said:**
> It worked, excellent! It's weird though, I can't remember having done that before, only time I input the password was when I installed it. Either way, thanks a bunch for the help!

No problem! Glad to hear it's fixed! :popcorn:
To help others who need a solution to this problem, please go to thread tools -> mark as solved. ;)

---

### Post by knoble on 2012-11-26
thanx ey had same prob twz worryng me

---

