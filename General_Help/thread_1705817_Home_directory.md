---
title: "Home directory"
date: 2011-03-12
forum: General Help
---

### Post by Diametric on 2011-03-12
Hello All,

I've attempted to search the forums for a guide on how to place your home directory on a separate partition as I recall reading that this was advantageous for upgrade purposes.  I haven't found anything concise, and was hoping someone could point me in the right direction..maybe a link to post or wiki where this is explained?

I'm currently running 9.10 and have just purchased a new 500GB SATA drive.  My goal, if I understand this correctly, will be to split my home directory into its own partition, upgrade to the latest release and from that point on I can upgrade as I see fit, without loosing what I've save in the existing home directory.

Many thanks,
-Dylan

PS: If I manage to pull this off, the apps I install to bash, like lame, would those be kept under this setup?

---

### Post by Krytarik on 2011-03-13
Generally follow this guide, it seems to be ok, especially because you do all operations from a LiveCD, whereas the other guide below moves your home directory while you are in a running GUI session, depending on those files:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

But you may choose ext4 as filesystem instead, mount the home partition by its UUID and copy the files with the command in this guide:
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Good luck and don't be afraid, it's really not that complicated!
But definitely keep the renamed old home directory until everythings works!

PS: Regarding your PS, everything located in your home directory is kept after upgrade/fresh install. Btw., generally you can *upgrade* without moving the home directory to an external partition, it would be kept also.

---

### Post by Diametric on 2011-03-13
Awesome.  Thank you for your thorough reply.  Yeah, I can't image it's THAT complicated...I've just not done it before and want to make sure I pull it off correctly as I understand it can affect future upgrades.

Thanks again...much appreciated.

---

