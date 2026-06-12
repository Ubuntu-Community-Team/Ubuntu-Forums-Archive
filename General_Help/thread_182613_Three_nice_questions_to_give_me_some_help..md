---
title: "Three nice questions to give me some help."
date: 2006-05-26
forum: General Help
---

### Post by turbojugend_gr on 2006-05-26
Hi everyone, I hope to get some extra help on this. I helped one or two of you maybe, and since now never needed something that wasn't written on another thread! Well there's a good start for everything in life... lol!

Issue 1: I am planning on a new 32bit install since i 've seen no good reason for me staying at 64bits. I wonder if i keep my Home partition as it is, what should i still have to deal with after the 32bit install. Please only response to this one if you are sure, as I have some important data in this partition. note that I use various apps from desklets and rythmbox to Anjuta IDE and so on.

Issue 2: Is there a SAFE and not extra-complicated way to enlarge my Home Partition??It is about 5 gigs and would like to at least double it...

Issue 3 : Should I go to Dapper or should I wait for the "Official Release". Note here I am aware I can upgrade through apt-get (at least), but all you Flight Testers give me a hint here should I try it now or in 5 days will it be actually released??

ATTENTION: I own an AMD 4400 Dual Core Proccessor and I am currently using a k8 SMP kernel. I thing i can use the i386 SMP kernel (k7 SMP?), if I am wrong PLEASE say so. Lol I tricked you with an extra Question...

Thanks in Advance all you wonderfull people....

PS: In case it gives you any hint on what I might be familiar with I use ubuntu Breezy 64bit for about 2 months now and before that I used SuSE 9.3 and OSS 10 for about a year (loved the 32bits apps working great on 64bits there).

PS 2: My machine specs just in case: amd 64 X2 4400, nVidia 7800GTX, Asus A8n-sli, 2 dimms 1gb each on dual channel, and two disks, one of which is a pain in the ***, FAT32 issues, I will try a new one before bothering you with this though.

---

### Post by turbojugend_gr on 2006-05-26
What's up??? 
39 views and counting and no post yet ????
What if I promise some nude photos... will this help.LOL!

Seriously now please aid to this one!

---

### Post by tkjacobsen on 2006-05-26
i can't answer your questions. But i know that dapper 64 is much better than breezy 64. My roommate uses it!! Maybe you should give it a try.

I'll forward this thread to him.

i think the k7 kernel will work flawlessly, since amd 64 processors are 32-bit compatible.

Go for dapper now.. apt-get will update the rest for you. no problemo.

---

### Post by dlai on 2006-05-26
So I am tkjacobsen's roommate and, i have had no problems with the k7-kernel do not have any dual core though. I agree on your choice to switch to 32 bit.
ISSUE 1. I would recommend you keeping that partition, and not mounting it as /home... but something else, and thereafter try and copy the different things over into your new directory... I actually just changed from 64 bit dapper to 32 bit dapper, and there were no compatibility issues in the home folder config-files. The only thing that did not work was my evolution-config. I just copied from one home folder to the other. But anyway everything in the home folder is just databases or config-files. I know it is much work but if you are unsure you can config everything again. But I have heard that it is a bad idea to mount it as /home from the installation... At least it did some weird things when i did it in kubuntu.

ISSUE 2: I have no idea.. but if you want to ensure your data, move it to another partition/harddrive/dvd/something and do your messing around

ISSUE 3:As I see it dapper is safe to install... but if you really want to be sure.... WAIT!

---

### Post by turbojugend_gr on 2006-05-26
Thank you for your first replies.

My first question: Oh you Famous Roomate...(lol) did your evolution config worked after the copy??? I can't get that one clear, anyway.

As for the /home partition I will just burn it on a DVD and then copy the .config folders of those apps that is absolutely needed... that' will do the trick. So the last 2 issues are solved (along with the enlargement) though for trivial purposes I would like to know If I am able to do that.

Since now I would like some help on the LINUX K7 SMP Kernel (that should be the dual core 32bit kernel) ISSUE 1.

Thanks again both you room8s, and also any future help...

---

### Post by blackjack6.21.91 on 2006-05-26
as far as the dapper thing goes, the release candidate already exists, so if you upgrade now you'll pretty much be getting what you will if you wait.  also, it's really super-awesome (trust me), so it's definitely worth getting.

---

### Post by turbojugend_gr on 2006-05-27
Thank you for your info regarding the Dapper issue.

I would like some help here, is there a k7 SMP (a 32bit kernel for Dual Core CPUs?). Is it stable and trustworthy?

