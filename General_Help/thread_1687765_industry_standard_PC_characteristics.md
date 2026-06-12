---
title: "industry standard PC characteristics"
date: 2011-02-14
forum: General Help
---

### Post by hill0093 on 2011-02-14
I have in past years installed ubuntu linux by installing windows and ubuntu separately each on its own separate hard drive while the other drive was not connected up. Then when I connected both at the same time, the BIOS recognized each and placed it on the boot menu. I have recently bought a Hewlet Packard ENVY-17 PC and when I do the same procedure, the  Linux does not show up on the boot menu. My experience with three PCs in the past few years lead me to expect that it is industry standard for motherboard and their BIOS to work that way. I consulted with HP on their chat. The various persons give different opinions, but the last one I chatted with said that I cannot put windows and Linux on the ENVY-17. I told him that was absurd, that I want my money back, And that the reason I bouht the ENVY-17 was that it had two disks, the one being empty. So now I am looking for a laptop that has two hard drives; I don't want to partition a drive. Does any one have any information about anything I have said in this post.

---

### Post by An Sanct on 2011-02-14
According to my web search the Envy17 has a 500GB internal drive, I am confused tho, why you would not want to partition such a drive? 

Searching the forum for dual booting will get you a ton of results and already answered questions. IMHO In short: it is better to install windows and then Linux, so GRUB takes over and reports both OSes at boot time.

The industry standard is as follows (I will skip EFI here):
BIOS takes a look at the first selected boot drive and if it finds a boot sector, continues to execute code in the boot sector and then gives full control over the computer to that code ([see bios wiki]("http://en.wikipedia.org/wiki/BIOS"))

And you can multi boot to nearly as many different OSes as you like (according to the restrictions of the OSes)

---

