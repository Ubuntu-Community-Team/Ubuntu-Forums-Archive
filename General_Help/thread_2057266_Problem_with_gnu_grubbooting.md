---
title: "Problem with gnu grub/booting"
date: 2012-09-13
forum: General Help
---

### Post by Charobnjak on 2012-09-13
Hi,

I have a problem with booting up ubuntu, there's a cursor blinking on a black background right before gnu grub should come up but it never does, it just stays that way . It is installed along with Windows 7 which was already installed  before. At the time it was version 10.10 and haven't used it in a while so recently I decided to update it and it upgraded fine to 11.04 (or 11.10, can't really remember the version number) even though there was a warning about boot error but it was fine after it finished. But then I upgraded it to 12.04 the same warning poped up but after that I couldn't start it up again. Since I had some problems with gnu grub before I already have installed some dual boot software( can't remember which but it let's me choose with partition to boot from before booting) so I can still access my windows. Is there any was that I could fix ubuntu through windows to make it able to start up again?

I am not an advanced ubuntu user so please keep things simple.

Thanks,
Charobnjak

---

### Post by sid0972 on 2012-09-13
use boot repair
first, boot from the live cd, then select try ubuntu
upon arriving at desktop, open firefox and enter the following commands

> sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update

and then 

> sudo apt-get install -y boot-repair && boot-repair

then either select recommended repair, or you can select advanced if you want the OS and time for GRUB menu to change

everything's given at this link [here]("https://help.ubuntu.com/community/Boot-Repair")

---

