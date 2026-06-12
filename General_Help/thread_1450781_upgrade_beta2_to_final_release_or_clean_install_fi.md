---
title: "upgrade beta2 to final release or clean install final release"
date: 2010-04-09
forum: General Help
---

### Post by linuxrockz on 2010-04-09
Hi every one 
I just clean installed lucidlynx beta2. I am really impressed with it :guitar: especially the boot speed.

It worked almost flawlessly except my system froze two times today on desktop and showed this 

"could not write bytes:broken pipe"
and my display became off.

2nd thing is that I have been using ubuntu since 8.04 but I always did a clean install of the final release, this is the first time I have installed a beta version. 

So my questions are

1. Do I need to download the final release and clean install it, or i will need a dist upgrade or ```
sudo apt-get upgrade
``` regularly will be sufficient :).

2. I know the message I got is a bug but is there any known workaround.

Thanks :)

---

### Post by QIII on 2010-04-09
My general answer is usually "Do a clean install".  But that advice is usually targeted at those who are going, say, from 9.10 to 10.04 directly.

Since you have installed Beta 2, the final freeze is on the 15th and the RC comes out on the 22nd, I'd say that if you are having no issues after doing normal upgrade and dist-upgrade after the final freeze before the RC, the change between Beta 2 and the RC will be little, and the change between the RC and the Final will be even less.

So, see how it goes.

If you have persistent issues you can't resolve before the RC, do a clean install of the RC.

---

### Post by oleink on 2010-04-09
> **QIII said:**
> My general answer is usually "Do a clean install".  But that advice is usually targeted at those who are going, say, from 9.10 to 10.04 directly.

Since you have installed Beta 2, the final freeze is on the 15th and the RC comes out on the 22nd, I'd say that if you are having no issues after doing normal upgrade and dist-upgrade after the final freeze before the RC, the change between Beta 2 and the RC will be little, and the change between the RC and the Final will be even less.

So, see how it goes.

If you have persistent issues you can't resolve before the RC, do a clean install of the RC.

Do you mean when 10.04 final release comes out youd suggest getting rid of this OS completely and installing 10.04 over it instead of upgrading to 10.04 though the update management?

---

### Post by sports fan Matt on 2010-04-09
I agree with QIII.  I figure from here on out there may not be so much to break.  I think I joined at the 1st alpha, and other then an issue that affected everyone (can't remember what it was) everything has gone smoothly.  

With that said, I've played with upgrades since Gutsy and I think I'm going to do LTS to LTS for the foreseeable future.  There isn't much on here that is necessary for a work environment but I'm tired of testing, to me it's time to leave it alone.  :)

---

### Post by QIII on 2010-04-09
> **oleink said:**
> Do you mean when 10.04 final release comes out youd suggest getting rid of this OS completely and installing 10.04 over it instead of upgrading to 10.04 though the update management?

No.  What I am saying is that since you came in on Beta 2, the likely differences -- barring any show stopping problems you have in the mean time -- are likely to be small enough that doing your regular upgrade and dist-upgrade will be quite sufficient to keep up with the Final.

If you have some terrible problems right now, those may persist when doing upgrades.  If upgrades fix them, no problem.  Don't reinstall.  If upgrades don't fix them, just be prepared to install the Final release.

In effect, upgrades and dist-upgrades from this point forward will leave you with the Final Release by the time we get there.

(Just thought I'd throw this in here:

There is some confusion on dist-upgrade.  It does not automatically upgrade you to the next version.  So long as you DO NOT use the "-d" switch and accidentally upgrade to the next development version, dist-upgrade will maintain your current sources list (in this case Lucid) and upgrade distribution specific items. I usually do an upgrade and a dist-upgrade when that is finished.)

---

### Post by oleink on 2010-04-10
Gotcha thanks

---

### Post by linuxrockz on 2010-04-11
Thanks a lot QIII, but now I have rolled back to karmickoala. 
Actually my computer became unusable. 
The broken pipe messages and blank screens got on my nerves.
My computer won't check disc beyond 73%.
Network Manager stopped working.
Regular ubuntu one crashes.
I got around all these with workarounds but I need to study and I was there all day long in front of my pc thinking of workarounds.

Now I need peace of mind. :lolflag:

But using the beta versions does make u discover many things at the cost of Convenience :)

I have reported a few already reported bugs (Increasing the number of users affected by bugs :P)

But I do agree that lucid is way ahead of karmic :guitar:.

Waiting for the final release.

Bye.

---

