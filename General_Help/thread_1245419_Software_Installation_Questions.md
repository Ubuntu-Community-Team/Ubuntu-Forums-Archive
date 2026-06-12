---
title: "Software Installation Questions"
date: 2009-08-20
forum: General Help
---

### Post by Jimoid on 2009-08-20
Dear Gurus,

I would like to know a bit more about permissions in Linux. As I understand it to change system files (those in /etc/ or /var/ for example) you need root privileges. As a normal user on a system however, I have full control over files under /home/username/ .

From experience I know that if I want my, say, default python version to be higher than that installed on the system, I can install whichever python version I want under my home directory, then prepend that directory in my .bashrc path, source it, and I bypass the system's python version.

I must be missing something, and hence asking the question here. Installing a new kernel under your home directory wouldn't work, but what stops lots of other bits and pieces being installed under your own directory? Am I right in thinking that as long as the changes only affect you (i.e. not systemwide), I can install any software I need?

Thanks for reading

---

### Post by mcduck on 2009-08-20
> **Jimoid said:**
> Dear Gurus,

I would like to know a bit more about permissions in Linux. As I understand it to change system files (those in /etc/ or /var/ for example) you need root privileges. As a normal user on a system however, I have full control over files under /home/username/ .

From experience I know that if I want my, say, default python version to be higher than that installed on the system, I can install whichever python version I want under my home directory, then prepend that directory in my .bashrc path, source it, and I bypass the system's python version.

I must be missing something, and hence asking the question here. Installing a new kernel under your home directory wouldn't work, but what stops lots of other bits and pieces being installed under your own directory? Am I right in thinking that as long as the changes only affect you (i.e. not systemwide), I can install any software I need?

Thanks for reading

Yes, you are free to do whatever you want inside your own home directory. :)

Of course there are some limits to what things can actually run that way, for example any drivers and such are clearly out of the question. But most of the normal stuff should be able to run from your home directory.

---

### Post by Jimoid on 2009-08-20
Great, thanks for the clarification.

My question was a bit of a generalisation that I wanted the answer to.

More specifically, (I hope these aren't dirty words) I run RHEL clones at work (but Ubuntu at home). I want to install some RPMs via YUM, into my user account only (i.e. not through root) on a machine. Is this possible too? I guess it is the same question replacing RPM with APT-GET, but I'm here to learn.

Cheers

---

