---
title: "Problems with VMWare and Ubuntu"
date: 2011-03-18
forum: General Help
---

### Post by iliekpie on 2011-03-18
Hi all,

I installed ubuntu 10.10 64 bit into vmware. The install went fine. I just tried to install the proprietary drivers from nvidia. I tried to follow this: [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

I avoided the section that said that it might mess SOMETHING up with vmware being used.

So i just skipped over that to stopping the gui. So I forgot where I saved the install file so I wanted to go back in and find it. Unfortunately it won't let me start the gui now. I tried the step to start it up from the above link. That gives some long cryptic message about how it failed and that maybe I can try typing something else to start it. i try those commands that it listed and nothing works.



FYI: I know there is way to install from the package manager but I had no clue as to how to get it running as it wasn't working automatically. I've grown used to having to do things myself to get things working in this os....Plus I was successful in doing this in a normal install so I figured it should work this time too.

***TL;DR - How do I get my GUI back when running in VMWare?***

---

### Post by alarme on 2011-03-18
The virtual machine doesn't know your real graphics card, it sees VMWare SVGA II adapter.  Don't try to install the drivers for the physical adapter.

Google for "ubuntu restore generic video driver" to address this.

---

### Post by iliekpie on 2011-03-18
Hmmm, good to know. Thanks.

---

