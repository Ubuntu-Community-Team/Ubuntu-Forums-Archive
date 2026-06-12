---
title: "Update Manager, &quot;292 updates available&quot;, Partial Upgrade?"
date: 2011-04-27
forum: General Help
---

### Post by Simon G Best on 2011-04-27
Today I find that Update Manager tells me that there are "292 updates available", and it comes up with a dialogue box that says the following:-

> **Not all updates can be installed**

Run a partial upgrade, to install as many updates as possible.

This can be caused by:
* A previous upgrade which didn't complete
* Problems with some of the installed software
* Unofficial software packages not provided by Ubuntu
* Normal changes of a pre-release version of Ubuntu

And then it has two buttons: "Partial Upgrade" and "Close".

I did click on "Partial Upgrade", thinking it would simply be a lot of *updates*, but it then appeared that it really was some kind of *upgrade*, as if it's a distribution upgrade.

Has something gone wrong in relation to the imminency of Natty Narwhal?

Does anyone know what's going on?  Is this normal (though I've never seen it before)?  Is it some sort of distribution upgrade?  What would happen if I went ahead with it?

---

### Post by KegHead on 2011-04-27
Hi!

Try in terminal:

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Restart

advise

KegHead

---

### Post by Simon G Best on 2011-04-27
Thanks, but I'd rather not start doing that stuff until I know what's going on.

---

### Post by KegHead on 2011-04-27
Hi!

It's one possible solution.

[COLOR="Red"]No harm or foul[/COLOR]

KegHead

---

### Post by Simon G Best on 2011-04-27
Okay, my original post wasn't very clear, so I've added the following clarification:-

Does anyone know what's going on? Is this normal (though I've never seen it before)? Is it some sort of distribution upgrade? What would happen if I went ahead with it?

Basically, the problem is that it's not clear to me what's going on, and that's why I'm asking about it here.

---

### Post by Joe of loath on 2011-04-27
I've seen it before. Usually nothing to worry about, it's normally to do with extra repositories, and maybe major changes in software version number.

If you didn't ask it to upgrade, it won't, so don't worry!

---

### Post by Mashepherd on 2011-04-27
I was having the same problem, in fact it was telling me this for about a month until this morning when I simply removed the wine PPA from software sources.

I did this because I noticed that aside from all the updates it was telling me that were available, wine was always there as an 'Extra Upgrade' available but would never allow me to tick it's box. So I disabled the extra wine repository that I assume I had manually added at some point in the past, and refreshed the update manager.

This got rid of the partial upgrade notification and everything has been hunckydory every since; if for you its not wine's PPA then it will probably be another software source that you have manually added in the past, have a look at the list of upgrades your upgrade manager tells you are available and check them against the list of software sources in 'System->Administration->Software Sources'.

Hope this is of use and its not to far of the mark as to what your problem is

---

### Post by plucky on 2011-04-27
> **Simon G Best said:**
> Okay, my original post wasn't very clear, so I've added the following clarification:-

Does anyone know what's going on? Is this normal (though I've never seen it before)? Is it some sort of distribution upgrade? What would happen if I went ahead with it?

Basically, the problem is that it's not clear to me what's going on, and that's why I'm asking about it here.

Normally it some some missing dependency for a package.

If you go through the list,you should find one or more packages are not ticked in the list.This is why it is offering you the "Partial Upgrade".

I normally just let it run the updates,not the partial upgrade, and then from a terminal run ```
sudo apt-get dist-upgrade
``` which,if it can fix the dependency problem,will install the rest of the upgrades.

Good Luck

---

### Post by Simon G Best on 2011-04-27
> **plucky said:**
> Normally it some some missing dependency for a package.

If you go through the list,you should find one or more packages are not ticked in the list.This is why it is offering you the "Partial Upgrade".

Yes, I'd noticed that.

> I normally just let it run the updates,not the partial upgrade, and then from a terminal run ```
sudo apt-get dist-upgrade
``` which,if it can fix the dependency problem,will install the rest of the upgrades.

Good Luck

Thanks for your post.

I'm still wondering what the "partial upgrade" is.  It sounds like it's not simply a bunch of updates, but more like a distribution upgrade.  But it's not telling me that a new distribution is available the way it usually does for distribution upgrades.

I'll try updating just a few packages, and see how that goes.

---

### Post by Simon G Best on 2011-04-29
I ended up applying the updates in Synaptic.  That seems to have worked, and didn't appear to omit any upgradeable packages.  It seems I now have an up-to-date Xubuntu 10.10 system.  (Almost all the package updates were for KDE packages.)

I think I can now mark this as "solved".

---

