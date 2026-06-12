---
title: "what to do if ubuntu doesn't start"
date: 2011-07-27
forum: General Help
---

### Post by pain.reign on 2011-07-27
I need to know how to repair ubuntu. I don't want to reinstall it. I want current version keep working. Is it possible? 

I know that i need to remove recently installed program but how can i do that if ubuntu doesn't start. Even in recovery mode.

---

### Post by linuxuser12345 on 2011-07-27
Have you tried logging in as a Ubuntu Classic mode user? That usually solves any problems with me when it comes to login issues

---

### Post by dim_hyder on 2011-07-27
What error message is displayed when ubuntu does not start?

---

### Post by pain.reign on 2011-07-27
Does it matter what it says? I need general method to reinstall broken software.

But if u feel easier if i  tell what it says here it goes:

1. In normal mode it says nothing just hangs on in ubuntu purple screen.
2. In recovery mode it tries to load but also cannot get anywere and it says that intel graphic card faild. I have optimus. And intel card fails. I don't get anywhere.

About try in classic mode its nice. But do u understand what means cannot load? It doesn't boot anything even recovery mode. It hangs on first step.

---

### Post by dim_hyder on 2011-07-27
Firstly ppl in this forum are just trying to help, please show a little respect.

If recovery mode fails I think you are looking at a reinstall. On the allocate drive space screen during the setup select upgrade ubuntu 11.04 to 11.04 (assuming you are running 11.04), this should keep all music and user created files and also keep installed software where possible.

Cheers,

Pete

---

### Post by pain.reign on 2011-07-27
I understand thank u all very much. 

When i reinstall ubuntu. thereis no option upgrade there is options:
1. Erase ubuntu and reinstall - all files deleted
2. Erase everything and install - windows 7 and ubuntu files deleted.  

how to get to upgrade option? I have ubuntu desktop 64. 11.04 version.

So how to fix my system if its broken?

---

### Post by Mark Phelps on 2011-07-27
I understand your frustration -- really.  Can't count how many times I've had to repair one thing or another.

But YOU need to understand something -- there is NO "general fix" for anything.  Period.  Every problem requires its own specific solutions -- which is why folks are patiently asking you for more information.

So, stop demanding miracle cures, and work with those offering you help.

---

### Post by pain.reign on 2011-07-27
but there should be something to do if system doesn't boot? login in terminal or something. because now i cannot repair it at all now i don't have anything important there so i can easily reinstall but what if there is important information reinstalling every time doesn't help

---

### Post by varunendra on 2011-07-27
While I'm not familiar with **chroot** myself, I've heard a lot about using it to repair a broken installation of linux (even ub-bootable one). In your particular case, it'll involve booting into Live CD environment of the same version that is installed, then chrooting into your installed version, then proceed with dpkg or whatever required to fix broken packages.

Since I haven't used it myself, I can't suggest anything beyond this at the moment. But I'd definitely try to help (including requesting others who know-how) if you wish to go this way. Some suggested links as a starting point:
[http://www.linuxquestions.org/questions/linux-newbie-8/howto-use-chroot-431293/](http://www.linuxquestions.org/questions/linux-newbie-8/howto-use-chroot-431293/)
[http://answers.yahoo.com/question/index?qid=1005122600994](http://answers.yahoo.com/question/index?qid=1005122600994)
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

---

### Post by crmullin on 2011-07-27
Okay, so please tell us what your goal is.  Do you simply want to keep all of your files and work from the previous installation?

It looks like either you'll have to
1) do a clean install or upgrade (which in many cases won't wipe out all your files, but you should back up just in case) or,
2)  you can boot with a LiveCD and repair all your packages manually.  

Option (1) is relatively easy, and option (2) can be anywhere from mildly complex to impossible depending on what the problem is.  

Everyone on here has been faced with this situation at least once in some form, so it's not a huge deal.  This is just a part of working with Linux.  :D  Give us a little more information and hopefully we'll be able to help!

---

### Post by bodhi.zazen on 2011-07-27
> **dim_hyder said:**
> What error message is displayed when ubuntu does not start?


> **pain.reign said:**
> Does it matter what it says? I need general method to reinstall broken software.

It is critical if you want assistance. You may not understand the error message , but we will.

See: [http://www.chiark.greenend.org.uk/~sgtatham/bugs.html](http://www.chiark.greenend.org.uk/~sgtatham/bugs.html)

---

### Post by pain.reign on 2011-07-27
well its not bug just i have optimus and it is not yet supported in good way by linux so i already reinstalled my ubuntu about 15 times. now i decided to find another way to repair except reinstalling.

chrooting I like this method i definately will try to find more about it.

but about uprgading i cannot find this option. 

Can anyone tell me exactly how to get to upgrading option that doesn't erase previously installed linux?

I have this installer cd:

ubuntu-11.04-desktop-amd64

---

### Post by holycow131415 on 2011-07-27
You need the 11.10 64 bit CD.

Its in alpha though, so im not sure if you want to use this on a production machine.


[http://cdimage.ubuntu.com/releases/oneiric/alpha-2/](http://cdimage.ubuntu.com/releases/oneiric/alpha-2/)

---

