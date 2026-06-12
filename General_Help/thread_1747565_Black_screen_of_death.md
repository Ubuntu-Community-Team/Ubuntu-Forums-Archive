---
title: "Black screen of death"
date: 2011-05-02
forum: General Help
---

### Post by Nextgeneration on 2011-05-02
My problem, I upgraded from the pakage manager to ubuntu 10.10 and went to bed, woke up and the computer was turn off, I thought ok cool it's finished. I am on my second hard drive running fedora, my ubuntu hard drive boots and then there is a black screen and an underscore just blinks for hours. It looks like terminal but I can't type anything. I can see all the files but I can't get permision to do anything to them.

Any and all help Thanks.

---

### Post by PsYcHoTiC_MaDmAn on 2011-05-02
I had a similar problem (it was either just a black screen and underscore as you mention, or a blank purple screen. and it wouldn't accept passwords so wouldn't do anything)

first off, boot into the recovery console. then use the dpkg option to make sure all has been unpacked and installed properly, then run in low graphics mode and download the restricted drivers.

this got it working properly for me (though in the end I did a clean install, repartitioning the hard drive so there was a separate /home partition to avoid similar issues in the future (much credit to Hedgehog1's various postings)

[edit, just realised your talking 10.10, the above was for 11.04 but should be a similar fix

---

### Post by lakerssuperman on 2011-05-02
I always like watching my updates for this reason, so when something does goes to hell, I at least have some idea as to which road it took there.

Most likely, as the above poster said, it is a case of the installation not completing.

---

### Post by Nextgeneration on 2011-05-03
Ok so I booted to recovery mod and it did nothing just hung there. I couldn't even get to a terminal screen to install anything
sudo apt-get update
I try to run terminal from my fedora system but it says that my username dosn't exist.
I'm going to try to launch terminal in terminal from my ubuntu desktop and see if the permisions work there.

---

