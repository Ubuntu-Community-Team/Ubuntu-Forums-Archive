---
title: "Wake On LAN - Simply Not Working... Ubuntu at fault??"
date: 2012-03-14
forum: General Help
---

### Post by Roasted on 2012-03-14
EDIT - Changes made at bottom...

I always thought that WOL was entirely hardware driven. I have an MSI H61M E33 motherboard on my HTPC, and I cannot for the life of me get it to WOL whatsoever. I called MSI and they confirmed that this board supports WOL, however I need to do several things:

Disable EUP-2013
Enable Wake From PCI or PCE Device

Once done, that's essentially the equivalent of Wake On LAN = Enabled, as some other manufacturers have.

This tech was telling me if I go in Windows 7 and go to this this and this I just have to enable it. Well, I run Linux, and from what I understand it should work out of the box as long as the hardware supports it. Is that correct? He didn't offer much other insight, but he certainly didn't push me away once I said I run Ubuntu, which was nice. He confirmed several times, yes, this board supports Wake On LAN.

That said, what could possibly be the issue? Could Ubuntu have ANYTHING to do with the fact this MSI board refuses to WOL yet my desktop, running an ASRock H61 motherboard works fine, along with my Dell Optiplex 330, and dozens of other systems I've used WOL with running Ubuntu at work?

EDIT - So now I just realized something... WOL works... but only if the computer is turned completely off... then I can fire it up via WOL just fine. But it will NOT wake from suspend. If I'm in Ubuntu and suspend, then send a magic WOL packet to it, nadda. Power off, do the same thing, just fine... What the? How can I get suspend WOL working?

---

### Post by papibe on 2012-03-14
Hi Roasted.

Sometimes you need to do extra steps by configuring some options for your NIC.

Have you take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=360901&highlight=wakeonlan") and this [tutorial]("https://help.ubuntu.com/community/WakeOnLan")?

What is your output of this?
```
sudo ethtool eth0
```
Regards.

---

### Post by Roasted on 2012-03-14
> **papibe said:**
> Hi Roasted.

Sometimes you need to do extra steps by configuring some options for your NIC.

Have you take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=360901&highlight=wakeonlan") and this [tutorial]("https://help.ubuntu.com/community/WakeOnLan")?

What is your output of this?
```
sudo ethtool eth0
```
Regards.

Thanks for the quick response. I'll be able to take a closer look at that system later tonight. Meanwhile, is this kind of the equivalent of how in Windows you have to enable a few check boxes for WOL to work properly?

I suppose it's not always 100% hardware dependent like most people were saying, eh?

The only thing that confuses me is the fact it works when powered off, but not in suspend... Any insight on why that may be?

---

### Post by papibe on 2012-03-14
> **Roasted said:**
> The only thing that confuses me is the fact it works when powered off, but not in suspend... Any insight on why that may be?
I wonder the exact details myself, but since I've configured it several times this is what I can tell you:

Have you noticed that when your computer is on your ethernet card blinks showing traffic?

When properly configured, those lights keep blinking even when you turn off your computer. I imagine that somehow a (minimal) power is still sent to the card so it keeps operating.

When a special package is sent over the network, addressed to the MAC's machine, the card sent a signal to the motherboard to turn on the computer.

I'm no an expert, but that what I've understood so far.

Kind Regards.

EDIT: I just saw your edit about complete off vs. suspend. I'm my experience, not all combinations are possible. Look for the specific capabilities of you motherboard (download a technical manual would be a good idea). Then you would have to match those features with what is presented on 'ethtool'.

---

### Post by matt_symes on 2012-03-14
Hi

This thread may be relevant.

[http://ubuntuforums.org/showthread.php?t=1642272](http://ubuntuforums.org/showthread.php?t=1642272)

The poster had exactly the same problem as you. It's one a bookmarked a while ago.

Kind regards

---

### Post by Roasted on 2012-03-14
I just have to wonder, in most cases where a motherboard blatantly supports Wake On LAN, is this even typically an issue? With my board, it doesn't say Wake On LAN whatsoever. It's just disabling EUP2013 and enabling PCI/PCIE Device Wakeup somehow = Wake On LAN. I work in IT, and I would have never known that had I not called MSI and had them tell me.

So in short, majority of the time, does WOL that's blatantly listed as a feature typically work? Or is it just odd ball occurrences like this that kind of have these features halfway hidden are sometimes in the gray area?

---

### Post by Roasted on 2012-03-14
So now, no WOL works, whether suspend or when it's powered off. This is beginning to seem so incredibly unreliable... :mad:

The pattern I'm seeing is this:

Power on computer - power off computer - WOL does not work.
Power on computer - suspend computer - wake up computer manually - power off computer - WOL works.

It's as if I need to suspend it at some point during use for WOL to function.

Okay, so... this is getting a little old, fast. WOL is proving to be extremely hit or miss, RTC is not even working on my system (I've tried it on other systems in the past and it's always left something to be desired).

SO... that being said... Let's rewind a bit... let's say I have a computer, and I want it to run from 6pm to 7pm every day, and be either turned off or in suspend mode the other 23 hours. I don't even care which, but in some sort of turned off/low power mode... and just the single hour between 6 and 7 that it's up and running.

How can I do it? What alternatives are there? Any Linux-based alternatives? I have a whole slew of towers at home and this lack of reliability from one to another, not to mention, just with one alone... having xyz feature work great, then next time, no dice, I really just don't want to trust the BIOS. Is there any way I could have Ubuntu solely handle all of this? The wake up, shut down, etc?

---

