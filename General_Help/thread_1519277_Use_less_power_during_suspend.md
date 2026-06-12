---
title: "Use less power during suspend"
date: 2010-06-27
forum: General Help
---

### Post by pytheas22 on 2010-06-27
If I suspend my netbook for about twelve hours without plugging it into a power source, the battery loses about 10% capacity while it's suspended.  That seems like kind of a lot to me, given that the 6-cell battery provides as much as 8 hours of life when the computer is turned on.

So I'm wondering if there's a way to make my computer draw less power when it's suspended.  I don't know enough about low-level stuff to know exactly what happens when the system suspends, but my basic understanding is that everything shuts off except the RAM, which stays charged.  And I'm thinking there might be a way to minimize the amount of energy that the RAM needs to use.

For instance, is there perhaps a way to dump everything from memory that's not actually essential just before suspending, so that only 500 megabytes' worth of RAM needs to be powered instead of the full 2 gigabytes?  Maybe this doesn't make sense, but it seems like it could, depending on how exactly suspend-to-ram works.

I know, I know, I could just hibernate it forever, but that doesn't work on this computer because I don't have a swap partition (also not a great idea, but the solid-state hard disk is only 16 gigabytes so I didn't have much room to spare when partitioning).

Anyway, any insights or thoughts on what I could experiment with would be appreciated.

---

### Post by psusi on 2010-06-27
10% over 12 hours is pretty good for suspend, and no, there isn't anything you can do to make it better other than switch to hibernate.

---

### Post by dcstar on 2010-06-28
> **psusi said:**
> 10% over 12 hours is pretty good for suspend, and no, there isn't anything you can do to make it better other than switch to hibernate.

Pull out half the RAM and there will be less to keep powered up.....  ;-)

---

