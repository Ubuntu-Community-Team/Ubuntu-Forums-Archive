---
title: "NFS root / netboot bug &quot;fixed&quot;, how to apply?"
date: 2009-12-07
forum: General Help
---

### Post by dannysauer on 2009-12-07
So, when I upgraded my netbooted Mythbuntu box from Jaunty to Karmic, the boot process was broken.  It looks like Bug [430348]("https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/430348") describes what's happening, and I'm hopeful that it'll fix things.  It says in the bug report that mountall version 0.1.8 fixes it.  So, I find another amd64 machine, mount the root filesystem, chroot into it, run dpkg - and it says I have version 1.0.  I find this disconcerting.

A little more research later, I see a reference to [https://launchpad.net/ubuntu/+source/mountall/0.1.8/](https://launchpad.net/ubuntu/+source/mountall/0.1.8/).  Ok, there's the changelog again which says it fixes this, and there's source.  It also says that mountall is the binary built from that, so I click that link and I get taken to the page where mountall 1.0 is located.

So, umm, how do I 1) tell which unrelated source version I have installed and, if needed, 2) install a package built from that which won't bust further upgrades later on?

---

### Post by dannysauer on 2010-01-14
I guess I should ask how to enable the root account.  Perhaps the ensuing ruckus would then attract the attention of someone who knows how Ubuntu package development relates to the eventual distributed packages. ;)

---

