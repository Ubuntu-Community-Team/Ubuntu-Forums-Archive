---
title: "Virtual Box and Windows"
date: 2010-01-04
forum: General Help
---

### Post by staf0048 on 2010-01-04
Ok, before I get started I want to recognize that I understand this has little to do with Ubuntu itself...

That said, I know some of you are using Windows inside a VM, so I figured this was a good place to start.  I've got Vista installed on a seperate HDD (I don't want or need to dual boot), but I cannot install it on a VM because all I have is the rescue CD that came with my computer.  It thinks I'm trying to install it on a different computer and kicks me out, when in fact it's the same physical computer.

So my questions are this:  

1.  Has anyone been able to install from a rescue CD onto a VM?
2.  Is there a legit site for me to download a copy of Windows Vista, knowing that I already have a registered product key?
3.  If not, what are my chances of getting a copy of Windows from Microsoft if I were to say I lost my rescue cd?

Thanks for your thoughts/help!

---

### Post by howefield on 2010-01-04
> **staf0048 said:**
> Has anyone been able to install from a rescue CD onto a VM?

Most recovery CDs are tied to the hardware that they are intended for and therefore won't install inside a VM. The VM only sees the virtual drivers, and doesn't access the hardware for itself.

> Is there a legit site for me to download a copy of Windows Vista, knowing that I already have a registered product key?

Don't know. I'm guessing you mean for free, seeing as you have a valid key, but I still don't think so.

> If not, what are my chances of getting a copy of Windows from Microsoft if I were to say I lost my rescue cd?

At best, I'd say less than nil, your computer vendor will most likely replace your recovery disk for a fee, which could well be silly money when compared to buying a new copy off the shelf.

Sorry I can't be more positive, but chances are you'd be able to pick up a new copy at a decent price with Vista not being current any more, and if your software runs on xp, maybe you could try that.

---

### Post by LinuxRules1 on 2010-01-04
you could use G4U. G4U(ghost 4 unix) makes an image of your hard drive. it might also include the recovery partition (i don't know for sure) so if it won't boot when you load the image in the VM you might be able to use the recovery CD to reload vista.

it will require you to have a ftp server though, but they are easy to setup

G4U Website: [http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)

---

### Post by staf0048 on 2010-01-04
That was my fear.  To be honest I'd rather stick with removing and replacing the Vista HDD for the few times I'm going to need it, vs. paying more $$ for an OS I already own.

How about this...It's a Toshiba recovery disc and I'm assuming Toshiba just added some software to the disc to load it's own interface before getting to the full Windows install...is there a way to strip out the Toshiba software somehow and just be left with the Windows install?

---

### Post by staf0048 on 2010-01-04
> **LinuxRules1 said:**
> you could use G4U. G4U(ghost 4 unix) makes an image of your hard drive. it might also include the recovery partition (i don't know for sure) so if it won't boot when you load the image in the VM you might be able to use the recovery CD to reload vista.

it will require you to have a ftp server though, but they are easy to setup

G4U Website: [http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)

Thanks!  I will give that a try.  I already attempted loading Vista and Ubuntu on the same HDD, then link Vista to the VM.  It didn't load, so I used the rescue CD to attempt to fix it and nada.  So I don't know if this will change that situation....but we'll see.

---

### Post by howefield on 2010-01-04
> **staf0048 said:**
> To be honest I'd rather stick with removing and replacing the Vista HDD for the few times I'm going to need it, vs. paying more $$ for an OS I already own.

Just wondering if you could put it inside your computer and boot to whichever disk you want, or put it inside a USB caddy, or e-SATA if you have that interface and boot from it as required. 

> is there a way to strip out the Toshiba software somehow and just be left with the Windows install?

Well, it is only software, and what can be man made can be man broken. :-)

Seriously though, not worth the huge and considerable effort, even if you could find someone who could do it.

---

### Post by blur xc on 2010-01-04
> **staf0048 said:**
> That was my fear.  To be honest I'd rather stick with removing and replacing the Vista HDD for the few times I'm going to need it, vs. paying more $$ for an OS I already own.

How about this...It's a Toshiba recovery disc and I'm assuming Toshiba just added some software to the disc to load it's own interface before getting to the full Windows install...is there a way to strip out the Toshiba software somehow and just be left with the Windows install?

check out vlite - an IT friend of mine suggested that it might be possible to do this, but either way I sure it'll be a violation of your EULA.  Ethically, it'd be no different than downloading a cracked windows iso from some pirate software website.

BM

---

### Post by staf0048 on 2010-01-04
> **howefield said:**
> Just wondering if you could put it inside your computer and boot to whichever disk you want, or put it inside a USB caddy, or e-SATA if you have that interface and boot from it as required. 



Well, it is only software, and what can be man made can be man broken. :-)

