---
title: "Boot options"
date: 2005-01-20
forum: General Help
---

### Post by Swazi on 2005-01-20
Hi

Is there a way to insert boot options with the live cd like there is in knoppix ?

"xmodule=fbdev" for example 

I just get a blank screen when X starts and have tried every avaiable option. Ubuntu picks up my Nvidia card as "nv" but that does not help.

---

### Post by misGnomer on 2005-01-21
I booted the[ **Gnoppix** hoary_0.9.3b**2**-i386.iso](http://source.rfc822.org/pub/local/gnoppix/gnoppix/beta/) successfully using *xmodule=radeon*.

OTOH on my hardware I must also use "noapic" and/or "acpi=off" to get off the ground so your blank screen problem might be caused by something else than the display driver as well.

Which version of the live CD are you trying?

---

### Post by Swazi on 2005-01-21
I am using Warty.

Where and how exactly did you type in "xmodule=raedon"

I cannot see where to type this in.

---

### Post by misGnomer on 2005-01-21
Oh, the "old" Warty live CD?  :-)

It's been a while and I can't remember how I booted it up. In any case it never worked properly for me and it was more of a technology preview (now in process of being rewritten and to use Hoary).

Perhaps someone who's stuck with the Warty live CD could help you out here.

Alternatively you could either wait for the *official* Ubuntu Hoary live CD *betas* to show up, or you could try one of the following:

1) [The in-development (daily alpha builds) of Hoary live CD](http://cdimage.ubuntu.com/daily-live/)

2) [The Ubuntu-like Gnoppix "Hoary" live CD betas](http://source.rfc822.org/pub/local/gnoppix/gnoppix/beta/) (the 0.9.3b**2**-i386.iso worked well here, but for some reason the new 0.9.3b**3**-i386.iso is a lot smaller...)

3) Finally there's the recent [Xfce-based version of MorphixCombined-LightGUI-0.5-pre4.iso](http://prdownloads.sourceforge.net/morphix) (no recent Gnome version is available yet though) which is light-weight and worked great here. It's no Ubuntu (although Morphix collaborates with Ubuntu on live CD development at some level) but it's an interesting option anyhow.

---

