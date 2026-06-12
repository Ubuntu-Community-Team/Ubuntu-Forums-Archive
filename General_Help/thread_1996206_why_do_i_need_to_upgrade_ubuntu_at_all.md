---
title: "why do i need to upgrade ubuntu at all?"
date: 2012-06-04
forum: General Help
---

### Post by jinjin on 2012-06-04
hi all i just want to know why do i ever need to upgrade my ubuntu at all?  people say it's because you can get new software.   but what's the point if all the software i need are available via PPAs?  so i don't need new drivers because everything is working fine with me.  security updates don't even do much for me so i don't see the point in upgrading for that.    for me stability  is the key issue.  the reason i'm asking is because i was using ubuntu 10.04 and it was very stable for me but then i upgraded to 12.04 and it's very unstable, lots of bugs and i'm thinking of going back to 10.04

so for a person like me, do i even need to upgrade at all?  technically, even if they stop supporting 10.04 in april 2013 and i'm still using it,  couldn't i just get what i need via PPAs and not have to upgrade at all?

i need some help on this before deciding to go back to 10.04 or not!

---

### Post by Los Frijoles on 2012-06-04
For me the main reason is kernel updates. A main reason to upgrade at least my desktop to 12.04 was because of the increased Sandy Bridge support that came with using the 3.2.x kernels.

If you really wanted to run it without ever updating you would be ok, but if they discovered a critical bug in, lets say, your internet browser and the update repositories were no longer available you would then have to compile the browser from source. To do that you would have to make sure you had all its build dependencies installed. That is much more difficult to do without being able to use the package manager since if you didn't already have the library installed from before they discontinued support you would also have to download that and compile it from source (and in the process doing the same thing along its dependency tree).

The advantage of keeping up with the upgrades is that you get the package manager to do all the dependency tracking for you and you don't have to go and build everything (which takes a TON of hard drive space...The OGRE 3D rendering library was several gigabytes in object files when I compiled it one day...imagine that for all of your libraries).

Ubuntu 12.04 is an LTS release, so it should end up being more stable in the long run (at the moment my computer is less stable because of a suspend-resume crash problem but once they get all the bugs ironed out it should be good) since they are going to support it for 5 years.

---

### Post by wilee-nilee on 2012-06-04
> **jinjin said:**
> hi all i just want to know why do i ever need to upgrade my ubuntu at all?  people say it's because you can get new software.   but what's the point if all the software i need are available via PPAs?  so i don't need new drivers because everything is working fine with me.  security updates don't even do much for me so i don't see the point in upgrading for that.    for me stability  is the key issue.  the reason i'm asking is because i was using ubuntu 10.04 and it was very stable for me but then i upgraded to 12.04 and it's very unstable, lots of bugs and i'm thinking of going back to 10.04

so for a person like me, do i even need to upgrade at all?  technically, even if they stop supporting 10.04 in april 2013 and i'm still using it,  couldn't i just get what i need via PPAs and not have to upgrade at all?

i need some help on this before deciding to go back to 10.04 or not!

The only thing I would say is that an upgrade from lucid to precise is a big jump in how the OS has changed, if it is unstable I suspect it was the upgrade. If you had a fresh install I suspect as well here you would have a set up that works.

I have seen numerous up graders that were still using PPA's that were not supported in 12.04.

PPA's although I have never had a problem are considered unstable, not a real solid justification.

You don't really have to upgrade until the release goes end of life anyway. Precise is covered for 5 years now.

---

### Post by jinjin on 2012-06-04
> **wilee-nilee said:**
> The only thing I would say is that an upgrade from lucid to precise is a big jump in how the OS has changed, if it is unstable I suspect it was the upgrade. If you had a fresh install I suspect as well here you would have a set up that works.

I have seen numerous up graders that were still using PPA's that were not supported in 12.04.

PPA's although I have never had a problem are considered unstable, not a real solid justification.

You don't really have to upgrade until the release goes end of life anyway. Precise is covered for 5 years now.

