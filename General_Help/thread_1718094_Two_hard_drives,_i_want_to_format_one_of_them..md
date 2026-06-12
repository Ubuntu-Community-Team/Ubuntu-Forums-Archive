---
title: "Two hard drives, i want to format one of them."
date: 2011-03-30
forum: General Help
---

### Post by Nastybuzz on 2011-03-30
hello!

i am still somewhat of a novice on ubuntu, and computers in general. i have a nice computer i have been dual booting between either ubuntu or win7. i am wanting to remove win7 and install winxp sp3, so i can use media center with my xbox. i preferred that win7 work, but since my copy is not genuine, its authenticity is believed to be the culprit in connection errors with the xbox. i have not been able to find a linux alternative, which i doubt even exists due to the proprietary nature of the xbox.

so, my question is how do i reformat the win7 hard drive? are there issues i need to worry about that may reformat both hard drives on accident? and when the hard drive is formatted, will i be prompted to choose which hard drive to install win xp on? 

i enjoy the linux and ubuntu communities, i know these questions are very researchable, i just wanted to post my questions to see what ideas, recommendations, or general information i might receive. keep up the open source fight, i look forward to hearing from ya'll.

the buzzard

---

### Post by Nastybuzz on 2011-03-30
p.s. the relevancy of postin these win questions on ubuntu forum is because im assuming i will be doing the reformat and winxp installs from ubuntu. is this possible? do i need fdisk? does this work on ubuntu? o dear...

just found my resource   [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)   bummer. i was hoping someone would need to reply...

---

### Post by seawolf167 on 2011-03-30
You can reformat a drive in GParted (System -> Administration -> GParted). However, Windows & Ubuntu will both format the drives during their OS installation so all you have to do is select the correct device/partition for the install.

I'd suggest making backups with [Clonezilla]("http://www.clonezilla.org") if you are worried something may get screwed up. [Here]("https://help.ubuntu.com/community/WindowsDualBoot") is the dual boot guide in case you need it later.

---

