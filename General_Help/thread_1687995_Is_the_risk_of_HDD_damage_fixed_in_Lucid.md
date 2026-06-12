---
title: "Is the risk of HDD damage fixed in Lucid?"
date: 2011-02-14
forum: General Help
---

### Post by Ernesto RD on 2011-02-14
Ibe read in several places, that older versions of ubuntu could *possibly* cause damage to the Hard disk of laptops / netbooks, due to constant load cycles (spin-ups?). 
For expamle, here:
[http://www.thebuzzmedia.com/ubuntu-power-saver-settings-could-damage-hard-drive/](http://www.thebuzzmedia.com/ubuntu-power-saver-settings-could-damage-hard-drive/)

And since im using Ubuntu Netbook edition (Lucid 10-04 NRE) on my netbook, im a bit concerned about this issue.
Just as a precaution, ibe disabled the checkbox in the power management dialog, that sais "reduce speed of hard drives when possible".
So:

¿Is it true that some ubuntu version actually damaged hard drives?

If so, ¿has this issue been fixed in 10.04?

¿Can i safely re-enable the "reduce speed of hard drives when possible" option in power management options?

Ibe tried looking for answers to these questions, but i only find old information about previous (8x, 9x) versions of ubuntu, so any help would be appreciated.
thanks

---

### Post by Docaltmed on 2011-02-14
I'm pretty sure that problem is long gone.

---

### Post by Ernesto RD on 2011-02-15
are you shure???
:)

---

### Post by matt_symes on 2011-02-15
Hi

From what i have read it seems to have been fixed in 10.04 but you can check with the smartctl monitoring tools and keep an eye on what the kernel is doing to the drives.

Kind regards

---

### Post by mr_luksom on 2011-02-15
Hmmm, I've been using ubuntu since 10.04, and anything set in hdparm has always been persistent. This dude's script resets hdparm basically on any acpi event.

Doesn't sound like it was that serious anyway, just a few extra pinups spindowns.

---

### Post by Grenage on 2011-02-15
The article is cute, I'll give it that.

---