when i said upgrade, i meant i upgraded from 10.04 to 12.04 by reformatting and doing a fresh install off the 12.04 DISC, not the upgrade manager.  sorry that i did not clarify.   i don't know, i just might downgrade and then wait 12.04 to be more stable or maybe a better version to upgrade, cause right now 12.04 is giving me one bug after another, for example my sound was just working fine and now it's not working and i can't find a solution that works on google...

---

### Post by wilee-nilee on 2012-06-04
> **jinjin said:**
> when i said upgrade, i meant i upgraded from 10.04 to 12.04 by reformatting and doing a fresh install off the 12.04 DISC, not the upgrade manager.  sorry that i did not clarify.   i don't know, i just might downgrade and then wait 12.04 to be more stable or maybe a better version to upgrade, cause right now 12.04 is giving me one bug after another, for example my sound was just working fine and now it's not working and i can't find a solution that works on google...

I have seen people periodically on the IRC freenode #ubuntu channel with no sound, problems, you might try there, go on during daytime US/British time.

You might try a thread on the forum as well, it would be nice to see you have everything working. :)

---

### Post by Peripheral Visionary on 2012-06-04
In reply to the *original* question, no, [COLOR=Purple]**upgrading is not mandatory!**[/COLOR] If it works wonderfully and you love it, then keep using it! Even after security updates end, if you use your computer like most home users do (for web browsing, email, listening to music, writing papers and letters, etc), even "security" updates aren't any big deal. Hardy Heron, 8.04, is still in use by a lot of folks with old old ooollllld hardware and the users love it (see the Testimonials section).

Fortunately 12.04 is even faster on my old computer than Lucid was and I don't have to remove PulseAudio now, as before with Lucid. The upgrade actually solved a few problems that I experienced "out of the box" with Lucid. But for others, 10.04 has been the pinnacle, the absolute best 'buntu ever. Love it? Keep it!

---

### Post by inashdeen on 2012-06-04
My own personal opinion is that, it depends. are you comfortable with your current system. I got friends who didnt upgrade their system since 8.04, but as time goes by, you may need to use better software like gimp 2.8 for example, which i am not sure could run on 8.04. so at this point, if such programs really matter to you, you have no choice but to upgrade, but you don't need em, example you are comfortable in using an existing older version of mozilla, there is no question of why you shouldn't keep your system static.

---

### Post by 3rdalbum on 2012-06-04
You can certainly keep 10.04 for nearly another year. After that, it no longer gets security updates; I definitely would update or install a newer Linux distro in April 2013.

Linux isn't very backward-compatible, so eventually (soon?) new programs will not even be able to compile or run on 10.04. At that point, they will no longer be available in a PPA for 10.04. Or, if a maintainer of a PPA decides to stop compiling for 10.04, it will disappear then.

If 12.04 is unstable for you, then you may want to do a proper RAM test. Take out some of your RAM and see if your system works with the stability you should expect, and then you can narrow it down to a specific stick that's causing problems. Ubuntu 12.04 should not be unstable, but bad hardware can cause problems. And it's usually bad RAM, because RAM isn't made to the same quality it used to be.

---

### Post by 3Miro on 2012-06-04
Of course 10.04 is stable, for two years people have been working on it to clean all the possible bugs. Of course 12.04 is unstable, it just came out.

Check out the old threads on how many people were complaining about 10.04 when it first came out.

If you wanted stability and stability only, you should have waited a few more months before upgrade. There is a reason why LTS releases have a year of overlap, it is there so you can wait until most of the major bugs have been cleaned before you upgrade.

Check the state of 12.04 in six moths or so, it will be ultra stable.

---

### Post by inashdeen on 2012-06-04
I agree and second what 3miro had said. if now it it debian, 10.04 should be called old stable. 10.04 still undergo improvement process after it has been release. 12.04 too will go through the same process. hence, it's not that easy to compare between a newly released OS to something that has been too mature.

---

### Post by buzzingrobot on 2012-06-04
If you are happy with 10.04, you have no real reason to move on.

That said, I would install all the available updates for 10.04.  They do fix bugs, add functionality, and close security holes.

---

### Post by inashdeen on 2012-06-04
up to buzzingrobot . agree :)

---

