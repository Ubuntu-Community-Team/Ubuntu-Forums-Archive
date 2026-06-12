---
title: "Advie Please: FIX bad upgrade, or INSTALL from scratch on custom kernel laptop"
date: 2006-06-10
forum: General Help
---

### Post by malacandra on 2006-06-10
The machine: A Dell Latititude D810 from Emperor Linux running their custom kernel. Mostly it was "kernelized" to do an effective hibernate.

OK, I got impatient and (even against the warning of Emperor's support) went ahead and switched my repositories to "dapper" and upgraded everything.

The problem:
(1) No hotplug or card services: I can't use my plugin wireless mouse, mount flash drives or get my Sprint wireless card to work (using scripts that worked before the dapper upgrade).

(2) My wireless card is completely gone. Used to show up as wlan0 now it's not there at all. (It *is* listed in the Hardware Device List). An "ifconfig" only gives me **eth1, lo, sit**.  

Now, ALL of the above works fine from the Dapper Live CD.

Here are my options:

(1) Try to fix tis busted install by tracking down modules, and really pulling things apart under the hood.

(2) Go crawling back to Emperor and telling them what I did and getting some support that way.

(3) Doing a complete overwrite/install of Dapper into the existing / director. If I do so, I already have a separate partition for /home, so would I need to do anything special or just go ahead and install. 

I'm leaning heavily toward 3 unless someone can give me a reason why that wouldn't work or would be a bad idea. 

Now that I've hosed things, I don't think I'd feel terribvle if I had to abandon my emperor kernel. It's a modified version of an earlier kernel and the Dapper kernel is newer.  So, again, just give me some heads up before I install Dapper completely; and dangers on the path?

I appreciate your help and advice

Mark

---

### Post by tsb on 2006-06-10
I'd go for the reinstall not because it's cleaner or easier, but because when faced with a similar problem it decreased my boot times dramatically.

---

### Post by nalmeth on 2006-06-10
What is Emperor Linux? From your post it sounds like a debian-based distro, that came with the dell, is this correct?

It probably was not a good idea to add dapper repos, unless you really know what you're doing. I know a guy who did something similar with debian and hoary, a hybrid debian system you might say. I know it can be done, but it's a dangerous risk to take.

I don't even know if you can use your old home folder for dapper, but you'll at least be able to access it to get the media back.

I think at worst, if Emperor won't give you any support, you could just install dapper, and migrate all your data from the old /home into your new dapper one.

---

### Post by malacandra on 2006-06-10
No, Emperor is not a custom distro. It came with Ubuntu installed (5.10, Breezy). 

What Emperor does is sell laptops with Linux preinstalled. They add their own custom kernel to give better hardware support (for such things as hibernate). So it's just Breeezy with a custom kernel. (but their kernel lacks in other respects, actually, so I'm thinking now might be the time to dump it).

Well, now it's Dapper with a custom kernel. I think the problem is that when I upgraded all the packages, Dapper upgraded Breezy but whatever particular hardware connection there was between Ubuntu and the empkernel was messed up.

That's why I suspect installing a fresh Dapper might work OK, since all it will do is replace all the emperor kernel stuff with it's own, which should work. Since it's already Ubuntu the settings in my home directory will probably work, yes?

---

### Post by Quirky on 2006-06-10
I'd contact Emperor. You've paid extra for support, though upgrading to Dapper may have voided your warranty I think they'll probably offer you a work around. 

Their website says they do Ubuntu Dapper installs now, so they could probably tell you what you need to do to configure you laptop, maybe even get you their custom upgraded kernel.

---

### Post by malacandra on 2006-06-10
OK. So I modified Grub so that it would load the Ubuntu kernel (rather than the custom kernel). Everything seems to work now: hotplug, wireless, even suspend works nicely.

Hhmmm...perhaps it's just a matter of what kernel to load at boot?

My assumption is that while the empkernel may be "dislocated" because of the Dapper upgrade, the Dapper kernel has all it needs to run properly.

I did put in a request to Emperor. We'll see what they say.

Mark

---

### Post by malacandra on 2006-06-10
OK...still fiddling and here's what I've got:

Whenever I reboot, the names of the ethernet and wireless cards change:

Boot once:
eth1 = wireless
wlan0 = wired network

Boot again:
eth2 = wired network
wlan0 = wireless

What gives?

Also:

(1) Suspend and hibernate seem to work intermittently. After a successful suspend or hibernate, sound is gone. Otherwise sound works fine.

Any ideas on these nooglies?

Mark

---

### Post by malacandra on 2006-06-11
I'll probably hear from Emperor this week.

But here's what I did anyway:

Split my / partition in half. Made a new partition. Did a fresh install of Dapper there. Reinstalled software I had before. With my home on a separate partition, all my data and settings were saved and work fine.

Suspend and Hibernate are the big problems; they don't work or only work intermittently. But lots of people have those problems. Time to go research....

---