---

### Post by dlai on 2006-05-27
...did your evolution config worked after the copy??? I can't get that one clear, anyway. --- Well if you mean as in my mailboxes calendars and all just opened again when I started evolution, then no, I just can't figure out where the config files are, but actually i think my roommate found out sometime, I will rererepost him this link, and maybe you will hear from him, anyway he is trying to get more beans than me so I think he will:D 
About the resize, again I have no idea, never done it.
And by the way dapper i soooo good!!

---

### Post by skippy81 on 2006-05-27
[QUOTE=turbojugend_gr]Issue 1: I am planning on a new 32bit install since i 've seen no good reason for me staying at 64bits. I wonder if i keep my Home partition as it is, what should i still have to deal with after the 32bit install. Please only response to this one if you are sure, as I have some important data in this partition. note that I use various apps from desklets and rythmbox to Anjuta IDE and so on.[/QUOTE]

The contents of your home directory are best left alone.  I would recursively copy the entire home directory structure onto a CD or memory stick.  If this isn't an option because of the size of your home partition then make a new home partion (during dapper CD install) and leave your old home unmounted and unpartitioned.  Copy across all your multimedia files and documents, and then copy across settings bit by bit until you have restored your system to how you want it.  

The only problem with this approach is that it will leave you with a 5gb partition that is not really being used (after you have copied everything across from you old home) No problem!!! Just mount the old Home partition inside your new one :)   Use it as a handy place to keep your multimedia and important files - in fact since it is on a seperate partition you could mount the whole thing as read only and have it as an extra safe place to store your precious stuff.

By the way, dont take this to mean that linux is a pain to upgrade.  I would personally just do an install and mount my old home directory without formatting it.  However you want to play it safe, so the way listed above is best for you.  I suggest that when you use the install program you spend at least 20 minutes doing the partitioning.  Make sure you understand what all the flags and stuff do - remember, you DO NOT want to either format or mount your existing home partition. 

[QUOTE=turbojugend_gr]Issue 2: Is there a SAFE and not extra-complicated way to enlarge my Home Partition??It is about 5 gigs and would like to at least double it...[/QUOTE]  

There is no safe way of resizing paritions.   I remember my days on windows using Partion Tragic *cough Magic and things can always go wrong.  

[QUOTE=turbojugend_gr]Issue 3 : Should I go to Dapper or should I wait for the "Official Release". Note here I am aware I can upgrade through apt-get (at least), but all you Flight Testers give me a hint here should I try it now or in 5 days will it be actually released??[/QUOTE]  

Go for Dapper.  I have been running it for a few weeks now, not a single crash.  I have found it to be more stable and faster running than breezy.  Dapper is in my opinion a polished and excellent product.  The majority of the complaints about it at the moment regard the artwork, which IMO is a good indicator that the OS itself is perfect :)  Once you expierience the ducks vibrant plumage you will never go back :cool:  

Don't use apt get.  Just download the i386 iso of dapper RC1 and install from that.  The reason I suggest this is that it is actually quicker.  Doing a dist-upgrade from breezy can go wrong, and takes an incredibly long time to download and then install everything.  Also having a physical disk with which to install from is really handy.

---

### Post by skippy81 on 2006-05-27
As for you evolution settings, I can assure you that if you backup or leave your current home partition intact you WILL be able to get you evolution mail and contacts back.  The best way of doing it is to simply set up the program as if you are a new user, and then use the built in import function.

---

### Post by turbojugend_gr on 2006-05-28
First of all I would really like to thank you for your time, but I made my mind on all of this stuff. Don't get me wrong but I don't like stealing your time for nothing.

As I said above please give me some feedback on the *****kernel  K7 SMP (Multicore Proccesors)******.Is someone having any problems with it? I use the K8 SMP kernel (for 64bit Dual Cores) for quite a long with no issue but I was wondering what about the 32bit brother? IS IT SOLID??? Plz if anyone post some feedback.

Again I don't mean to offend you but I solved the other issues gracefully, so I asked a while ago for the K7 SMP kernel and still I seem to steal your energy on topics that have now gone trivial... :-)

---

### Post by tkjacobsen on 2006-05-29
I have a cron-job rsync-ing my evolution mails and contacts every hour (along with some other stuff).

All evolution stuff is in:
~/.gconf/apps/evolution
~/.evolution

though it will not remember your accounts.. Havent figured that out yet.. But all your mails and contacts should be safe.

---

### Post by turbojugend_gr on 2006-06-02
Thread Closed

---

