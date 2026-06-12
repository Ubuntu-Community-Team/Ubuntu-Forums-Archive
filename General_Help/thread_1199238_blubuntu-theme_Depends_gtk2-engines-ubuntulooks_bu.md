---
title: "blubuntu-theme: Depends: gtk2-engines-ubuntulooks but it is not installable"
date: 2009-06-28
forum: General Help
---

### Post by yang on 2009-06-28
Ever since I upgraded to 9.04 (soon after its release), every time I try to use apt in some way I see this warning:

```

blubuntu-theme: Depends: gtk2-engines-ubuntulooks but it is not installable

```

This is a package that I had installed in the past (probably under 8.10). And thus there's always a lingering non-upgraded package, e.g.:

```

X upgraded, X newly installed, X to remove and 1 not upgraded.

```

(or, in the Update Manager, the Blubuntu package is always listed in the box, but grayed out.

I also tried:

```

$ sudo apt-get install -f
[sudo] password for yang:
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

But it never goes away.  What's going on?  If it makes any difference I'm on x86_64.  Thanks in advance.

---

### Post by yang on 2009-06-29
Also, I'm getting this:

```

$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following packages are BROKEN:
  blubuntu-theme
The following packages will be REMOVED:
  gtk2-engines-ubuntulooks{a}
The following packages will be upgraded:
  human-theme
1 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 44.6kB of archives. After unpacking 81.9kB will be freed.
The following packages have unmet dependencies:
  blubuntu-theme: Depends: gtk2-engines-ubuntulooks but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
human-theme
ubuntu-artwork
ubuntu-desktop

Keep the following packages at their current version:
gtk2-engines-ubuntulooks [0.9.12-12 (jaunty, now)]

Score is 328

Accept this solution? [Y/n/q/?] 

```

---

### Post by oldos2er on 2009-06-29
Do you have the universe repository enabled?

---

### Post by CatKiller on 2009-06-29
Well the problem is that blubuntu-theme depends on gtk2-engines-ubuntulooks, but gtk2-engines-ubuntulooks conflicts with human-theme. Since you aren't using both of them at once, you need to decide whether you want to keep blubuntu-theme or human-theme. Remove the other one and your problem will go away.

---

### Post by yang on 2009-06-29
Ah, thanks for your answers, CatKiller.

First off, how did you determine all this?  Did you simply navigate through the dependencies in aptitude?  Is there an easier way to visualize these dependencies and conflicts and what needs to be removed/installed/etc.?

The naming may have been throwing me off, since in my mind, the Human theme (human-theme) *is* the official look of Ubuntu (gtk2-engines-ubuntulooks).  Or at least, I would've expected human-theme to be *parallel* (a sibling) to blubuntu-theme, as in it would *also* depend on gtk2-engines-ubuntulooks.

Why didn't this happen before / why did these two suddenly start to conflict in 9.04?

I may choose to stick with Blubuntu instead of Human - would removing human-theme cause any problems?

---

### Post by CatKiller on 2009-06-29
> **yang said:**
> First off, how did you determine all this?  Did you simply navigate through the dependencies in aptitude?  Is there an easier way to visualize these dependencies and conflicts and what needs to be removed/installed/etc.?

Well, the fact that your output showed a problem with gtk2-engines-ubuntulooks and wanted to remove human-theme to resolve it was a big clue. A quick *aptitude show human-theme* confirmed it;

> Conflicts: gtk2-engines-ubuntulooks> The naming may have been throwing me off, since in my mind, the Human theme (human-theme) *is* the official look of Ubuntu (gtk2-engines-ubuntulooks).  Or at least, I would've expected human-theme to be *parallel* (a sibling) to blubuntu-theme, as in it would *also* depend on gtk2-engines-ubuntulooks.Yeah, I don't know why that's happened; specifically that human-theme conflicts with gtk2-engines-ubuntulooks. It seems like the kind of thing that's just an oversight and would be corrected quickly, but I guess there must be a proper reason for it since it's stayed that way for quite some time now.

I just checked on Launchpad, and it seems that it was deliberately specified on 9/9/2008. The changelog doesn't say why.

> 
I may choose to stick with Blubuntu instead of Human - would removing human-theme cause any problems?You'll lose the ubuntu-desktop metapackage, since that depends on human-theme. That's not really anything to worry about though, it's just a list of software that should be included in a default install. You might want to put it back before you dist-upgrade to the next version, that's all.

You'll also lose the ubuntu-artwork package. I'm not entirely sure what ramifications that would have. It describes itself as

> Description: Ubuntu themes and artwork
 This package contains merely the Distributor Logo and pulls in all the other
 components via Depends.

---

