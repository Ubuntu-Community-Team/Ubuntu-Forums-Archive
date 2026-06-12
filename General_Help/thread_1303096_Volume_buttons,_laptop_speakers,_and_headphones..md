---
title: "Volume buttons, laptop speakers, and headphones."
date: 2009-10-27
forum: General Help
---

### Post by SPARTAN-118 on 2009-10-27
I keep seeing this problem for Ubuntu 9.04 users:

You plug in headphones, crank the volume to what should only be audible to you and you alone, then you get complaints about how loud it is. So you take off the headphones to reply, and find that your laptop's speakers are still playing music, even though you have something plugged into the headphone jack.

Now, this isn't a problem for desktop users, as there isn't usually a pair of built-in speakers right on your case (or even inside it, for that matter).

However, I (and a few other users) would like to know why this is happening, how to fix it, and how to prevent it from happening again.

The bug has already been filed [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/427980"), but it's for an HP laptop, and I've already tried the supposed "fix", with revisions like changing "Intel model=HP" to '=Toshiba' or deleting the space between the two, etc.

This so-called "fix" either does nothing, or mutes all sound. Note that the volume controls all say that it's at a high volume, it's not muted.

Another problem I've only recently been experiencing is that the volume buttons on my USB keyboard stopped working, around the same time I tried this fix. 

I think they're related, since I only started having problems with the buttons after I removed the "options..." line I entered to try and fix the speaker+headphone problem.

Note: When using the keyboard buttons, it appears that Ubuntu itself receives the message, but it fails to deliver it to the laptop. Scrolling with the mouse on the icon on the panel in the bottom-right corner works, as does scrolling on the Volume Control Screenlet. It seems hardware-related switches 'n' things don't work anymore, as the laptop's volume dial doesn't work, either.

The mute button below the play/pause button doesn't work, but the play/pause button still works.

I am using the world's slowest Processor, the Intel Celeron M (1.6 GHz, on par with *netbooks*) with 1 GB of RAM on the Toshiba Satellite a200 Series laptop (from 2007, I think) and a $20 Microsoft keyboard I got for last Christmas.

---

