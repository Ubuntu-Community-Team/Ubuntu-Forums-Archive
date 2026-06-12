---
title: "OpenOffice makes system freeze"
date: 2010-03-22
forum: General Help
---

### Post by mje1708 on 2010-03-22
I am running Ubuntu 9.10 and trying to use OpenOffice 3.1. If I run OpenOffice, after 10 minutes or so, the whole computer freezes. Even if I have shut down OpenOffice it still happens. Only answer is to turn computer off and on again.

I read some other people's posts listing the same problem and as a result uninstalled Open Office and then installed it again. I also uninstalled Compiz. Neither of these seem to be the solution. I have just installed Lotus Symphony and there are no problems with freezing and so the issue is definately with OO and Ubuntu.

I then on further advice uninstalled the bundled Ubuntu version of OpenOffice and installed directly from the OpenOffice website. The problem still remains.

Next thing I tried was to uncheck autosave feature. This doesn't help either.

The above problems only happen on my desktop. I also have an ASUS EEE Netbook running Ubuntu 9.10 Netbook remix. This is fine - the problem does not seem to affect the netbook.

Any ideas? I would really like to continue to use OO - I like it a lot. Unfortunately this freezing issue is making it unusable.

Thanks

Mike

---

### Post by 666f6f on 2010-03-22
Why do you think this is an OpenOffice problem (not trying to defend it, I personally don't like it that much)? Does your system freeze only after running OpenOffice? Have you checked /var/log/messages and /var/log/kern.log for anything suspicious?

---

### Post by mje1708 on 2010-03-23
I think it is to do with OpenOffice because it always freezes after 10 minutes or so of opening it. It doesn't do it otherwise.

How do I access the files you mention? What am I looking for on them?

Thanks

---

### Post by konqueror7 on 2010-03-23
try increasing its memory share,,, Open OOo Write, then Tools > Options, then under 'OpenOffice.org', tr increasing the memory allocations...see if that helps...

---

### Post by 666f6f on 2010-03-23
> **mje1708 said:**
> I think it is to do with OpenOffice because it always freezes after 10 minutes or so of opening it. It doesn't do it otherwise.

How do I access the files you mention? What am I looking for on them?

Thanks

The files I mentioned are located in /var/log (= a system folder, you can hit Alt+F2, type /var/log and press Enter to go there) and you are looking for error messages (probably originating from the kernel). It's not a precise procedure..

If what konqueror7 proposed doesn't work, then **right after your system hangs and you reboot**:

1. Open a console window
2. tail -n 5000 /var/log/messages > ~/Desktop/last_messages
3. tail -n 5000 /var/log/kern.log > ~/Desktop/last_kern

(*The OpenOffice log file would help too, but I'm not sure where it's located.. Will have a look and post back.*)

On your desktop two new files should appear, *last_messages* and *last_kern*. They will probably be lengthy, so it's best to attach them (and not include them as text) to a new post in this thread.

---

### Post by mje1708 on 2010-03-23
Hi

I'm not entirely sure what you mean by "increase the memory allocations" in OpenOffice.

I went into Write and opened Tools->Options->Openoffice.org->Memory and increased Mb assigned to graphics cache - both "use for open office.org" and "Memory per object".

Is that what you meant?

btw - somebody suggested I have system monitor open to see what could be going on. I have it open and for some reason for the last hour or two there has been no freezing. Could system monitor be doing something to help rather than just monitor?

(you can see how ignorant I am :))

Thanks

Mike

---

### Post by konqueror7 on 2010-03-24
> **mje1708 said:**
> Hi

I'm not entirely sure what you mean by "increase the memory allocations" in OpenOffice.

I went into Write and opened Tools->Options->Openoffice.org->Memory and increased Mb assigned to graphics cache - both "use for open office.org" and "Memory per object".

Is that what you meant?

btw - somebody suggested I have system monitor open to see what could be going on. I have it open and for some reason for the last hour or two there has been no freezing. Could system monitor be doing something to help rather than just monitor?

(you can see how ignorant I am :))

Thanks

Mike


yes, it will try to use more memory so it could run better,,,

system monitor? unlikely, they just wanted a overview or screenshot of the running services, if it's OpenOffice.org that really the problem is...:o

---

### Post by mje1708 on 2010-03-24
For some reason the problem seems to have improved dramatically - I have no idea why!

When I first started this it was freezing up repeatedly after about 10 mins or so of opening an OpenOffice program. Now it has only frozen once in last day or two.

Maybe the memory increase thing worked - aside from that I have done nothing other than change the version I was using (which appeared to have no effect).

So not sure what to do now ???

