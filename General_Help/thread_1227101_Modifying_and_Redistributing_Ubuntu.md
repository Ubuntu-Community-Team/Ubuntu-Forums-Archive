---
title: "Modifying and Redistributing Ubuntu"
date: 2009-07-30
forum: General Help
---

### Post by mitgiraffe on 2009-07-30
I work for a company that for the last several years has been selling computer systems  composing of Windows XP with a large number of educational programs (all proprietary made by numerous different vendors) installed, along with our own custom code designed to integrate all of the applications and provide limited management capabilities for the system.

For a number of reasons, we are interested in looking at alternative operating systems on which to base our solution. Ignoring the technical aspects of getting these Windows applications to run on other operating systems, what are the licensing ramifications?

More specifically, I know Ubuntu is free to install and distribute... but we will certainly be charging for our value-add and licensing fees for the software we are installing. Is this legitimate, and how should we handle that fact that all the various software packages that ship with Ubuntu has their own licensing terms? Do we have to evaluate every single application license to ensure we are not violating license conditions, or is there some level of freedom that we have?

Additionally, in terms of redistributing source code, if we just point users to Ubuntu downloads if they want the free software we are using, is that adequate? I know any actual changes to the software have to be posted back to the community as well and freely available, but this would not apply in any way to simple configuration changes we make would it?

I know I am asking a lot, and it has probably all been asked before, but I am trying to gather as much information as possible as our greatest hinderance to proceeding with a full-fledged feasibility is ensuring we are not violating licensing terms...

Thanks for your input!

---

### Post by LowSky on 2009-07-30
Ubuntu's default install is completely redistributable. Things like MP3/Flash/Java are not, but are also not installed by default, hopefully you understand.

Selling ubuntu with your own built in applications isn't an issue, but it might be if you go around calling *_Your_*buntu, as Canonical isn't a fan of people using their name projects outside their control. Best is to cal it whatever you liek, and maybe say, built on Ubuntu.

---

### Post by az on 2009-07-30
> **mitgiraffe said:**
> For a number of reasons, we are interested in looking at alternative operating systems on which to base our solution. Ignoring the technical aspects of getting these Windows applications to run on other operating systems, what are the licensing ramifications?

To put it simply, the most prevalent FLOSS (Free-Libre Open Source Software) license you will encounter in Ubuntu is the GNU GPL.  To comply with the GPL, you need to provide the source code for any GPL-licensend program you (re)distribute.  Since Ubuntu is already distributed with the source code, all you need to do it point your customers to the Ubuntu sources and you are compliant.

There are other licenses, but everything in the Ubuntu Main and Universe repository are licensed in that way (either using the GPL or a compatible license).

The other two licensing fields are trademark and patents.  Patents are easy - there are no software patents for you to worry about.  Trademark is pretty simple, too.  Canonical owns the Ubuntu trademark.  There is a simple Ubuntu Trademark policy which you can find on the ubuntu.com website.  In simple terms, if you simply add a few extra ubuntu packages to the default subset, you can call it Ubuntu.  If you make deeper modifications, you can call it an "Ubuntu Remix" or "based on Ubuntu" to make it clear that it is not the original version.

> **mitgiraffe said:**
> More specifically, I know Ubuntu is free to install and distribute... but we will certainly be charging for our value-add and licensing fees for the software we are installing. Is this legitimate, and how should we handle that fact that all the various software packages that ship with Ubuntu has their own licensing terms? Do we have to evaluate every single application license to ensure we are not violating license conditions, or is there some level of freedom that we have?

It's actually a lot easier than dealing with proprietary software in which every single piece truly has a unique licensing situation.  In FLOSS, if it's GPL or GPL-compatible, you know where you stand.  For everything else, you need to know the differences.

You are entitled to charge for your services.  You are simply not allowed to redistribute the programs under a different license than the license that was given to you.

> **mitgiraffe said:**
> Additionally, in terms of redistributing source code, if we just point users to Ubuntu downloads if they want the free software we are using, is that adequate? I know any actual changes to the software have to be posted back to the community as well and freely available, but this would not apply in any way to simple configuration changes we make would it?


No, this doesn't apply to configuration changes and the like.

---

### Post by mitgiraffe on 2009-07-30
Thank you very, very much for your quick and detailed responses! They have been incredibly helpful and reassuring that, from a legal perspective, we will definitely be able to continue!

---

