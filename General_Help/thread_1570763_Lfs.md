---
title: "Lfs"
date: 2010-09-08
forum: General Help
---

### Post by didix_1 on 2010-09-08
Hello! Maybe this is not the correct place to ask about Linux from scratch (LFS) but i just want to know if it is better to use a package manager or i can built my LFS without it, and then when i want a Package manager i can just install it later? Can i?
thank you

---

### Post by kidders on 2010-09-09
Hi there,

If you need/want a package manager (at least what the typical Ubuntu user thinks of as a package manager), LFS probably isn't for you.

They're really a feature of maintained distros (eg Debian/Red Hat/etc). Projects like LFS give you the scope to build a completely custom OS, so package management would basically be up to you. A good compromise might be something like Gentoo, which exposes enough of the hardcore stuff to keep things interesting & flexible, but offers a standardised, well-maintained toolchain & package management system.

Anyhow, the answer to your question depends on what kind of system you're going to build. For a standard desktop box you'll certainly need to put *some* sort of package management strategy in place, or you'll wind up going completely insane. The sheer volume & variety of apps you're likely to install would make keeping the state of your entire system in your head very difficult.

For example, suppose you become aware of a new version of libssl or mesa or something, that fixes a critical security bug in the version on your box. Depending on your level of Linux guru-ness, you may find it difficult to assess whether you can even consider installing the update without completely breaking your system. Then, you'd need to identify & rebuild everything that linked against the old application's libraries, determine the nature of any API changes that might require a version bump for other software on your box, and so on.

Once you've gotten started, changing the way you manage installed software could be very tricky, so I'd suggest deciding your approach first, and sticking with it. 

On the other hand, of course, you could be building something completely different (eg some sort of embedded system), with a highly restricted set of software & no particular need to keep it current, in which case you may well just wind up fighting with a package manager, rather than benefiting from it.

I hope that helps.

---

### Post by didix_1 on 2010-09-11
Thank you for your reply,
For my first LFS i think I'll go without a package manager , I'll try to keep it all in my head , because I'm intending to keep it simple i just want to see it work :P And of course I'll built other LFS where i will use a package manager.
Thank you again.

---

