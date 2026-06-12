---
title: "Experience: VMware Workstation 7.1.4 Virtual Mchines on encrypted home folder"
date: 2011-05-02
forum: General Help
---

### Post by fzfq3m on 2011-05-02
HI

I want to share my experience trying to upgrade to Ubuntu Natty 11.04  from ubuntu 10.10... I did a quick search and didn't find anything  similar to what happened to me last weekend so I posted it here

After the upgrade network manager was not working and VMware Workstation  7.1.4 GUI crashed when the GUI tries to show a message. I found that  VMware Workstation doesn't no like the new ubuntu unity and that there  is a workaround for this issue. The workaround worked for me and all  myVMs wre working but I was no happy.

In order to discard upgrade problems I tried to do a fresh install of  Ubuntu Natty 11.04 and for the firts time in my live as ubuntu user I  decided to encrypt my Home folder just to see how it works. The installation process completed without a hitch although quite slow downloading a language pack, but I'm sure that was due to my internet connection being slow at that time.
  
After install I proceeded to update the system and then install VMware Workstation and I wasvery surprised when a virtual machine with Windows 7, that I previously backed up, trew me a BOSD... that VM was working perfectly on ubuntu 10.10 with same workstation version :confused:. I also have a ubuntu server 10.10 vm that worked without problems. 

I used these VMS just for testing so I decided to create fresh copies of  them, just to upgrade to ubuntu server 11.04 and to correct the problem  with my windows 7, but unfortunately all my tries ended with a frozen  installation in the case of Ubuntu or a BOSD in the case of Windows 7 (I  tried Windows Server 2003 also with same result). After spending a day  testing and searching the web for help without luck, I decided that it  was time to give a try to VirtualBox 4.0.6 with Oracle Extension Pack  and I must say that things went much better although Vbox trew me an  error about being unable to access the USB Subsystem... that made me  fall back to Ubuntu 10.10.

Once again I did a fresh install of Ubuntu 10.10 and enable the option  to encrypt my home folder, but after updating (not upgrading) and  installing VMware Workstation I ended in the same spot as with Ubuntu  11.04: No being able to run my backed VM or create a new one, the  symptoms were similar and I was starting to get crazy... I didn't tried  VirtuakBox this time.

I must admit that I gave up and decided to return to Ubuntu 11.04 just  because there was no point (at least to me) to keep version 10.10 if the  problem was not ubuntu version, so I got installed version 11.04 again,  but this time I did not encrypt my home folder because I forgotten to  do it... and guess what? VMware and Virtualbox are working as expected,  well VMware still have troubles with Ubuntu Unity but that is solved  with the workaround.

I'm almost sure this issue is related to my laptop, may be a hard drive  issue (my hard drive is very old and just 5400rpm), so was wondering if  somebody tried to use VMware Workstation or VirtualBox 4.0.6 on Ubuntu  while having an encrypted home folder...

Regards

---

