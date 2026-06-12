---
title: "Ubuntu 9.10 Kernel Panic"
date: 2009-12-20
forum: General Help
---

### Post by arizonagirl11 on 2009-12-20
Hi everyone. I was hoping you could help me. I installed Ubuntu 9.10 a while back, and used it for about a week. But then, I got this message after booting into it...

[       1.7589621] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (8,1)

I am running this on a desktop computer with Windows 7 Preview edition on another boot. Windows 7 was in it first. 

Nothing can be done with the computer when I attempt to boot Ubuntu. Under that message, I get a blinking line, which I guesss is a curser, but, nothing will type. 

Windows is about to runout, and I would rather not buy windows since I do not like Microsoft. However, this message has me really scared about switching to Linux. My Windows OS is working fine. Please tell me

1--how, if possible, can I fix this?
2--How did this happen? The message makes no sense to me.

Thank you in advance for any help you can supply.

Kimmy

---

### Post by simpleAndrew on 2009-12-21
Hi, Kimmy

I'm a newby in Lunux, but i 've found a similar problem at another forum. Try the link below:

[http://www.linuxquestions.org/questions/ubuntu-63/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block81-646063/](http://www.linuxquestions.org/questions/ubuntu-63/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block81-646063/)


Hope it helps

---

### Post by spacewaster on 2009-12-22
I get the same error, using Ubuntu installed via Wubi on a borrowed Laptop (Acer Extenza 5630Z), worked like a charm for a week.

But this morning I got the Kernel Panic on start, after a regular shutdown last night (no errors reported).

---

### Post by lukejv on 2009-12-22
I'm having the same problem. I have 9.10 installed This only happens when i load 2.6.31-16-generic and 2.6.31-16-generic(recovery mode) I do not understand the problem nor do i understand how to fix it.

---

### Post by recmajkemi on 2009-12-29
Same thing happened to me after 3 days of use, nor even -14 generic worked.  Did anyone install ATI catalyst center? (just wild guess)

---

### Post by AsianSpanker on 2009-12-30
Is anyone reading these issues? 
We have all repeatedly asked for help.
Same issue. We downloaded the updates. turned on our computers
the next morning and got kernel panic. 
Is there on computer person that can stop from going off into nerd
heaven and explain the steps. I have seen newbees ask repeatedly for more detailed explainations, only to receive another ration of steps that are much beyond someone who doesn't do computers for a living.
There is an ancient African word that means humanity to others.

---

### Post by fanndian on 2009-12-31
> **recmajkemi said:**
> Same thing happened to me after 3 days of use, nor even -14 generic worked.  Did anyone install ATI catalyst center? (just wild guess)

yes, I have the same problem, just after I tried several ways to install the driver and ccc for my ati video card. I guess the unstable situation is caused by that. But now it still happens, though I have deleted them.

---

### Post by Rickylike on 2009-12-31
I encountered this issue 2 days ago, I can't recover the ubuntu. I captured 2 pictures that showed this problem.
 
Is anyone can solve this issue? Thanks in advance!

---

### Post by Rickylike on 2010-01-02
There is a patch/workarounds for this issue, pls refer to this link: [[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169?comments=all]](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169?comments=all]).
 pls see the layer 210 response for the details!

---

### Post by ph0neman on 2010-01-13
This is issue is turning people off in BUNCHES.  Totally unacceptable and pretty unreal the team ISNT FIXING it.

---

### Post by deathseek on 2010-01-13
ive encounter that thing to after i installed kde i was running on 2.3.31.17
after the update it just froze i guess we have the same problem :(

---

### Post by deathseek on 2010-01-14
im having the same problem, tried reading all te links i found posted still i have no idea what im reading.. im a newbie with this..

---

### Post by john newbuntu on 2010-01-14
What is the exact message that you are getting?  Are you able to boot from an older kernel?
If not, can you boot to a grub prompt (by hitting the Esc key when Grub loads).  Then  basically follow step 15 from this document by drs305:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
and try booting from the grub2 prompt.

---

