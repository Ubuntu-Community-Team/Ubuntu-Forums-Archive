---
title: "ATI x2600XT underclock..."
date: 2011-06-08
forum: General Help
---

### Post by edwardecl on 2011-06-08
I'm not sure where to post this so it ended up here.

As my title suggests I have an x2600XT ATI (passive cooling) installed and working on Ubuntu 11.04. However I wish to under clock the card but am not able to.

I have tried rovclock which doesn't seem to support the x2000 series or higher.

Then you have aticonfig which uses the ATI overdrive settings in the GPU BIOS. That's where my problem is, there is only one clock speed set in the BIOS (800mhz GPU/700Mhz Ram) and I can only over clock by 80mhz but can't under clock at all...

As I don't even log into X most of the time is is a big waste, and I don't have another card to put in it.

The only other option I have found is to rewrite the ATI BIOS with a modified one, and I really don't want to go down that route as it is extremely risky apparently.

It's annoying because all my newer cards under clock by themselves when not in use but not this one...

Are there any other alternatives?

---

### Post by Mark Phelps on 2011-06-08
Don't have a solution ... but my suggestion, if you want to do some research, is to head over to the Phoronix forums and look through their ATI Linux threads.  They do a LOT of low-level ATI stuff there and they may have a thread for that, or they may also respond to a question from you.

Good Luck

---

### Post by edwardecl on 2011-06-08
Cheers...

Didn't find anything new there so I bit the bullet and dumped and edit the video BIOS to add lower clock settings which worked like a charm.

Now aticonfig lists the range as 300-880mhz instead of 800-880mhz and sets the clock to 108mhz when idle :). Now the GPU temp is 53C instead of 80C which is a bonus.

---

