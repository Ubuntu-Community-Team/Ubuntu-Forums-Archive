---
title: "Can Kubuntu and Mandriva 2006 share a common /home partition?"
date: 2006-06-25
forum: General Help
---

### Post by mibadt on 2006-06-25
Hi,
I'm a veteran Mandriva user.
Recently I tried Kubuntu 6.0.6 and I'm very impressed.
Initially, I've installed Kubuntu with it's separate /home partition.
As I plan to continue using Kubuntu, in the interim period **together with Mandriva 2006**, I'd rather share my (substantially larger) Mandriva /home partition (ReiserFS 3.6) with Kubuntu 6.0.6..
My Mandriva's /home is a separate partition and both OSs have the same users (each one with same PW).

Two issues that nother me:
a. I'm not sure whether both OSs define identical groups as well.
b. Mandriva uses KDE 3.4 whereas Kubuntu-3.5.2

1. Can I safely share hat /home partition? Namely, will I be able to reuse it afterwards from **both** OSs?
2. If Y, Do I have to make any changes (beside obvious fstab editing)?

TIA;)

---

### Post by BoneKracker on 2006-06-25
Ubuntu is based on Debian.  Is Mandriva?  If not, I wouldn't even consider it.

Even if it is, I would not recommend trying this.  Too many things store configuration files in your home directory.

What you might do is leave the two distros with their own home directory, but create a shared partition that you actually USE as though it were your home directory.  In other words assign it the same permissions and put all your personal files there.

But I'd leave the configuration files alone.

---

### Post by mibadt on 2006-06-25
Mandriva is a Red Hat derivative (not Debian).
I don't have free space on my HD for a shared partition.

:p 

[QUOTE=BoneKracker]Ubuntu is based on Debian.  Is Mandriva?  If not, I wouldn't even consider it.

Even if it is, I would not recommend trying this.  Too many things store configuration files in your home directory.

What you might do is leave the two distros with their own home directory, but create a shared partition that you actually USE as though it were your home directory.  In other words assign it the same permissions and put all your personal files there.

But I'd leave the configuration files alone.[/QUOTE]

---

### Post by vigleik on 2006-06-25
Don't do it! The config files in your home directory will mess everything up. What you can do (without making more partitions) is keep the Ubuntu home on / and make links to the Mandriva home partition. If you make a link to each of the non-hidden directories in your Mandriva home (just drag them from one konqueror window to another and choose link when it asks you) then it'll be almost as sharing the home partition.

Vigleik

---

### Post by darkhatter on 2006-06-25
yes you can do it, and it will most likely work pain-free, but you may run into conf. errors, cause of different program versions. Linux is Linux, doesn't matter what its based on

---

### Post by mibadt on 2006-06-25
Thanks all :D 

Vigleik's links idea seems the practical, safe and elegant solution.
I'll give it a try.

mibadt

[QUOTE=darkhatter]yes you can do it, and it will most likely work pain-free, but you may run into conf. errors, cause of different program versions. Linux is Linux, doesn't matter what its based on[/QUOTE]

---

### Post by BoneKracker on 2006-06-26
I agree.  If you're space-limited that's the way to go.

---

