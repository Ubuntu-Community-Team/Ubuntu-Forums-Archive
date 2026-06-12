---
title: "Upgrading... fixed vs rolling releases"
date: 2010-10-05
forum: General Help
---

### Post by marc_roi on 2010-10-05
Of the many distros I've used over the years, Ubuntu is the one I settled with. I needed a system I could carry around on an USB disk and use on different hardware configurations, and Ubuntu is the only distro that allows this despite many other (good) distros that claim more or less advance automatic hardware configuration.

However, there's one thing I grew to hate and it's the fixed release system. I tend to configure quite heavily my OS, changing system scripts, config files, and installing tons of software. Thus having to reinstall everything when a new release appears is not feasible, and dist-upgrade broke my system more than once and I had to reinstall.

Debian's rolling releases seems the only way to go, if only Debian had the same automated hardware detection as Ubuntu... *sigh*
Looks like it's not just a matter of kernel config as I tried the same config, modules and firmware both on Debian and Ubuntu and most of my wifi and sound cards were not recognized on Debian.

Any suggestions are welcome... :(

---

### Post by TBABill on 2010-10-05
If you don't mind changing distros, PCLinuxOS is a rolling release, great hardware detection and very up to date software. Repos are pretty good but not as good as Ubuntu. however, a simple package request can get something you want into the repos in just a day or two. The devs actually visit the forums daily and respond when they choose. 
 
If you want a rolling release and a super fast system it's a great OS. But it doesn't break much so you'll probably get bored. And you have all the DE flavors you want...KDE is the main, but they also have Gnome, E17, LXDE, Xfce, etc. Keeps you from upgrading every 6 months :)

---

### Post by muteXe on 2010-10-05
Slackware my friend. Slackware.

---

### Post by wafflesausage on 2010-10-05
You can try backing up your /etc directory between upgrades. Also, if you want to try a rolling release distro, I'd suggest Arch.

---

### Post by snowpine on 2010-10-05
Rolling release and fixed release are equally risky over the long term (all other things being equal). The only difference is how this risk is distributed: fixed releases are very unstable for one day every 6 months, while rolling releases are slightly unstable every day. In other words the decision is all about your personal style in managing risk. 

I like to celebrate "upgrade weekend" every 6 months where I work through any problems with the new release in one intense session. Then I am guaranteed my system will work exactly as I expect it to work until the next release. I am uncomfortable with the small daily changes of a rolling release distro. When I turn my computer on in the morning, I do not want any surprises that might cause lost productivity. Most enterprise users (i.e. "paying customers") agree, which is why a commercial distro like Ubuntu will never be rolling release.

For a hobbyist or home user, I agree rolling release can be fun, and I've had plenty of good times playing around with Arch or Sidux on spare machines.

As an addendum, I'll point out that Ubuntu does not force you to release-upgrade every 6 months. Many users stick with the LTS releases for 2-3 years for maximum stability.

---

### Post by schtufbox on 2010-10-05
I tried PCLinuxOS on the wife's PC (heh) and found it quite good, I'm actually considering switching my Ubuntu PC over, but not actually decided yet..I may go for Mint Debian instead.

---

### Post by marc_roi on 2010-10-05
Thanks for your replies.

[QUOTE=TBABill]If you don't mind changing distros, PCLinuxOS is a rolling release, great hardware detection and very up to date software. Repos are pretty good but not as good as Ubuntu.[/QUOTE]

Thanks, I just downloaded PCLinuxOS and am going to try it. From your description I guess it doesn't use Debian's or Ubuntu's repos?

[QUOTE=snowpine]As an addendum, I'll point out that Ubuntu does not force you to release-upgrade every 6 months. Many users stick with the LTS releases for 2-3 years for maximum stability.[/QUOTE]

Agreed, but the problem is, once the current LTS "dies" (I'm using Lucid ATM) I will be forced to upgrade... either that or I'll have to forget about further updates. And I know from experience that the upgrade process is going to break my system and I'll have to lose days reinstalling and reconfiguring everything like I did for 9.04 and 9.10. That's the only reason I thought about Debian's rolling releases.

---

### Post by cascade9 on 2010-10-05
> **marc_roi said:**
> Debian's rolling releases seems the only way to go, if only Debian had the same automated hardware detection as Ubuntu... *sigh*
Looks like it's not just a matter of kernel config as I tried the same config, modules and firmware both on Debian and Ubuntu and most of my wifi and sound cards were not recognized on Debian.

Any suggestions are welcome... :(

Tried/tought about Linux Mint Debian Edition? ;) 

BTW, with the sound cards + debian, were you using lenny or testing/sid?

---

### Post by snowpine on 2010-10-05
> **marc_roi said:**
> Thanks for your replies.

You're welcome!

> **marc_roi said:**
> Agreed, but the problem is, once the current LTS "dies" (I'm using Lucid ATM) I will be forced to upgrade... either that or I'll have to forget about further updates. And I know from experience that the upgrade process is going to break my system and I'll have to lose days reinstalling and reconfiguring everything like I did for 9.04 and 9.10. 

Do you think rolling releases never break? The advantage of fixed releases is that you know in advance exactly when they will break. You can circle the date on the calendar and plan your schedule around it. 

For Lucid, that date is April 2013 (April 2015 for server installs).

> **marc_roi said:**
> That's the only reason I thought about Debian's rolling releases.

Debian is a fantastic distro (I made the switch from Ubuntu a couple of years ago) so I won't try to talk you out of it. ;)

---

### Post by dabl on 2010-10-05
Rolling release is definitely preferred, if you (a) make a lot of custom configurations, and (b) need or want to use the most recent software.  I like aptosid, the distribution formerly known as sidux, based on Debian Sid.  Others like Arch, and it would be my second choice, if I weren't completely happy with aptosid.

The *buntus are interesting because of their "early adoption" of emerging software, and you can learn a lot working with it, but the six-monthly reinstall/reconfigure events are kind of a drag.  As said above, there's no _requirement_ to update, if you are fully productive with the earlier version.

---

### Post by marc_roi on 2010-10-06
> **snowpine said:**
> Do you think rolling releases never break?

If a few packages break, I can fix them, or I can wait a couple of days until a fixed version is released (sort of what happened with sidux).
But in my experience a distro upgrade on a heavily customized OS screws up the system horribly, insisting on removing dozens of packages, replacing settings and breaking dependencies, applications and things that previously worked fine...

Anyway I tried PCLinuxOS, Aptosid and a few others and it looks like Ubuntu is the only installable distro who can recognize sound/gfx/lan/wifi cards on each and every system I try it on. I don't know how it does it, but in the end it looks like I'll have to stick with Ubuntu's fixed release system and pray dist-upgrade won't force me to reinstall.

Thanks everyone for your suggestions.

---

### Post by andrew.46 on 2010-10-06
Hi muteeXe,

> **muteXe said:**
> Slackware my friend. Slackware.

I assume you are referring to the development arm of Slackware known as -current? Strictly speaking even this is not a *true* rolling release as it is primarily focused on the next release version. Apart from this aspect Slackware uses fixed releases at relatively irregular intervals.

Andrew

---

### Post by marc_roi on 2010-10-07
Success! I'm writing this from my new Debian system. Everything works, from sound to webcam to wifi to touchscreen, on every pc I try it on.
It was easier than I thought: I just had to enable all the drivers in the kernel config, install all the free/non-free firmware, and tweak the alsa config file.

Goodbye Ubuntu :guitar:

---

### Post by polki@mac.com on 2010-10-07
Glad you solved it! Have fun and enjoy Debian.
Don't forget to mark the thread solved as well ;-)

---

