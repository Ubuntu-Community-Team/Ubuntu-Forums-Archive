---
title: "where to store system, home and swap partitions on two disks"
date: 2010-12-22
forum: General Help
---

### Post by tanoloco on 2010-12-22
Hi,

I have got 2 disks available and would like to create 3 main partitions: one for file system (maverick), one for home folder and one for linux swap.

I read many howtos and now I feel more confused!  ](*,)

I would like to obtain the more efficient solution in order of speed (performance): as far as I can understand (not so far) .. it seems that the best choice is:

> disk 1: [COLOR=Blue][beginning][/COLOR] **ubuntu** | **home** | others [COLOR=Blue][end][/COLOR]
disk 2: [COLOR=Blue][beginning][/COLOR] **swap** | others [COLOR=Blue][end][/COLOR] My situation now is, according to guides I read before:
> disk 1: [COLOR=Blue][beginning][/COLOR] **ubuntu** | others [COLOR=Blue][end][/COLOR]
disk 2: [COLOR=Blue][beginning][/COLOR] **home** | others | **swap** [COLOR=Blue][end][/COLOR] now .. before moving all my staff .. what's your best suggestion?

I thought to have understood that ubuntu use swap only for hibernation / suspend activities,
and therefore it's recommendable to put the system at the beginning of one disk, and the home folder at the beginning of a second disk in order to have quickly two disk reading / writing on the right position without moving too much and spend time.

But now I'm confused because it seems that ubuntu DOES use swap for normal activity (and so it's better to put it) at the beginning of a second disk. :confused:

Could anyone help me in understanding better please? I always saw my swap next to zero during my activities .. is ubuntu using swap like windows with pagefile.sys?

Thank you in advance

---

### Post by JKyleOKC on 2010-12-22
Your present setup looks perfectly good to me. In most systems with adequate amounts of RAM (more than 512 MB), the swap partition is hardly ever used except for hibernation. And when you hibernate, response speed really isn't a major concern.

Since you say that most of the time you see swap using almost no space at all, there's really no need to be concerned about it. You can search the site for "swappiness" if you want to reduce its use even more, but if evewrything is working properly with your existing setup I wouldn't change it.

To answer your question about similarity to Windows' pagefile.sys, while the purpose is similar, the usage is rather different. The Windows approach is to fill RAM as much as possible with programs, then swap them out as needed to make room for data. The Linux approach is to load only the programs that are needed into RAM, leaving space for data and to use as disk cache areas. Thus it doesn't need to swap nearly as often. In fact some users who have more than 2 or 3 GB of RAM don't configure a swap partition at all (but I think that's a bit extreme, like doing trapeze stunts without a safety net)...

---

