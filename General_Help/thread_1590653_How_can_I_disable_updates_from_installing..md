---
title: "How can I disable updates from installing."
date: 2010-10-08
forum: General Help
---

### Post by rmjohnson144 on 2010-10-08
I have been installing Ubuntu on my friend's and family's computers.  I keep getting phone calls on Ubuntu won't start.  Update keeps breaking things.

I want to know if there is a way to at least disable the auto update option or disable it completely.

---

### Post by TNT1 on 2010-10-08
Administration/Update Manager/ Settings Button. un-check the check for updates box. It will never look for updates then, but you really need to update the system every couple of weeks/once a month for security reasons.

---

### Post by coffeecat on 2010-10-08
> **rmjohnson144 said:**
> Update keeps breaking things.

"Keeps" breaking things? I recall a seriously bad update in 2006, but apart from that I can only remember  the very occasional minor niggle from updates and nothing I would call a breakage. That's with every version of Ubuntu since Dapper and on several different machines. I know that with *some* hardware there have been problems with *some* updates, but if this is a persistent issue I would look elsewhere for the cause of the breakages.

Have you, by any chance, enabled either the backports or proposed repositories?

---

### Post by lotharmat on 2010-10-08
The only updates that have borked my system recently were the SAMBA ones - I had to keep resetting the sticky bit for mount.cifs and umount.cifs.

---

### Post by linux-hack on 2010-10-08
try may be a more stable system like Debian or Arch Linux .

---

### Post by ivarn on 2010-10-08
I am a very new user of ubuntu but haven't got any update problems yet even with the 3rd party (unsupported) updates enabled which is a risk to take. And since this thing happened on 2 PCs, maybe (just maybe) you have done something wrong.?

---

### Post by WorMzy on 2010-10-08
Have you been installing Ubuntu inside Windows (Wubi)? Wubi installations don't work well with kernel updates, which is probably what's going wrong.

Wubi isn't designed for long term usage, it's just a way of trying Ubuntu out. If they've liked what they've seen so far, install it to a partition for them; that way they can have an up-to-date system without having to worry about being dumped to a grub rescue screen.

---

### Post by rmjohnson144 on 2010-10-08
There are only two issues.  One being a new kernel update that affect the ATI driver updates and the other when a new Ubuntu is released it borks the whole system and usually reinstall with the new version for simplicity reasons.

---

### Post by bodhi.zazen on 2010-10-08
> **linux-hack said:**
> try may be a more stable system like Debian or Arch Linux .

I would list Debian stable or Centos.

Arch is not all *that* stable, it is rolling release, and if you have a problem it is difficult to roll a change back.

Don't get me wrong, I like Arch, but I do not see it a "stable" as the other two distros.

@rmjohnson144 - I agree, disabling updates does not sound like the best option, updated include security patches. 

A better question is what is broken and how to fix the underlying problem.

---

