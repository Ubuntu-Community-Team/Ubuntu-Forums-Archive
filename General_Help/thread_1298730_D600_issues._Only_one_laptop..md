---
title: "D600 issues. Only one laptop."
date: 2009-10-23
forum: General Help
---

### Post by KeyserSoze93 on 2009-10-23
I have a Dell Latitude D600 which works fine with Ubuntu 8.04, fully upgraded including backports, and Firefox 3.5 (from Ubuntuzilla)

My mother has the same laptop (though with the 1024x768 version of graphics card) which is a pile of crap.

Seriously, sometimes it doesn't even startup, and simply says:
"Kernel panic - not syncing: Attempted to kill the idle task"

I think I resolved that issue by adding "idle=poll" to the kernel parameters in GRUB.

She always has about 12 tabs open in Firefox, so with the original 512 MB of RAM it was a joke.

I added another 1 GB stick in, which gives her 1.25 GB (since the 512 was in 2 sticks)

After that, the laptop seemed to be fine, yet recently, with no changes to the system config whatsoever, the computer began to crash when she was using Firefox.

I tracked this issue down to the graphics driver (she is using the default, which is the open source radeon driver, and the same on as I am running with no problems, remember), which I figures was having problems with blitting (since it only crashed when she was scrolling around pages or spreadsheets)

I did a full "apt-get update && apt-get upgrade && apt-get install linux-image-generic && apt-get install linux-headers-generic", and that seemed to solve the blitting issue, and I scrolled as fast as the mousewheel would allow, and the laptop handled it with no issues.

I then gave it back to her, but when she began using it, she managed to make firefox (at this point the newest version of 3.0.*)

I installed Firefox 3.5 (with Ubuntuzilla), and Google Chrome as a backup.

Firefox 3.5 seemed OK when I briefly tested it, but when she began using it in earnest, IT FROZE.

I don't know whether it is simply the amount of tabs she has open (none are running youtube or any CPU intensive tasks, and remember, she has a perfectly reasonable amount of RAM), or whether there is a hardware issue (i.e. bad RAM)

I don't understand why my laptop works fine, with exactly the same software, give or take, and yet hers is unusable.

Any ideas? Since the main app she uses is Firefox, and it is on Firefox that the computer becomes particularly crap, I can't really establish whether the problem is with the computer, or simply Firefox, but Firefox works fine for me, and everyone I know.

---

### Post by earthpigg on 2009-10-23
if the exact same software running on the exact same hardware fails in one case but works perfectly in the other as you describe, then it is almost certainly a hardware failure.

