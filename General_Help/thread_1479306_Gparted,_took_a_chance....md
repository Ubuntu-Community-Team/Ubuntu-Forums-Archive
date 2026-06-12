---
title: "Gparted, took a chance..."
date: 2010-05-10
forum: General Help
---

### Post by User3k on 2010-05-10
Before anyone says how _***not***_ smart this is. I already know. I have all important data backed up so if I had to reinstall Ubuntu 10.04, not a big deal.

I installed Debian 5.04 (Lenny) I wanted to give it a try. I also want to install Slackware, Fedora 13 when it comes out and reinstall PC-BSD. So I needed to resize a couple of partitions, including my Ubuntu partition. So I used gparted to do this in Debian. Problem was after it resized the Ubuntu partition and made the fourth one it was trying to move the Ubuntu partition to the right, I never told it to. This would have taken almost five hours to do. So I stopped it after 2%. I got the warning that it could cause severe file damage but I still did it, (Yeah I know, but remember I had everything backed up and at this point it would have been quicker just to reinstall everything then wait five hours for it to move the Ubuntu partition, which I didn't want moved anyways.)

Now I fully expected to not be able to boot into Ubuntu or that it would freeze (or something) during boot. None of this happened. It appears that there was no damage at all, that I can see anyways.

So my questions are these. Did I get lucky? Will the damage show itself later? Should I just reinstall to be on the safe side?

---

### Post by gadolinio on 2010-05-10
Well, I don't know for sure, so I'll just give you my opinion, based on ignorance and prudence.
No matter whether you've been lucky or not, whether any problems will show up later or not, you can consider yourself at least in a lucky position NOW, as you have everything backed up and feel safe enough to make such "experiment" :P  And I guess that if yo go on and install everything, and then some problem explodes, you'll lose more than you can lose now (maybe data, maybe time installing everything again, I mean all the OSs you will have installed and configured by that time).
So, in your place, I'd use gparted to format and re-partition the entire disk so that there are no chances of lost fragments of data nor any corrupted stuff in the disk. I'd make it a brand new disk, and then install every OS in the partition destinated for that purpose.
Hope this sounds at least somewhat suitable/sensible.
Good luck!

---

### Post by User3k on 2010-05-10
> **gadolinio said:**
> Well, I don't know for sure, so I'll just give you my opinion, based on ignorance and prudence.
No matter whether you've been lucky or not, whether any problems will show up later or not, you can consider yourself at least in a lucky position NOW, as you have everything backed up and feel safe enough to make such "experiment" :P  And I guess that if yo go on and install everything, and then some problem explodes, you'll lose more than you can lose now (maybe data, maybe time installing everything again, I mean all the OSs you will have installed and configured by that time).
So, in your place, I'd use gparted to format and re-partition the entire disk so that there are no chances of lost fragments of data nor any corrupted stuff in the disk. I'd make it a brand new disk, and then install every OS in the partition destinated for that purpose.
Hope this sounds at least somewhat suitable/sensible.
Good luck!

The more I think about it, I think you are right. I am just going to redo the whole hard drive now. It is better being safe then sorry. Just because there is no apparent problems right now, doesn't mean that there will not be some issues in the near future.

---

