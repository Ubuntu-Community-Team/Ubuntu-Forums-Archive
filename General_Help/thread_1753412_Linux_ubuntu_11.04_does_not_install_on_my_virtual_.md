---
title: "Linux ubuntu 11.04 does not install on my virtual machine?"
date: 2011-05-08
forum: General Help
---

### Post by chanderkant on 2011-05-08
[»]("http://answers.yahoo.com/question/nextQuestion;_ylt=AjDwTvnZyfzQLMdv2JXpsHhz7hR.;_ylv=3?qid=20110508085441AAGpfJn&cid=396545664&state=open")                                              **Linux ubuntu 11.04 does not install on my virtual machine?**


Hello guys I have a problem installing ubuntu on my virtual machine.  recently I downloaded ubuntu and burned it to a cd and a dvd. but now I  have a problem, when after the setup is nearly 80% percent complete. the  installation stops and says that cd or dvd has a problem. but I have  tested the cd and dvd and even the dvd drive, also the .Iso file using  7zip and cd checker. I allocated 304 mb of ram out of 896 mb. would  anyone knows that it should be the problem. I am using oracle vbox 4.0.6  and win xp as host. :confused:

---

### Post by lmarmisa on 2011-05-08
If you are using VirtualBox, you do not need to burn a cd. Try to attach the Ubuntu iso file to the virtual CD driver.

If you wish to check the consistency of your iso file, you can see here the md5sums of the different iso files of Ubuntu 11.04:

```

8468300a61ea1e3b7607f46f7643b57a *ubuntu-11.04-alternate-amd64.iso
e6a29ce3dccb0ab12332036dcff7d9e4 *ubuntu-11.04-alternate-i386.iso
7de611b50c283c1755b4007a4feb0379 *ubuntu-11.04-desktop-amd64.iso
8b1085bed498b82ef1485ef19074c281 *ubuntu-11.04-desktop-i386.iso
355ca2417522cb4a77e0295bf45c5cd5 *ubuntu-11.04-server-amd64.iso
b1a479c6593a90029414d201cb83a9cc *ubuntu-11.04-server-i386.iso

```

---

### Post by chanderkant on 2011-05-09
e45a962e12c93bddcad5f26aff865e81, yeah it is the checksum of my ubuntu 11.04 .ISO desktop file, I downloaded it from ubuntu site using Internet download manager.
do you think I have to redownload it.
also the ubuntu demo runs on my virtual machine but it does not install. I tried ubuntu .ISO install as you aforesaid. but I still get the SAME PROBLEM. 
is it the problem with the checksums not matching.

---

### Post by lmarmisa on 2011-05-09
> **chanderkant said:**
> e45a962e12c93bddcad5f26aff865e81, yeah it is the checksum of my ubuntu 11.04 .ISO desktop file, I downloaded it from ubuntu site using Internet download manager.
do you think I have to redownload it.
also the ubuntu demo runs on my virtual machine but it does not install. I tried ubuntu .ISO install as you aforesaid. but I still get the SAME PROBLEM. 
is it the problem with the checksums not matching.

No doubt. If the md5sum of your ISO file is wrong, you should download it again.

---

