---
title: "Mass Image Ubuntu?"
date: 2011-08-25
forum: General Help
---

### Post by Roasted on 2011-08-25
Currently we utilize FOG (based on Linux) to image our Windows systems. Think Norton Ghost, except free, open source, and quite a bit better.

On the flip side, we're beginning to tinker with Ubuntu in replacement of the Windows installs. Problem is, FOG was geared specifically for Windows imaging. So far I have yet to get FOG working with Ubuntu.

I've heard about Clonezilla.  Yes, the Live version is great. The server version is nothing short of an absolute headache to set up. Assuming you can even completely set it up...

That said, I've also heard a lot about preseeding. Something about utilizing Remastersys to make a custom ISO of your current base install and then using that ISO to be pushed out over the network via PXE boot and preseed. Thing is, when I look this up, each guide I find is wildly different and each one looks incredibly confusing.

Is there one centralized guide that is good to use for preseeding? Or would you guys recommend I look elsewhere for mass imaging systems? Nothing via USB or CD. It has to be done over the network so I can do upwards of 30 at a time in a timely manner.

Any thoughts?

---

### Post by TeoBigusGeekus on 2011-08-25
Just a thought: what about dd?

---

### Post by Basher101 on 2011-08-25
Depending on your ubuntu install size, Remastersys is the best choice. It creates a Live CD image of your WHOLE ubuntu install and you can burn it to a DVD and simply follow the usual installation progress when you want to restore it.

(for the depending size, Remastersys cannot create a live CD image larger than 4gb, as it has to fit a dvd. So far i backed up 10gb that resulted in a slightly under 2gb iso, so i think it can back up a maximum of 20 gb, not sure tho)

---

### Post by Roasted on 2011-08-26
> **Basher101 said:**
> Depending on your ubuntu install size, Remastersys is the best choice. It creates a Live CD image of your WHOLE ubuntu install and you can burn it to a DVD and simply follow the usual installation progress when you want to restore it.

(for the depending size, Remastersys cannot create a live CD image larger than 4gb, as it has to fit a dvd. So far i backed up 10gb that resulted in a slightly under 2gb iso, so i think it can back up a maximum of 20 gb, not sure tho)

That sounds... somewhat do-able. Problem is, what about when we have 2,000 systems we need to redo in batches of 30? I'd prefer to have a network based solution so we can hook the systems up to a secluded LAN with a gigabit switch so I can just blast them.

These are laptops, so mobility is easy. That way I can just stack them up on the bench and go to town. Sure, a bunch of custom DVDs might be somewhat do-able. In fact, in a lot of situations it'd probably be completely awesome. But in a severe time crunch "go go go!" type of situation, I'm wondering about making it a little more automated and/or faster.

Sure, I could remastersys to a USB install I suppose? But even still... 

Any additional thoughts? Thanks for the input!

---

### Post by christopher.wortman on 2011-08-26
> **Roasted said:**
> That sounds... somewhat do-able. Problem is, what about when we have 2,000 systems we need to redo in batches of 30? I'd prefer to have a network based solution so we can hook the systems up to a secluded LAN with a gigabit switch so I can just blast them.

These are laptops, so mobility is easy. That way I can just stack them up on the bench and go to town. Sure, a bunch of custom DVDs might be somewhat do-able. In fact, in a lot of situations it'd probably be completely awesome. But in a severe time crunch "go go go!" type of situation, I'm wondering about making it a little more automated and/or faster.

Sure, I could remastersys to a USB install I suppose? But even still... 

Any additional thoughts? Thanks for the input!

My thoughts are stick with Windows on the laptops. Ubuntu has power issues and is a battery hog.

Other than that, Remastersys +1

---

