---
title: "Will anything break if I suddenly start using Aptitude?"
date: 2009-10-19
forum: General Help
---

### Post by brownbat on 2009-10-19
If I being using Aptitude instead of apt-get to install programs on my laptop, will anything break?

I don't expect the video card to stop working because I use a different installer, or anything. But doesn't each system keep track of dependencies slightly differently, is each able to see the maintenance work of the other installer? Will Aptitude be able to track all those dependencies flagged by apt-get?

I don't know too much about what these do under the hood, is it safe to bounce back and forth between them?

---

### Post by -Zeus- on 2009-10-19
Aptitude and synaptic are front-ends to apt, and they all work together.  You will notice that you can't run more than one of them at once (eg, aptitude and apt-get) that's because they lock the files so they can sync them.  They all use the same system, so no worries.

---

### Post by zkriesse on 2009-10-19
> **brownbat said:**
> If I being using Aptitude instead of apt-get to install programs on my laptop, will anything break?

I don't expect the video card to stop working because I use a different installer, or anything. But doesn't each system keep track of dependencies slightly differently, is each able to see the maintenance work of the other installer? Will Aptitude be able to track all those dependencies flagged by apt-get?

I don't know too much about what these do under the hood, is it safe to bounce back and forth between them?
No, you won't or shouldn't have any issues! Apt-get and Aptitude are the same and I've used both. Never once have I had any problems.

---

### Post by Niko Johnson on 2009-10-19
there simmilar enough to not have any problems.. ive used both without ever having any problems, you should eaither

---

### Post by -Zeus- on 2009-10-19
> **Niko Johnson said:**
> there simmilar enough to not have any problems.. ive used both without ever having any problems, you should eaither
They're not "similar enough", they are two user interface systems running on the exact same foundation.

---

### Post by zkriesse on 2009-10-19
> **Niko Johnson said:**
> there simmilar enough to not have any problems.. ive used both without ever having any problems, you should eaither
Just so you know, they're not **similar** they are exactly the same thing. Two different commands using a slightly different interface but using and running on the same platform.

---

