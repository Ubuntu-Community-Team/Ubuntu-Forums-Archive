---
title: "#&amp;%$&amp;#* Tap to click hell!!!!"
date: 2009-11-05
forum: General Help
---

### Post by tkirby on 2009-11-05
I'm a recent ex-Gentoo user who got sick of the constant problems with Gentoo and decided I wanted something that "just worked".  Ubuntu has a rep for being just that so I installed 9.04 and with a few minor exceptions everything "just worked". So far so good.

So, I'm happily computing along the other day and a dialog pops up asking me to upgrade to 9.10. I figured it's a minor upgrade so how bad could it be? Well aside from the fact that it no longer sees my sound card, everything went ok. Or so I thought. Apparently, somebody decided it would be a fun idea to turn on tap-to-click by default in this version.  I didn't notice right away but after a few minutes of accidentally launching programs and sending half written emails I decided that tap-to-effing-click had to go. Open up 'Touchpad' in settings and turn it off, right?

WRONG!

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics.

Ok, I didn't launch GSynpatics, I launched 'Touchpad' but I'll play along. I Gentoo around with xorg.conf until it is set up like the nice dialog told me to and Touchpad/GSnapticwhatever will launch, right?

WRONG!

Same effing message.

Search the net for other people stuck in my ring of touchpad hell. Find lots of the same error but none of the proposed solutions fix my issue.

Anyway, I've done my time and just don't have it in me to track down another obscure xorg/hardware issue. I just want to go back to the Ubuntu that didn't suck. How can I revert to the previous version of Ubuntu?

PS: Whoever invented tap-to-click should to be defenestrated. Seriously, who thought this was a good idea?

---

### Post by alphacrucis2 on 2009-11-05
> **tkirby said:**
> I'm a recent ex-Gentoo user who got sick of the constant problems with Gentoo and decided I wanted something that "just worked".  Ubuntu has a rep for being just that so I installed 9.04 and with a few minor exceptions everything "just worked". So far so good.

So, I'm happily computing along the other day and a dialog pops up asking me to upgrade to 9.10. I figured it's a minor upgrade so how bad could it be? Well aside from the fact that it no longer sees my sound card, everything went ok. Or so I thought. Apparently, somebody decided it would be a fun idea to turn on tap-to-click by default in this version.  I didn't notice right away but after a few minutes of accidentally launching programs and sending half written emails I decided that tap-to-effing-click had to go. Open up 'Touchpad' in settings and turn it off, right?

WRONG!

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics.

Ok, I didn't launch GSynpatics, I launched 'Touchpad' but I'll play along. I Gentoo around with xorg.conf until it is set up like the nice dialog told me to and Touchpad/GSnapticwhatever will launch, right?

WRONG!

Same effing message.

Search the net for other people stuck in my ring of touchpad hell. Find lots of the same error but none of the proposed solutions fix my issue.

Anyway, I've done my time and just don't have it in me to track down another obscure xorg/hardware issue. I just want to go back to the Ubuntu that didn't suck. How can I revert to the previous version of Ubuntu?

PS: Whoever invented tap-to-click should to be defenestrated. Seriously, who thought this was a good idea?

Have a look in archived Karmic Koala dev thread. There was a lot of discussion about this.

---

