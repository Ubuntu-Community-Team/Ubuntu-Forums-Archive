---
title: "Argh! PHP... Where??"
date: 2006-02-15
forum: General Help
---

### Post by petbo2 on 2006-02-15
Hello!
As you may be able to tell with the title to my post, I'm having problems installing PHP...  I have managed to install Apache no problem, but I simply can't find PHP in the funky auto-installer program.  Also, when I try 

```
$ sudo apt-get install php4
```

it says it can't find that package!!  It would be pukker if someone could tell me what I'm doing wrong - I've got version 5.1 which the lovely people at Ubuntu sent me, so there shouldn't be any corrupt package issues or nothing!!

Thanks in advance!

---

### Post by LordBug on 2006-02-15
Check Synaptic yet?  I know PHP4 and PHP5 are in there.  I *think* they're in the main repositories.  If not, add the extra ones in.

I don't know the full package names for apt-get usage, unfortunately.

---

### Post by petbo2 on 2006-02-15
Thanks for the quick reply.

I initially tried using Synaptic.  When it wasn't there, I tried from the command line.  Alas, nowt works.  I have been looking around the forum, and it seems I'm the only one with this problem.  Either I'm being incredibly stupid, or no one else has tried to install PHP yet (unlikely).

You mention adding extra repositories.  How does one do that??

Thanks

---

### Post by sbassett on 2006-02-15
[QUOTE=petbo2]Thanks for the quick reply.

I initially tried using Synaptic.  When it wasn't there, I tried from the command line.  Alas, nowt works.  I have been looking around the forum, and it seems I'm the only one with this problem.  Either I'm being incredibly stupid, or no one else has tried to install PHP yet (unlikely).

You mention adding extra repositories.  How does one do that??

Thanks[/QUOTE]

Easiest way to add the extra repos would be open up Synatptic, then select settings-> repositories. Then select add. This will give you the option of adding the multiverse, universe and restricted. Then it will reload your repositories, then search for PHP again. It should be in there. As a matter of fact, it should have a boatload of php related software.

---

### Post by LanceM on 2006-02-15
PHP4 is in World Wide Web (Universe) in Synaptic, PHP5 is, I believe, in the main World Wide Web section.

---

### Post by wrtrdood on 2006-02-15
Sometimes the package names are not very intuitive or there's a lot more of them than you realize.  A good first start is to use something like *apt-cache search <packagename>* where <packagename> is all or part of a name you think should be in the repository.  For example, there's a lot of additional stuff for PHP and you may find you'll need those packages as well.

---

