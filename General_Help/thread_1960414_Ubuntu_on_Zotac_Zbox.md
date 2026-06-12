---
title: "Ubuntu on Zotac Zbox?"
date: 2012-04-17
forum: General Help
---

### Post by Eirreann on 2012-04-17
So I've been looking at this line of mini-desktops made by Zotac, called "Zboxes".  [http://www.zotacusa.com/products/mini-pcs/zbox]("http://www.zotacusa.com/products/mini-pcs/zbox")
Their very affordable, however none of them include an OS... this seemed like an awesome opportunity for a Linux enthusiast, like myself, who is trying to find an affordable PC.
So what do you guys think?  Would Ubuntu work well on one of these?  (I'm personally looking at the $230 one with Nvidia ION graphics...)

---

### Post by lykwydchykyn on 2012-04-17
I use zboxes as thin clients for an Ubuntu LTSP system at our public library.  I've been reasonably pleased with their performance, especially as they were cheaper than actual thin clients, though we aren't exactly putting them to any stress tests (they run a browser pointing to some 90's-era html).

They seem to run Ubuntu just fine, though we had to use the old "nv" driver rather than the nouveau driver (and I didn't try the proprietary drivers) -- but this is on Lucid Lynx.  Newer zboxen might work better with the newer Ubuntu releases, i couldn't say.

---

### Post by Eirreann on 2012-04-17
> **lykwydchykyn said:**
> I use zboxes as thin clients for an Ubuntu LTSP system at our public library.  I've been reasonably pleased with their performance, especially as they were cheaper than actual thin clients, though we aren't exactly putting them to any stress tests (they run a browser pointing to some 90's-era html).

They seem to run Ubuntu just fine, though we had to use the old "nv" driver rather than the nouveau driver (and I didn't try the proprietary drivers) -- but this is on Lucid Lynx.  Newer zboxen might work better with the newer Ubuntu releases, i couldn't say.
Well it's awesome that you've had experience with them!  I hadn't heard about them before today when LinusTechTips on YouTube released an overview of one.
Spec-wise, their newer models should be quite capable of handling Ubuntu; with the Intel Atom 1.73GHz processor, up to 8GB of RAM (if you upgrade yourself), and an Nvidia ION video card (or they also can feature Intel HD graphics or AMD chips...)

---

### Post by forrestcupp on 2012-04-17
I have a zbox ID11 that ran Ubuntu well. I have Win7 on it now, though.

All I can say is that you'd better hope the new zboxes are better than the one I have. Because of the way it was set up, it didn't have enough PCIe pipelines to power everything sufficiently. That means that if you're trying to do two things at once, like using wifi and hdmi, it's going to be sluggish. If everything you do is hardware accelerated with the graphics being totally handled by the GPU, this is not as much of a problem, but not everything does hardware acceleration very well. A good example of how this fleshes out is that my Zbox couldn't stream Hulu videos in full screen without being extremely choppy. I tried a very simple 2D game that wasn't hardware accelerated, and it was unplayable.

Hopefully, they've worked some of the kinks out by now. But my experience is that once you've paid for the Zbox, RAM, and hard drive, you've ended up paying more than you would for a small desktop that you could hook up to your TV that would work much, much better.

It *did* run Ubuntu fairly well, though, other than the general hardware problems I mentioned that are across the board. If you end up getting one, don't even think about using any hard drive other than a solid-state drive.

---

### Post by gordintoronto on 2012-04-17
Forrest: have you tried XBMC with the Nvidia drivers?

Oops, too late.

---

### Post by papibe on 2012-04-17
I helped my brother to set up a Zotac MAGHD-ND01 as a HTPC.

We installed Ubuntu 10.04, and XBMC. Works great. Full HD acceleration with the proprietary Nvidia driver. A tip: update the BIOS before any software installation.

The only thing that is not great is its wireless card. It works, but it is a mediocre card at best. If your media files are on a different machine or server, wired connection is the way to go.

Regards.

---

### Post by Eirreann on 2012-04-17
> **papibe said:**
> I helped my brother to set up a Zotac MAGHD-ND01 as a HTPC.

We installed Ubuntu 10.04, and XBMC. Works great. Full HD acceleration with the proprietary Nvidia driver. A tip: update the BIOS before any software installation.

The only thing that is not great is its wireless card. It works, but it is a mediocre card at best. If your media files are on a different machine or server, wired connection is the way to go.

Regards.

Interesting.... now which Zbox is that which you used; the newest one?  I can't remember any of the model numbers but there are a LOT of Zboxes on the site now.

---

### Post by papibe on 2012-04-17
It is [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856173001") one.

As yo can see, it is not longer available there. My brother bought it on March 2011.

Regards.

---

