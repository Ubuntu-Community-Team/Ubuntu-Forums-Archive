---
title: "best way to reinstall ubuntu?"
date: 2010-12-25
forum: General Help
---

### Post by princeofnam on 2010-12-25
I've been having trouble loading Ubuntu and have been considering upgrading from 10.01 to 10.10 anyway.  I currently have ubuntu installed on a 10 GB partition of my HD with /home/ installed on the rest.  How can I reinstall ubuntu without losing what I have on /home/?

Moreover, is Ubuntu 11.04 an easy install? I'd like to begin using it but if there are still a sizable amount of bugs I might have to forget doing so.

---

### Post by fisch246 on 2010-12-25
I would suggest getting a live CD from Ubuntu.com it should teach you how to do this in the download section. Anyway, once you have booted from the live CD, you can mount that partition that Ubuntu exists in. Now connect and mount an external hard drive, flash drive, or any other external or internal storage medium. Then just drag and drop. once you feel safe that everything is over. Just restart the computer, and install ubuntu and tell it to write over the partition. However you will probably need to do this using custom options. So before you install i suggest checking how much memory you have, and making a swap space that's double that size. Then make a "/" which basically means you'll install everything. However if you don't want this to happen again you can create a partition from "/home". If you want this in detail i can post a link to a forum thread. Any other questions feel free to ask :) i have done this several times before, so i should be able to answer any questions.

---

### Post by nm_geo on 2010-12-25
Moreover, is Ubuntu 11.04 an easy install? I'd like to begin using it  but if there are still a sizable amount of bugs I might have to forget  doing so.

I would not recommend Natty 11.04 at this time it is just at alpha 1 stage and very buggy unless you are into testing.  Lucid 10.04 LTS is very stable compared to Natty.

---

### Post by fisch246 on 2010-12-25
yea thanks geo, i forgot about that part.

to add to what he said, 10.10 is also good, but 10.04 is LTS (Long Term Support). To be honest there isn't much difference between 10.04 and 10.10, but if you wish to stay up to date, i don't see why not.

---

### Post by DeMus on 2010-12-25
Why newbies always want to have the latest version of the OS? Choose a stable version, like 10.04, and stick with it until you know what you are doing. Learn Ubuntu. Read about Ubuntu and Linux so you know how it works. Then you can start to experiment.
When you start now you will be spending all of your time here on the forum asking questions, stating this doesn't work, that doesn't work. Well it works, you simply don't know how to make it work.
Linux is totally different from Windows and you need to spend time learning it. If you don't do that, it will always be a mystery for you, ending in a complaint: Ubuntu is useless. Which it most certainly is not.
So before you do anything, read about Linux, about Ubuntu, read how to install it, how to make programs install and work. There is so much info on the internet.
Success and enjoy it.

---

### Post by HermanAB on 2010-12-25
Howdy,

If /home is a separate partition, then you can re-install - without formatting /home - any time you want and your data will be preserved.

If you don't have a separate /home partition, backup your data and make one when you re-install.

---

### Post by fisch246 on 2010-12-25
ah yes... DeMus makes a point... if you're a newbie then yea just stick with 10.04 and wait until 12.04 the next LTS... but if you have experience or like playing around with Ubuntu, and love screwing around with all the new stuff, then yea get 10.10 and 11.04 when it comes out :)

you can get plenty of support from the community so staying up to date is always ok. just look at my profile, i never get a chance to post for help or post answers, cause the community has already taken care of it. what i suggest is just getting 10.04, and getting virtual box to test out 10.10... if you like it, get it... hope we've all helped you out :)

---

### Post by princeofnam on 2010-12-25
Thanks.  Maybe I'll just try to recover my current version of 10.04.  I have the following problem.

Whenever I try to boot to Ubuntu I get a blinking cursor.  GRUB loads perfectly fine thoug.   I posted about this on a previous thread but no one responded.

>  My friend gave me a spare 80 GB HD that i recently installed.  When I  booted up the computer it booted to Windows XP (i assume from the new  HD).  the 80 GB is installed in sata port 0, ubuntu in sata port 1, and  my windows 7 installed on sata port 3.  the boot order was the new 80 gb  drive, ubuntu, and then windows 7.  I thought if i switched the boot  order in bios GRUB2 would load but it didn't.  i decided to then unplug  the 80gb and GRUB2 loaded but now ubuntu just loads to a blinking  cursor.  This blinking cursor error happened before when i installed a  new mobo and processor but it somehow resolved itself.   and

Ever since replacing my mobo,  processor  and RAM with a core2duo and 2 GB of ddr2 ram   noticed through conky that I no longer have SWAP memory.  Is that normal? I could never find out how to fix that

---

### Post by princeofnam on 2010-12-25
if i end up not being able to fix my current version of ubuntu can someone clarify the following advice

> Now connect and mount an external hard drive, flash drive, or any other  external or internal storage medium. Then just drag and drop. once you  feel safe that everything is over. Just restart the computer, and  install ubuntu and tell it to write over the partition.

what would I be dragging and dropping and why? 

>  hen make a "/" which basically means you'll install everything. However  if you don't want this to happen again you can create a partition from  "/home".

wouldn't making a "/" wipe out my entire harddrive?  and what wouldn't have to happen again if i  created a partition from "/home"

---

### Post by dino99 on 2010-12-25
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by princeofnam on 2010-12-25
furthermore I have a 64 bit processor I believe.  

e4500 core 2 duo         
[http://ark.intel.com/Product.aspx?id=30781](http://ark.intel.com/Product.aspx?id=30781)

Should I install the 64 bit version of Ubuntu or will that make matters more complicated in my life?

---

### Post by dcstar on 2010-12-27
> **princeofnam said:**
> furthermore I have a 64 bit processor I believe.  

e4500 core 2 duo         
[http://ark.intel.com/Product.aspx?id=30781](http://ark.intel.com/Product.aspx?id=30781)

Should I install the 64 bit version of Ubuntu or will that make matters more complicated in my life?

The only "complication" with 64-bit is manually installing the pre-release 64-bit Flash from the Adobe site.

I have been using 64-bit Ubuntu for years now (like hundreds of thousands - millions? - of others).

---

### Post by princeofnam on 2010-12-27
Ubuntu won't have done this by default?  Are there instructions for installing that pre-release 64 bit flash from Adobe?

---

### Post by andymorton on 2010-12-27
> **princeofnam said:**
> I've been having trouble loading Ubuntu and have been considering upgrading from 10.01 to 10.10 anyway.  I currently have ubuntu installed on a 10 GB partition of my HD with /home/ installed on the rest.  How can I reinstall ubuntu without losing what I have on /home/?

Moreover, is Ubuntu 11.04 an easy install? I'd like to begin using it but if there are still a sizable amount of bugs I might have to forget doing so.

There will be lots of bugs since it's only at the Alpha 1 stage. You can specify which partition to use during the install process.

---

