---
title: "Windows Apps (Quicken and TurboTax) in Ubuntu 9.10"
date: 2009-12-23
forum: General Help
---

### Post by manco on 2009-12-23
Hello again everyone; I hope this is posted in the right category.

Today I installed Ubuntu 9.10 on my family's desktop PC in a dual-boot with Windows XP Home Edition.

Everything is looking good, but my parents need Quicken and TurboTax.

It's not a big deal, since they can go into XP and use the programs there, but is there any way they can access these programs in Ubuntu?

The only things I can think of are:

a) Wine

b) Virtual Windows

Can anyone help me out?

Thanks

---

### Post by Sef on 2009-12-23
Virtualizing Windows would be the best solution.

---

### Post by prshah on 2009-12-23
> **yellowsnow4free said:**
> 
but my parents need Quicken and TurboTax.

a) Wine
b) Virtual Windows


As suggested, virutalization is possibly your best bet, but, if for resource reasons, it is not workable for you, then you have the following options with WINE:

a) For Quicken, apparently all versions except the latest work fine with WINE: See [WINE's AppDB for Quicken]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=107") for more details.

b) With TurboTax, it's the converse: 2005 version worked OK, but current versions don't. See [WINE's AppDB for TurboTax]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=623") for more details.

If you use TurboTax only rarely, then you can stick to Windows for it; I think you can use Quicken through WINE if you use it on a daily basis. Please study caveats in the linked pages.

---

### Post by manco on 2009-12-23
> **Sef said:**
> Virtualizing Windows would be the best solution.
I'm willing to try that, but I read that with some VM's it requires a virtual re-install of Windows.

**I already have XP Home on my PC via dual-boot**, is there a good VM that can work off that?

I've read VMware player can do such a thing, but I don't know if my system will run it at speed anyway.  P4 1.7 Ghz, 3/4 GB RAM, Nvidia Graphics card

---

### Post by ubun_two on 2009-12-23
> **yellowsnow4free said:**
> I'm willing to try that, but I read that with some VM's it requires a virtual re-install of Windows.

**I already have XP Home on my PC via dual-boot**, is there a good VM that can work off that?

I've read VMware player can do such a thing, but I don't know if my system will run it at speed anyway.  P4 1.7 Ghz, 3/4 GB RAM, Nvidia Graphics card

I am pretty sure there are ways to load your existing Windows partition from Virtualbox, but it's not automatic.

[http://www.google.com/search?q=virtualbox+partition+access&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=virtualbox+partition+access&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

### Post by manco on 2009-12-23
Just a reply to everyone here, I just installed Quicken via Wine; working great.

I'm still going to check into a VM of some kind though, just because :)

Thanks everyone!

---