Seriously though, not worth the huge and considerable effort, even if you could find someone who could do it.

The Vista HDD is in a portable HDD case, but if I attempt to boot from the USB connection, the startup fails.  It only works if the HDD is actually installed inside the computer...

To that end, it's a laptop and there is just not enough space for a 2nd HDD, nor another SATA connection for it.  

Now that you mention it though, my portable HDD case does have an e-SATA connection (just need to buy the cord), could that possibly trick Windows into thinking it's loading from an internal connection?

---

### Post by staf0048 on 2010-01-04
> **blur xc said:**
> check out vlite - an IT friend of mine suggested that it might be possible to do this, but either way I sure it'll be a violation of your EULA.  Ethically, it'd be no different than downloading a cracked windows iso from some pirate software website.

BM

I'll check this out.  Ethically speaking, while it will probably be a violation of the EULA, I own a legit copy, so I don't feel bad about cracking my own software.  

Although, I'm beginning to think I should just patition the companies whose products require Windows.  Seriously, this stuff should be OS neutral anyway so as not to alienate customers...

---

### Post by snowpine on 2010-01-04
> **staf0048 said:**
> I'll check this out.  Ethically speaking, while it will probably be a violation of the EULA, I own a legit copy, so I don't feel bad about cracking my own software.  

Although, I'm beginning to think I should just patition the companies whose products require Windows.  Seriously, this stuff should be OS neutral anyway so as not to alienate customers...

A "virtual machine" install of Windows must be licensed and activated, just like any other Windows install. If you're looking for tips how to circumvent that, I hope you'll ask on a different forum. :)

I agree more companies should be developing software for Linux. I can't imagine the "hacker" mentality helps the Linux community's reputation.

---

### Post by staf0048 on 2010-01-04
> **snowpine said:**
> A "virtual machine" install of Windows must be licensed and activated, just like any other Windows install. If you're looking for tips how to circumvent that, I hope you'll ask on a different forum. :)

I agree more companies should be developing software for Linux. I can't imagine the "hacker" mentality helps the Linux community's reputation.

Too bad I can't "trade in" my license key w/ MS.  I'd give up the one for my laptop for a VM one if that were possible....

---

### Post by snowpine on 2010-01-04
> **staf0048 said:**
> Too bad I can't "trade in" my license key w/ MS.  I'd give up the one for my laptop for a VM one if that were possible....

It can't hurt to call them and ask... I have read a few Microsoft customer support success stories on these forums. And don't forget the computer manufacturer as well; technically your business relationship is with them (assuming the OS was preinstalled), not MS.

It makes you appreciate the freedom of Ubuntu all the more, doesn't it? :KS

---

### Post by staf0048 on 2010-01-04
> **snowpine said:**
> 
It makes you appreciate the freedom of Ubuntu all the more, doesn't it? :KS

Sure does.... I thought my Windows days were behind me too.  I was almost ready to throw away my rescue disc, then Christmas came and I get sucked back in.  It's weird, b/c from my vantage point as a primarily Linux user now, Windows (Vista at least) seems so slow, restrictive, and dangerous...but, that's another topic.

---

