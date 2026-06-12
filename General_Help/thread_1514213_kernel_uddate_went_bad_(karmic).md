---
title: "kernel uddate went bad (karmic)"
date: 2010-06-20
forum: General Help
---

### Post by max1e6 on 2010-06-20
Today I decided to pay attention to the Update Manager and I marked many of the recommendations. One was a new kernel. At reboot I had the new kernel at the top of the list:
Ubuntu, Linux 2.6.31-22 Generic.

When selected, the computer barked “error you need to load the kernel first”

I pick the old kernel (Ubuntu, Linux 2.6.31-20 Generic) and I'm back in business. (Thanks Ubuntu for giving me that option.) I don't think I want to fuss with the new kernel. Can I get it off my boot menu by marking it for removal from the Synaptic package Manager? I'm scarred to just do this because when I mark “Linux-image 2.6.31.22-Generic” for removal it auto-selects “Linux-image-Generic” for removal also. I don't want more things to go wrong.

I thought that simply doing what the Update Manager recommended that everything would work out. Did I not do something I was supposed to do? Can I not trust the Update Manager?

---

### Post by XSAlliN on 2010-06-20
I don't think removes it ( the older kernel). I've done many kernel updates and always had the older ones as option to boot from them, unless I clean them "manually'. 

Now (for example) I use an unsupported Kernel as in 2.6.34 (updates related) and all works nice, yet I have the default as alternative, even updated at least 3 times so far.

=====

Yet generally speaking (since you're new at this) - I would recommend you wait about week until updating to the a new kernel and browse the forum for problems related to that version. If all is fine you can go on, if not they'll probably release a new version one that's fixed.

But for me it's safer, since I know a thing or two about what can go wrong and how to stay on the safe side, or even resolve a problem if things go badly wrong. The linux Kernel is the core of Linux - most major updates come from that so I like to keep my system updated. I never use beta or rc versions, don't even bother testing them - but if I can move to latest stable kernel I'll do it just for the fun of it (can't wait for 2.6.35) :). :guitar:

I have newer hardware, and that's why it's so important.

---

### Post by max1e6 on 2010-06-21
Say something just went wrong with my update (somehow). If after a couple of weeks I go to the Synaptic Package Manager and re-install the new kernel, would that clear it up?.

I can leave the new kernel in the boot list for a while but I hate to have the dead-end entry in my grub loader (especially as the default). I am reasonably proficient in working out Ubuntu problems (mostly because I have found great tutorials in this forum and other resources I have found from Google).

The fear I have with this system is that I finally have it configured with various (complicated) work-arounds so that it works like a charm doing some pretty fancy tasks. It would be a real downer for me if I get locked-out and have to re-invent the wheel.

---

### Post by max1e6 on 2010-06-21
Still stuck. Anyone?

---

### Post by max1e6 on 2010-06-22
Just for the knowledge base.

Got it.

It's a WUBI

Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawik...lems:Wubi_9.10](http://sourceforge.net/apps/mediawik...lems:Wubi_9.10)

---

