---
title: "Home Storage Solution (ZFS alternative?) Suggestions?"
date: 2011-09-20
forum: General Help
---

### Post by Snowmirage on 2011-09-20
I've been a long time fan of Ubuntu and I am hoping the community might be able to point me in the direction of a solution that might work for a project I am playing around with.

In short I am looking to put together a cheap home storage server that will be expandable in the future with room for 12-24 drives.

Goals:

1)Cheap (~80 newegg case with room for 12 HD's is a good start, I have 4 500GB drives I can add to start with and I'll grow it from there.

2)Reliable I dont expect enterprise level fail over on every component its just my home lab, but I wont to be able to survive 1 drive failing with out loosing everything.  I also would like it to be easy to replace that failed drive.  I would also like to not rely on a specific hardware raid controller.  1st they are expensive 2nd if it goes bad you'll have a hell of a time getting to your data.

3) expandable, would like to be able to grow this later on.  Start with 4 or so drives add more as needed

4) I would like to be able to export some or all of this storage via iSCSI to my ESXi 4.1 server.  (i've done this in the past and suspect it should still work regardless)


What I have looked into.  

As I mentioned HW raids are probably out due to the limitations I mentioned.  

I have done a bit of reading on ZFS which sounds very interesting 
 and I'm sure setting it up would be a great learning experience.  I'm a bit confused on what is required for ZFS, from what i have read it was developed by SUN for Solaris (which admittedly I know little about).  From what i gather there is (was?) an open source version opensolaris?  Even if that open version is still available / supported it seems I'll probably have a hard time finding hardware that is supported.

There seems to be a linux version [http://zfsonlinux.org/](http://zfsonlinux.org/)
but from what i have read it seems to be rather young, maybe it would work maybe it wont? Not sure

There seemed to be other ZFS alternatives, I came across some talk about "butter fs"  BTRFS, but again having found out much about it yet.

Anyhow I suspect there are those out there in the community who have experimented with a similar setup.

I'd certainly appreciate any thoughts, ideas, or suggestions you might have.

Thanks

---

### Post by scarleo on 2011-09-20
You should definitely set up LVM partitioning, easy to extend anytime you want, just add more hardware and let your home folder grow by adding the available hardware space to your existing partition. I haven't done LVM on Ubuntu but I guess there is support, I have done it with openSUSE and it's really easy, you choose LVM when you install it.

The file systems you are speaking of won't exactly give you that expandability, just different type of file handling. BTW I definitely think you should pick Linux over Solaris.

Good luck!

---

### Post by aeiah on 2011-09-20
look into ZFS on netBSD or openBSD - its probably going to be the most stable solution. LVM is an option but ive had bad experiences with it when drives have failed - but that might be because they guy who implemented it made a mess of things.

---

### Post by Snowmirage on 2011-09-20
Thanks for the input

@scarleo 

Ah yes thank you LVM was one possibility I had come across years ago, but I couldn't remember what it was called so I couldn't search to do further reading.  I'll look into that,

I am frankly more concerned with the reliability than the expand-ability.

@aeiah

I'll look into that, as long as the OS can support the cheap hardware i'll be looking at that could work.

---

