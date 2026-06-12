---
title: "Question about multiple distros, multiple partitions."
date: 2010-03-04
forum: General Help
---

### Post by BT1 on 2010-03-04
Okay I have a netbook with a 150G Hard drive, and I wanted to really have Ubuntu Netbook because I had it on here as the only OS before I reformatted. I also found a while back that there was Kubuntu Netbook, so I decided I'd give it a shot in a natural environment meaning I wanted to see how it would run directly on my netbook to give it a fair shot. Well I was disappointed - not with the look, because that rocks better than Ubuntu Netbook, but the speed was drastically less impressive. Even the installer lagged down to a crawl, and after install I wasn't impressed enough to compile a kernel which speeds up the OS drastically.

I had my hard drive set up this way:

[15G "/"] Ubuntu Netbook
[15G "/"] Kubuntu Netbook
[115G "/home"] Home
[10G "swap"] Swap

Now I want to uninstall Kubuntu so I figure I just format the partition it's sitting on and update my grub to remove it from my Grub right? Well I have a couple of questions:

1.) Will Kubuntu leave behind any files in my "/home" directory that will mess with any installs in the future? I know that if you have root partitions and they're set up to share a home folder, some settings can be deposited there...right?

2.) In order to update Grub do I just run "sudo update-grub"?

Thanks for the assist!

---

### Post by TitanusEramius on 2010-03-04
Before you start with this, I would recommend a complete backup...

But otherwise in short: yes, no & yes.

Kubuntu will leave program-specific settings in your /home in the form of hidden folders (.folder-name). In nautilus you can manage this setting so you can see hidden folders.

I also tried Kubuntu alongside my Ubuntu, both of them on the same partition, and i did not run in to any problems when I removed Kubuntu for the same reasons as you describe.

The command for GRUB looks right, and for some reference reading you could try:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

Good luck

---

