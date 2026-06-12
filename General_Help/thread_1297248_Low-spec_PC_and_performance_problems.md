---
title: "Low-spec PC and performance problems"
date: 2009-10-21
forum: General Help
---

### Post by Rhapsody on 2009-10-21
We've got two PCs here, a high-sped Core 2 Duo and a low-spec AMD Sempron. Both have their problems, but this topic is about the latter.

_**Chihiro_**
AMD Sempron 2800+ (1.6Ghz)
512MB RAM (64MB taken by integrated graphics, so 448MB available)
Integrated GeForce6 (no idea whether it's high or low-end)
Ubuntu 9.04 (using GNOME)

I know it really needs more RAM (I'm considering an extra 512MB, if it's cheap enough) but I want to see if there's anything I can do right now to alleviate the worst of the performance problems.

Chihiro is a typical 'Facebook machine' and spends most of her time with Firefox (3.0.x) and Thunderbird (2.0.0.x) open. Despite this, Firefox finds ways to use as much as 80% of the system's RAM, and things frequently slow to an absolute crawl. This seems mostly due to Flash games (my mum frequently has two or three open at once and forgets to close them, despite my attempts to get her to do this).

I've thought of numerous possibilities, which I'll run by you to see what you think of them.

**_Try to tweak Firefox_**

This is obvious, since Firefox is causing the performance issues in the first place (and it's always had a reputation with me as a serious memory hog). But aside from removing unneeded extensions (I think we only have three or four to start with) I can't think of anything else to do. Any suggestions about how to make Firefox less resource-hungry?

**_Switch to a different browser_**

Another obvious one, but it'd need to have several features taken for granted right now with Firefox. Chief among these is compatibility with banking sites, then ability to use Flash, followed by a reliable and low-maintenance ad-blocker.

**_Flash alternatives_**

This one is more radical, but do Gnash or Swfdec use less resources than regular Flash? Either way, they'd need to work with a 'Test Suite' of at least three Facebook applications and the ever-present YouTube, and neither seemed up to anything like that standard when I last tried them.

**_New desktop environment_**

This is probably least likely to help, but worth a look anyway. I've been considering Xfce or even LXDE, but GNOME seems to be working well and I don't really want to mess with it now.

Feel free to add anything I didn't think of.

---

### Post by Quantux on 2009-10-21
The integrated video is likely the 6100, which is fine for what you use the pc for. Firefox can and will eat ram,so really if you've got that much stuff going on in the browser, it'll be a hog (I typically see ~100MB usage at most with FF on any platform when dealing with flash). So really, add a stick of 512 (newegg has them for $10-$15 depending on type and speed, and if it's ddr2, 2GB is only about $20-$25) and you will see a huge difference. The flash alternatives don't really work yet, gnash will play youtube video's, but thats about it (and they look pretty bad). Switching to XFCE will see some benefits, but nothing close to what that stick of ram will do.

---

### Post by Rhapsody on 2009-10-21
> **Quantux said:**
> So really, add a stick of 512 (newegg has them for $10-$15 depending on type and speed, and if it's ddr2, 2GB is only about $20-$25) and you will see a huge difference.
I'm going to be looking that up, but I'll have to see if I can dig out the motherboard manual and figure out what sort of RAM I actually need.

Also, funny that you also mention 2GB. That's exactly the amount I'm thinking of adding to this PC (the Core 2 Duo, which already has 2GB, so that would double me up to 4GB). I think I've learned my lesson for when I build my sixth PC...

> **Quantux said:**
> The flash alternatives don't really work yet, gnash will play youtube video's, but thats about it (and they look pretty bad).
I thought so, standard Flash will have to stay for now then.

> **Quantux said:**
> Switching to XFCE will see some benefits, but nothing close to what that stick of ram will do.
I may give Xubuntu a try in a virtual machine, see how it looks and feels. Squeezing a bit more responsiveness out of Chihiro would be a very good thing.

---

### Post by Sylslay on 2009-10-21
1 Tommorow is RC of Karmic Koala. Ubuntu 9.10, 
Is much faster on intel chipsest, but I don't how perform on Nvidia Chiepset. (but got new set of grapic driver)
I thinking that Yours Low Spec is still ok.And gnome should wrok great.


I tweak my firefox too, temporally,,
switched off history off browsing, so firefox is not using hardrive and work much faster than I opened 12 tab at some time,,, very quick
This "tweak" is for now ok, but not for forever.:)

2 Check System/Administration/Hardwere drivers, is any driver aviable from Nvidia (close source)

---