But next time it freezes I will take note of the exact time, print the logs as 666f6f suggests and post them here.

---

### Post by 666f6f on 2010-03-24
Well, since it happens even after you have shutdown OOo, I doubt it's a memory consumption problem. Also, from the fact that it freezes after a day or two reduces the possibility to be OOo related at all.. at least to my mind. Also, I did a quick Google Search and I haven't found any incidents reporting full system freeze because of OOo.

Don't want to be pessimistic but maybe it's a hardware failure? How old is your equipment? What are your system specs? The logs would certainly help.

In case I'm totally wrong, I apologise in advance..

---

### Post by mje1708 on 2010-03-25
This problem is getting weird. It was mostly fine last night. Left the PC on all night with OpenOffice and various other things running. Got up this morning - no problem - system still running. Played around with a few things and again no problem. Had breakfast and came back 5 minutes later and the system had frozen again.

So anyway as suggested earlier I have run the two commands to print out the logs. They are attached to this message. The freeze, according to the Linux clock on my screen, happened at 7:53am on 25/3. I have had a look at the logs but don't know what I am looking for. Can anyone else enlighten me?

As for my system - it is fairly old now - an HP Pavilion A509UK. These are the specs for the m/board -

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00100539&lc=en&cc=us&dlc=en&product=412535&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00100539&lc=en&cc=us&dlc=en&product=412535&lang=en) 

The motherboard however is brand new - I just put it in a few weeks ago but using the original processor and fan. The hard disc is not original and neither is the RAM (I Meg) - they are both around 2 yrs old. I am using onboard graphics - no card. I do have Windows installed as well but have to say haven't really used it much since I installed Ubuntu - but in the short times I have used it, there have been no issues of freezing.

For the moment I am not going to run OpenOffice at all - if nothing freezes for the next week I will run it again and see if the freeze comes back - at least that way I will know for sure whether the problem is somehow connected to it.

Thanks for everyone's help so far - it is much appreciated.

Mike

'

---

### Post by mje1708 on 2010-03-25
Am struggling on how to post attachments to a post. Thought I had done it ok but nothing is showing up. I clicked on attach and then uploaded files - but nothing appears on the post itself. How do I attach the uploaded file to the post?

Thanks

---

### Post by 666f6f on 2010-03-25
hmm... I think the files must have a file extensions.. like *.txt

---

### Post by mje1708 on 2010-03-25
I have added .txt to each file - hopefully that will work. I think they were also too big so I have just extracted the relevant bit.

---

### Post by mje1708 on 2010-03-25
And hopefully here is the second.

