---
title: "I don't  want Mint anymore."
date: 2009-07-07
forum: General Help
---

### Post by darkknight85 on 2009-07-07
I was playing with Mint 6 and Ubuntu 8.04 I like Ubuntu better. 
Q: How do I remove Mint and resize my Ubuntu to take over that partition?

---

### Post by anystupidname on 2009-07-07
install unetbootin partedmagic
[http://sourceforge.net/projects/lubi/files/PartedMagic%20Partition%20Manager/unetbootin_partitionmanagerrev146_all.deb](http://sourceforge.net/projects/lubi/files/PartedMagic%20Partition%20Manager/unetbootin_partitionmanagerrev146_all.deb)
reboot to it
Delete mint part and resize ubuntu part
Then edit /boot/grub/menu.lst and remove the mint entries

---

### Post by aysiu on 2009-07-07
Just go to System > Administration > Software Sources, uncheck the Mint repositories, go to Synaptic Package Manager and remove MintUpdates, MintMenu, and all that other Mint stuff, and change the theme to Human and add a top panel.

---

### Post by darkknight85 on 2009-07-07
Thanks I will try that...additionally I am using my terminal to add an additional desktop environment and was wondering if you or anyone you talk to on here knows how to save my progress so i can let my laptop rest.... it is starting to get warm....

---

### Post by anystupidname on 2009-07-07
Your followup question isn't clear to me. If you're saying you ran an aptitude/apt-get (from CLI) operation that is taking a while and you want to interrupt it to let the laptop cool down (this shouldn't be necesary normally just FYI) you can CTRL-C and halt the operation and when you unsuspend / unhibernate the laptop and rerun the command it will pick up where it left off. The GUI package managers usually have a cancel button available too. I generally wouldn't recommend canceling either method just because "$#!+ CAN happen" but those are some options for you... If I completely misunderstood your question, please clarify...

---

### Post by c0mput3r_n3rD on 2009-07-07
I can't help you out but I didn't like mint that much either, I thought it was too bland.  
You would think with a name like it would have some flavor...

---

