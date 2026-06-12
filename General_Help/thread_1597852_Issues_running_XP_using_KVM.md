---
title: "Issues running XP using KVM"
date: 2010-10-15
forum: General Help
---

### Post by jaksun5 on 2010-10-15
Guys,

I'm a relative noob that's been using 9.04 for about 9 months, and 10.04 for about 1 or 2. In trying to use a couple of old Windows apps I've found WINE to be helpful, but I hit a wall with the Australian Tax Office's eTax app not playing well in WINE, so I decided to run an XP virtual machine (I have a license with my notebook anyway).

I turned to KVM since it's the recommended app it appears (correct me if I'm mistaken, please).

After installing kvm and virt-manager I had a hard time getting XP to install until I ran virt-manager as root, then the installation crawled (I have a core duo 1.66 with 1.5Gb RAM and 64Mb SSD, and I allocated 1 core and 512mb with 4.0Gb for the partition). I've installed XP probably 100 times on a range of hardware and it's never been this slow to install.

Once I installed it I couldn't reboot the vm (error says it's not a supported feature, which confuses me as to why it's there in virt-manager). When I shut down and came back a few days later, it advised that it couldn't see /dev/sr0. I understood this to be the CD-ROM, so I changed the boot drive to the hard disk, and it just boots to a black screen. I then changed back to boot from the CD-ROM, and sure enough I see the 'starting seabios' post screen and then it tells me that I'm booting from CD with the usual windows 'Press any key to boot...' which I allow to pass. At that point I get the 'We apologise for the inconvenience..' screen that you get when you haven't shut down windows properly, but when I select anything it just freezes.

Hence I have some questions (and am appreciative of any further help that you might provide):

1. Why does it need to boot to the cd drive?
2. Why won't it boot directly from the hard drive? It only does this when the cd-rom has timed out?
3. Why does the boot from cd-rom then timeout act differently to the boot from hard drive?
4. Why does the 'reboot' feature appear if it doesn't work?
5. The 'shutdown' feature doesn't work for me either (it appears to do nothing)
6. I tried to start XP in safemode and it hangs at mup.sys. On traditional hardware I'd have assumed that the OS had become corrupt, and one of the reasons for this could be unclean shutdowns so this could be my own doing, but I refer back to points 5 and 6.

I hope I have been thorough without harping on, but if anyone could help me with this that would be grandiose.

thanks!

---

### Post by jaksun5 on 2010-10-17
60 views and no suggestions?

---

### Post by ronnielsen1 on 2010-10-17
I'd recommend Virtualbox (available in synaptic)

---

### Post by yetiman64 on 2010-10-17
> **ronnielsen1 said:**
> I'd recommend Virtualbox (available in synaptic)

+1,  I have used XP in Virtualbox and found it nearly as good as a full install. If you set it up I'd suggest you allocate 2 cores to XP to try avoid the "crawling" installation effect. You're figure of 512MB RAM for XP sounds good. 
Personally I prefer the PUEL version from the website over the OSE version in the repos because of the support for USB.  [--available here--]("http://www.virtualbox.org/wiki/Linux_Downloads")

I don't have any knowledge of or experience with KVM to help with the rest of your post.

Re > 60 views and no suggestions?     , the viewers may be like me with regard to the last sentence above. I find its generally a case of, if a helper is capable of assisting they usually will in here. Remember, everyone here is a volunteer with varying levels of knowledge and skills. Patience is a virtue ;).

---

### Post by jaksun5 on 2010-10-22
Thanks guys, tried virtualbox and it's much more intuitive and easier to use (at least for an ex-windows person) than KVM.

Still if anyone knows any of the above answers I'd be curious to know.

---

