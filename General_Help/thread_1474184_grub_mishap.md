---
title: "grub mishap"
date: 2010-05-05
forum: General Help
---

### Post by Scott_Starker on 2010-05-05
I'm a little afraid because I don't want to format my hard drive...

I booted up from a CD using ubunto 9.04 live. I installed ubunto on a USB flash drive TWICE. The first time something went wrong but the second time went without a problem. The problem was that ubunto went too slow over the USB port so I installed on VMWare Player under Windows Vista (for those who want to know where I am).

Now the hard part... The first ubunto install on a USB flash drive I had the boot re-director (grub) install on the hard drive and the second installation of grub from the USB flash drive. I can format my USB flash drive but how can I get my hard drive back to the way it as before I had grub installed on it??

Any help would be appreciated.

Scott

---

### Post by Scott_Starker on 2010-05-05
I got it. What pointed me in the right direction was:

 					Originally Posted by **ngcooper23** 					[[IMG]http://c0491962.cdn.cloudfiles.rackspacecloud.com/images/questions/images/buttons/viewpost.gif[/IMG]]("http://www.linuxquestions.org/questions/linux-newbie-8/uninstalling-grub-from-vista-550172/#post3155935") 				
 				[I]Put the Vista Install Disk into the  drive and boot it up, select your language, select repair, select which  partition/instalation to repair, click open Dos (last option on the  list)(2bit - black screen with white text for you newbs), type the  following:

"bootrec.exe /FixMbr"

do not include the quotes!

Hope this helps...

X-Wired Service Inc.
N. Cooper
[EMAIL="xwired.service@gmail.com"]xwired.service@gmail.com[/EMAIL][/I]

---

