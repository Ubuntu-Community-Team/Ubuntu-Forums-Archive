---
title: "/home in its own directory in 9.10 - grub2"
date: 2009-11-15
forum: General Help
---

### Post by aspergerian on 2009-11-15
My Acer Aspire 1410 solo core finally has the partitions I want, with 9.10 first on the HD, Vista later. Since grub has been replaced by grub2, some of the online descriptions for how to move /home into its own partition seem perhaps not quite accurate. 

I'd rather hassle through learning a sequence of maneuvers so as to move /home into its own partition. Suggestions would be appreciated. It's interesting that as Ubuntu progress to 9.10, numerous google-findable help pages retain relevance for pre-9.10 versions.

---

### Post by oldos2er on 2009-11-15
[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

---

### Post by dcstar on 2009-11-15
> **oldos2er said:**
> [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

Exactly, I cannot fathom how Grub is relevant in making a separate /home partition.

The only configuration file that needs to be manually edited - and even that is not necessary if people use the pysdm package - is /etc/fstab.

---

### Post by aspergerian on 2009-11-15
> **oldos2er said:**
> [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

Ann, 

Thnx for the suggestion. I've been trying two sets of instructions (one at a time):

[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)
[http://www.ubuntu4life.com/node/30](http://www.ubuntu4life.com/node/30)

Each baffles me. 

The first one has me "sudo mkdir /old", several more steps, then "cd /old/home" -- which has me wondering how home came to be within old. Then the instruction "find . -depth -print0 | cpio --null --sparse -pvd /new/" generates error text. 

The second url above baffles me similarly. My hd has a "43 GB Filesystem" partition.  I don't understand $mkdir /mnt/newhome on the instruction url, even if I try $mkdir /mnt/43 GB Filesystem".  I tried renaming that partition but may have to re-use Gparted in order to do that. 

Not getting far today...

---

### Post by aspergerian on 2009-11-15
> **aspergerian said:**
> 

[http://www.ubuntu4life.com/node/30](http://www.ubuntu4life.com/node/30)

The... url above baffles me similarly.

I used gparted to label the intended new /home directory's partition as MyHome. That worked in above url's instructions, with one alteration. Another set of instructions clarified/corrected a copy-this line in above url. 

[https://answers.launchpad.net/ubuntu/+question/21663](https://answers.launchpad.net/ubuntu/+question/21663)

"I'm afraid I don't know how the cpio stuff works. However, the "null" and "sparse" commands should have two dashes in front. That may be the problem. So the line should look like this..."

find . -depth -print0 | cpio --null --sparse -pvd /mnt/newhome/

That line, when used in place of similar line at first url seems to have worked. My new /home seems to be in its own partition. 

Thnx to the several who resonded. My mentioning grub may have come from reading too many ubuntu-related pages today.

---