let's start with testing the RAM:
[http://www.memtest86.com/](http://www.memtest86.com/)

if that isn't it, let's test the hard drive:
[http://en.wikipedia.org/wiki/Badblocks](http://en.wikipedia.org/wiki/Badblocks)

---

### Post by KeyserSoze93 on 2009-10-23
I was already figuring to do a memtest, and I'll do the hard drive test as well.

Thanks!

---

### Post by P4man on 2009-10-23
memtest would indeed be the first thing to try (its included in the livecd, just boot from it and select it from the first cd menu)

If its not Ram, then consider what else is different between the laptops. You mention screen, but do they have the same videocard (and drivers) ? Also are they using the same BIOS?

---

### Post by KeyserSoze93 on 2009-10-23
the ram was broken, as seemed likely. I memtested the 1 GB stick in both slots (DIMM A and DIMM B), and it's definitely bad.

Unless, that is, and this is what I'm trying now, there is a bad connection on the motherboard with the ram controller.

I'm memtest'ing now with only the 256 stick in, in order to make sure the RAM is definitely kaput before I take it back to the shop.

Thanks for the support, and hopefully I should have this issue solved soon.

---

### Post by P4man on 2009-10-24
its not necessarily kaput. those sticks may simply not work together or not work on that machine. laptops can be picky. try using two identical sticks and from a brand and type recommended by the vendor.

---

### Post by KeyserSoze93 on 2009-10-24
Well, when I memtest'ed the 1 GB stick, I took the other stick out so that I could make sure it wasn't just the stick or the socket or a combination of both sticks.

Then, I took the 1 GB stick out, and did a memtest with the 256 MB stick, and I left it for 12 hours and it found no problems.

---

### Post by P4man on 2009-10-24
well I agree you clearly found the root cause. But its still entirely possible that same 1gb stick works flawlessly on a different machine, and all sticks from that type/brand will fail on your laptop. Just saying in case you'd rma it and get a new -but identical stick. Problem might be compatibility so check dell website for tested ram modules on that machine, or buy from a brand that guarantees compatibility with your specific laptop.

---

### Post by blueridgedog on 2009-10-24
> **earthpigg said:**
> if the exact same software running on the exact same hardware fails in one case but works perfectly in the other as you describe, then it is almost certainly a hardware failure.

I see that he found the issue with memtest.  I was going to suggest that there are some pages with odd java or big animated gifs that seem to impact firefox.  If the problems persist after the memory swap, open the same tabs as her and see if there are any issue.

---

### Post by mikey12561 on 2009-10-24
Dell computers are very picky when it comes to ram. Besides the D600 is not very different then my D800 just it doesn't have WXGA or WYXGA screens. More likely it uses a DDR Type ram.

Here is your ram specs: Double Date Rate (DDR) SDRAM at 266MHz (PC2100); Standard - 128MB; Maximum - 2.0GB; Memory module
 capacities - 128, 256, 512MB, 1GB

So this is what you need to do. Your moms laptop take PC2100 DDR Ram. You may have bought the wrong kind. You could've bought PC2200 DDR ram it still fit in the slot but it wouldn't work. You can also find more information for your laptop at this link.

[http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CAwQFjAA&url=http%3A%2F%2Fwww.dell.com%2Fdownloads%2Fus%2Fproducts%2Flatit%2Fd600_spec.pdf&rct=j&q=dell+d600+specs&ei=sfbiStHpC8yg8AbmupzpAQ&usg=AFQjCNGl4RTTPJlR3XUM25F39DfrT0U7yg&sig2=2UhXLQpqXpKJPSh1pLPyNQ](http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CAwQFjAA&url=http%3A%2F%2Fwww.dell.com%2Fdownloads%2Fus%2Fproducts%2Flatit%2Fd600_spec.pdf&rct=j&q=dell+d600+specs&ei=sfbiStHpC8yg8AbmupzpAQ&usg=AFQjCNGl4RTTPJlR3XUM25F39DfrT0U7yg&sig2=2UhXLQpqXpKJPSh1pLPyNQ)

---

### Post by recluce on 2009-10-24
First of all, if you should combine a 256MB and a 1GB module, make sure that "Dual Channel" RAM mode is disabled (I only know the Latitude D-Series from D610/810 onward, so I do not know the BIOS settings for that machine).

Frankly, I would go for a matched pair of modules, either 2 1GB sticks or 2 512MB sticks, whatever seems better from your perspective - since working without Dual Channel comes with a performance loss.

Also, I would google around to see which brands are sold as specific matches for your notebook. If you find a brand you like, google around more with that brand name. 

As others pointed out very correctly: compuiters can be picky when it comes to memory. Using a brand that others with the same computer use successfully may be your safest bet.

---

### Post by KeyserSoze93 on 2009-10-24
The current 1 GB stick is an "A Data RMB-940764 DDR400(3)"

I'm not sure where the (3) figures in, or how the tell whether it is PC2100 DDR or PC2200 DDR.

There isn't much info about it online, and the RAM module doesn't say much on it I recognise, other than the fact its a 1 GB stick of DDR 400.

This was just the brand my local computer shop got from their supplier. I know the guy who runs to shop, and he has already said he could can send the faulty stick back if it is faulty.

---

### Post by P4man on 2009-10-24
PC2100 is just another name for DDR 266
PC2700 = DDR 333
PC3200 = DDR 400

The first number refers to the transfer rate in MB/s, the second number is the clockspeed. They are function of each other.

There is no such thing as PC2200

---

### Post by KeyserSoze93 on 2009-10-24
> **P4man said:**
> PC2100 is just another name for DDR 266
PC2700 = DDR 333
PC3200 = DDR 400

The first number refers to the transfer rate in MB/s, the second number is the clockspeed. They are function of each other.

There is no such thing as PC2200

Thanks for clearing that up, I was surprised that I'd never heard of it, but mikey12561 said I might have bought it by mistake, so I did wonder.

---