btw - whilst I was editing these files in ABIWord the system froze again - so I guess that tells me it is not specifically the program OpenOffice which is causing the problem. Not sure how much that helps :(

I am wondering if it would perhaps help if I downgraded to another version of Ubuntu..... 8.10 perhaps? (Does this exist? - I have only heard mention of 8.04)  

I would really like to continue using Ubuntu on this desktop - when it is not freezing, it runs so much better than it does on Windows. I also run Ubuntu 9.10 Remix on my Asus EEE PC900 Netbook. This came preinstalled with Windows and was frankly a little bit of a disappointment. However with Ubuntu it runs fantastically and now is a pleasure to use - it doesn't have any freezing problems - or any other issues for that matter.

---

### Post by 666f6f on 2010-03-25
Hi Mike,

Your /var/log/kern.log and /var/log/messages are filled with

```

Mar 25 07:57:34 mike-desktop kernel: [31680.584106] Call Trace:
Mar 25 07:57:34 mike-desktop kernel: [31680.584123]  [<c0572b76>] __mutex_lock_slowpath+0xc6/0x130
Mar 25 07:57:34 mike-desktop kernel: [31680.584130]  [<c0572a90>] mutex_lock+0x20/0x40
Mar 25 07:57:34 mike-desktop kernel: [31680.584174]  [<f82568fa>] i915_gem_retire_work_handler+0x2a/0x70 [i915]
Mar 25 07:57:34 mike-desktop kernel: [31680.584185]  [<c01579de>] run_workqueue+0x6e/0x140
Mar 25 07:57:34 mike-desktop kernel: [31680.584207]  [<f82568d0>] ? i915_gem_retire_work_handler+0x0/0x70 [i915]
Mar 25 07:57:34 mike-desktop kernel: [31680.584215]  [<c0157b38>] worker_thread+0x88/0xe0
Mar 25 07:57:34 mike-desktop kernel: [31680.584220]  [<c015c180>] ? autoremove_wake_function+0x0/0x40
Mar 25 07:57:34 mike-desktop kernel: [31680.584225]  [<c0157ab0>] ? worker_thread+0x0/0xe0
Mar 25 07:57:34 mike-desktop kernel: [31680.584229]  [<c015be8c>] kthread+0x7c/0x90
Mar 25 07:57:34 mike-desktop kernel: [31680.584232]  [<c015be10>] ? kthread+0x0/0x90
Mar 25 07:57:34 mike-desktop kernel: [31680.584238]  [<c0104047>] kernel_thread_helper+0x7/0x10
Mar 25 08:01:34 mike-desktop kernel: [31920.584069] i915/0        D c08185c0     0   240      2 0x00000000
Mar 25 08:01:34 mike-desktop kernel: [31920.584076]  ef669f04 00000046 f73ea000 c08185c0 ef664df8 c08185c0 17d685ac 00001ce2
Mar 25 08:01:34 mike-desktop kernel: [31920.584086]  c08185c0 c08185c0 ef664df8 c08185c0 17d65366 00001ce2 c08185c0 ef754a00
Mar 25 08:01:34 mike-desktop kernel: [31920.584093]  ef664b60 ef492814 ef492818 ffffffff ef669f30 c0572b76 c074ce80 ef49281c

```

Pay attention that messages exist even after your screen frozen, that means that your system was still alive but your GPU was not responding, i.e froze :-( 

There are many users reporting the problem and there even exists a relevant bug in launchpad [here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/451518").

From here on I would suggest the following:

Firstly fully update your system, maybe the latest kernel or the latest xserver-xorg-video-intel fixes the problem (I doubt so, but maybe I'm wrong). If it's fixed, that's cool, you can even report your success back to the relevant bug item discussion (the devs will be very very happy).

If it's not fixed, you can either downgrade to [8.04]("http://releases.ubuntu.com/8.04/") or [8.10]("http://releases.ubuntu.com/8.10/") (but not 9.04), or you can try to participate in the discussion in the bug page and troubleshoot the problem.

Hope this helps,
666f6f

---

### Post by mje1708 on 2010-03-26
Unfortunately I have already updated everything so clearly bug is not fixed yet in 9.10. What about 10.04? Is that going to be very different? I have read some articles which say it is not much different to 9.10 and others which say it is completely new.

Otherwise what is the easiest way to downgrade to 8,10?  Is a complete reinstall best?

But before I do anything I was planning to put a video card in this PC. Is it possible this could help the problem. Is the bug video related in any way?

Thanks for all your help

Mike

---

### Post by konqueror7 on 2010-03-26
it could definitely be a video card issue based on the log...

if you have a spare video card, then you could try it on, but if not, try going to 8.04 or 10.04, since they are LTS, you could possibly get better updates from that...oh, is compiz running or not?

---

### Post by mje1708 on 2010-03-26
I have the video card in now and so far so good.

It certainly fixed a video problem I was having with skype.

But only time will tell - if no freezes for the next few days I will report back and confirm.

Thanks everyone for their help.

---

### Post by 666f6f on 2010-03-26
> **mje1708 said:**
> I have the video card in now and so far so good.

I'm quite confident that this will fix the problem.

---

### Post by 666f6f on 2010-03-26
> **mje1708 said:**
> Otherwise what is the easiest way to downgrade to 8,10?  Is a complete reinstall best?

I don't think there is an easy way to downgrade however, if you keep your /home directory in a separate partition (I highly recommend doing so..), it shouldn't be much trouble to install Ubuntu 8.* from scratch. Normally there should be no user files outside that directory (/home).

---

### Post by mje1708 on 2010-03-26
Well it looks like you could be right - I am working from home today and purposely using the desktop as much as I can - opening multiple OpenOffice files, browsing internet - leaving everything open ....

and no freezes whatsoever so far ... so fingers crossed :)

---

### Post by 666f6f on 2010-03-26
> **mje1708 said:**
> Well it looks like you could be right - I am working from home today and purposely using the desktop as much as I can - opening multiple OpenOffice files, browsing internet - leaving everything open ....

and no freezes whatsoever so far ... so fingers crossed :)

I really hope so too.. let's be optimistic and see how it goes :-)

---

### Post by mje1708 on 2010-03-26
Have been using the PC quite extensively for whole of day now since fitting graphics card - no freezes or any other problems whatsoever

Ubuntu and OpenOffice are both running smoothly and perfectly and getting along fine. I have played movies, downloaded files, browsed internet, compiled spreadsheets and documents of varying complexities all without difficulty!

** .... and so I think I am cured :)**

(Hope I haven't spoken too soon)

Thanks guys for all of your help. 

Hopefully this is my last post on this subject !

---

