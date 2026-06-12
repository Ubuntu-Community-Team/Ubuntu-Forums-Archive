---
title: "How to dual boot Ubuntu &amp; Windows 7 (ubuntu already installed)"
date: 2010-04-16
forum: General Help
---

### Post by chris.jericho on 2010-04-16
Hey there, I have been using Ubuntu for quite a while and i am very happy with it since it serves my purpose.

But recently I got the need of Windows, since there is a software that I have to use that is compatible only with Windows, for my new job. 
That is why I purchased Windows 7 and now... can please someone help me on how can I create a new partition on my hard drive and install Windows 7 in that.

My computer is already installed with Ubuntu 10.04 beta 2 (updated yesterday from beta 1). 

Please someone provide me instruction to do so........   since I ain't a big computer savvy... :)

Thanks in advance...... really appreciate your help :)

- Chris

---

### Post by issamneo on 2010-04-16
Hi chris, as i know you have to install windows then install ubuntu coz if you install ubuntu first windows will erase the mbr and you will have only windows.
in your case (ubuntu is yet installed) i think you can install windows but in this case you have to do some commands to correct the mbr (such as check mbr,...).

the best way is to install windows then install ubuntu like that you're Ok and you have no thing to do.

---

### Post by chris.jericho on 2010-04-16
thanks for the reply bro........

I can backup my computer and then install Windows........ but to install I just put in the normal windows 7 CD and then just do a clean installation right???

sorry i am asking many stupid question...... i am a legal guy and not much into computers......

anyways..... once I am done..... with installing windows then how do I dual boot..... Ubuntu/........ i had tried it once and got confused....... cause it was asking some root think and something.........

and what is this swap space..??   

really appreciated :)

---

### Post by frantid on 2010-04-16
this is what you are looking for:

[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

---

### Post by chris.jericho on 2010-04-16
THANKS FOR THE HELP MATE.,........ :) I WILL GO THROUGH THAT.... :d

---

### Post by chris.jericho on 2010-04-16
Oh.... mate.... thats tutorial says that 

"
##This guide does not work for Karamic or future releases, For that see  page 14 and follow the link provided by presence1960 for how to dual  boot with Grub2 (requires some reading) I will update this guide for  grub2 when I have more time## 
"

I am currently using the 10.04 version.... :( 
This wont work for me....... He has given something saying Grub2 but can't understand anything there.......  please can someone help me with this.... 

I am getting a little confused on this one.... since his tutorial will only work.... with Ubuntus earlier than 9.10........... 

Please help me

---

### Post by chris.jericho on 2010-04-16
Somebody please help me on this one!!!

---

### Post by issamneo on 2010-04-16
after installing windows, create an empty partition.
then boot on  the ubuntu CD, it will ask you, you want to install on which partition: choose the empty partition. Ubuntu will create the dooble boot for you, you have nothing to do
hope i was clear

---

### Post by chris.jericho on 2010-04-16
okay.. alright... thanks mate,...... if thats the only option then I will do that..

---

### Post by issamneo on 2010-04-16
no it's not the only option you can follow  the tutorial that frantid send to install windows without removing the ubuntu.
a+

---

### Post by oldfred on 2010-04-16
Windows needs to be on a primary NTFS partition, so depending on how your paritions are used may make a difference.

Direct link to instructions on reinstalling grub2 (and others).

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

