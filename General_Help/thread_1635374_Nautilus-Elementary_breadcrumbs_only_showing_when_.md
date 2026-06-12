---
title: "Nautilus-Elementary breadcrumbs only showing when root"
date: 2010-12-01
forum: General Help
---

### Post by MariusLV on 2010-12-01
Hi all,

I generally manage to fix my problems when I break something, but this one has me puzzled. I'm using Nautilus-Elementary, and I've been using the hack that allows for custom breadcrumbs. Now, at some point I seem to have done something that broke this functionality, as the only breadcrumbs I see are the default ones. This is despite the fact that I'm using themes that are supposed to contain custom breadcrumbs.

What makes the matter all the more puzzling is that I get the correct custom breadcrumbs whenever I open Nautilus-Elementary as root. I cannot for the life of me figure out why it happened or how to fix the problem.

Is there anybody out there that could help me figure out what's going on?

EDIT: I just purged Nautilus-Elementary from my system, restarted and re-installed N-E. The problem, alas, persists.

---

### Post by MariusLV on 2010-12-03
I realize my problem was rather obscure, which explains why nobody replied :-P

On the off chance that anybody else might end up on this page with the same problem, here's how I solved it:

In my home folder was a file named ".gtkrc-2.0", which apparently contained some settings that overrode several settings in whatever theme I was using. This again explains why the problem only manifested itself when I wasn't using Nautilus as root. I simply deleted the file and reloaded my theme to solve the problem.

It would appear the cause of it all was my relatively recent installation of Lubuntu-desktop, which contained a piece of software called LXAppearance (part of the LXDE project). LXAppearance automatically created the offending file and after some tests I see that the file is recreated every time LXAppearance is executed.

So there you go :-)

---

