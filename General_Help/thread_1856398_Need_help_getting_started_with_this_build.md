---
title: "Need help getting started with this build"
date: 2011-10-08
forum: General Help
---

### Post by ClientAlive on 2011-10-08
Ok, so I'm sitting here in front of my other computer also. And I'm finally ready to begin configuring a kernel for it. It's more like a build from scratch though since I'm starting with just the partitioned drive. I've been searching around on the Internet for information but I'm not certain how to get myself into the right location/ environment under these circumstances.

I have xubuntu running live on that computer (the one I'm going to compile on) and I'm trying to figure out how to chroot into the right place to begin my config, compile, and install. So, of course, xubuntu (being that it's running live) is running from my cdrom. But I need to compile onto sda (the hard disk on the machine).

Also, the way I've partitioned the disk, /boot is on it's own partition (in fact there are quite a few partitions on the disk). Also, even if I did get chrooted to the right place I wouldn't be sure how to copy the kernel source from my thumb drive in the machine to /boot on the disk. In fact, I'm not even sure there is a /boot, just a partition created for it. No folders have been created though. I don't know, I'm confuse and LFS is after a completely different objective than I am.

And even if I got through the whole compile ok, I wouldn't be sure how to get back out of chroot and shut down the machine safely when I needed to. Compiling the kernel is only a first step too, of course. Then I have to compile Gentoo and then Xen. (Well I don't have to - I know - but this is how I want to do this).

So I guess part of my problem is that I'm not sure how to navigate around as well as I'd like. I only started using Linux 6 mos or so ago. I've learned how to use the command line well enough to do everything I need to for regular every day use but this is something different.

Then there's a question whether I need to manually create the folders on the partitions or what?

I'm going to keep googling for info but I was really really hoping to get this going tonight (and it's 4:09 am where I am).

Can anyone help please?
------------------------

Edit:

Got a hardened Gentoo system going now.

---

