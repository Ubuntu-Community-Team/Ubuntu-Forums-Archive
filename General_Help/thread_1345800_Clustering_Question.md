---
title: "Clustering Question"
date: 2009-12-04
forum: General Help
---

### Post by djbushido on 2009-12-04
I apologize to the moderators: I'm not sure where this topic should go, so I put it in general.
That being said, I'm trying to set up a cluster computer. The end result is hopefully video editing, probably with Windows. Is it possible to set up a Linux cluster to run a virtual computer to run Windows/video editing? Or do I have to do this all with Windows? I apologize for the n00bishness, but I really have no experience with parallel computing.

---

### Post by Torrilin on 2009-12-04
What exactly are you planning to do that makes you think you need a supercomputer for your video editing? If you can give us a clearer statement of the problem, odds are there's a way to address it.

---

### Post by djbushido on 2009-12-04
Supercomputer? only looking at chaining 5-6.
Anyway, some people I hang out with are trying to do video editing, only the computer they have is 1. Slow. 2. Not enough RAM. While the ram can be used from other computers, the budget is effectively nil, meaning no processor upgrade. I'm trying to do this to run Pinnacle Studio, which as far as I know is Windows only. So I didn't know if something like a VM to run windows could be run in parallel, or if I need to learn Windows Server.
Happy to provide as much info as I have access to.

---

### Post by Iowan on 2009-12-04
[Here]("https://help.ubuntu.com/community/Clustering") is a help page on clustering.

---

### Post by djbushido on 2009-12-04
Awesome!
May take a week to get back to you, this is a fairly length process.
Anyway, it looks like (once I get a network switch) I can get this up and running and then use a virtual machine for the editing.
Does RAM get shared among machines, or do I need to put extra RAM on the host?

---

### Post by Torrilin on 2009-12-05
Yep. Supercomputer :). Doesn't matter how many nodes, once you're doing a parallel setup like a beowulf cluster, it's a supercomputer in terms of how you have to program it. (I know a lot of Paradyn and Condor coders, so I've picked up a fair bit just by osmosis)

Most Windows software is set up for a single machine. The software will not effectively take advantage of parallel processing. And running Windows software in a VM will typically add at least one extra layer of processing, so if it was already pretty borderline useful, it's not gonna get better in a VM. It looks like Pinnacle Studio is fairly equivalent to things like iMovie on the Mac... not a high end video tool, and definitely unlikely to be helped by much besides more RAM.

It might be worth poking around in the Multimedia Production forum to see if there are Open Source tools that would help. I know the folks there tend to be more aimed at music, but I also know that for some visual problems there are some very good Open Source tools available. A lot will depend on exactly what they're trying to do, and how technically skilled they are. One of the most effective ways to speed up visual production problems is to break the job up into smaller pieces... but not all visual production tasks *can* get broken up. And sometimes you can't see how to break it up into pieces without being damn good with visual production.

---

