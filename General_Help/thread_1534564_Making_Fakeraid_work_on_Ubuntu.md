---
title: "Making Fakeraid work on Ubuntu"
date: 2010-07-19
forum: General Help
---

### Post by Aceninja on 2010-07-19
Hi Guys,

I have installed Ubuntu 9.10 (64 bit) as a dual-boot setup (along with Win 7) on my desktop. I can't emphasize how much faster Ubuntu loads when compared with Windows. There is only one problem though, I cannot figure out how to use my existing FakeRaid array (two 2TB hdds setup as RAID 1 - mirroring) to work with Ubuntu. I am NOT trying to install Ubuntu onto a raid array (I have Win 7 mounted on a separate boot drive , 4 hdds altogether, two for each OS and two for the RAID array). The raid array works fine in Windows and it's an Intel Raid Controller. How can I do the same for Ubuntu without losing any data? Is this possible? Any help will be truly appreciated.

-Dilip

---

### Post by ronparent on 2010-07-19
There is good news and bad news. The good news is that with 10.04 nautilus will automatically see and make mountable all of your raid drives. The bad news is that you won't be able to use gparted in 10.04 to create or modify any raid partitions. If you are not installing to the raid, you will find 10.04 easy to dual boot to and have full read/write access to all your ntfs partitions.

---

### Post by Aceninja on 2010-07-19
Thanks! That certainly is great news! I am downloading the new version as we speak (64bit desktop). Is there anything that I need to do after installation to setup the Raid or it going to be automatically recognized and set up?

---

### Post by ronparent on 2010-07-20
In my case, and yours should be the same, no special setup was needed. 'Places>Computer' showed all the partitions including raid partitions.

---

