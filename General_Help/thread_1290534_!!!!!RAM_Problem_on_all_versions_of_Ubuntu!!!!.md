---
title: "!!!!!RAM Problem on all versions of Ubuntu!!!!"
date: 2009-10-13
forum: General Help
---

### Post by yo2boy on 2009-10-13
Hey, I got a small question for you all..

Uhh.. for some reason, Ubuntu says that I have 497.6MB of RAM (1.70GHz processor), when I fully have a solid 512mb. Why is it saying that? And I've noticed that my performance is slower than it is in Windows XP which gives the correct amount of RAM (512mb 1.70GHz).

Is it anything driver related?

Yes, it's the same whether or not I'm dual-booting, using a Wubi-install or just using the LiveCD.

Do you guys want a screenies? If so, put that into your response.

Thanks.

---

### Post by collinp on 2009-10-13
There could be a few things that are causing this:

[LIST=1]
[*]Linux could be reading the RAM differently
[*]Some of the ram could be reserved for system use
[*]You could have bad ram and not know it
[/LIST]
Have you ran a memory check yet?

---

### Post by sgosnell on 2009-10-13
512,000,000 is not 512MB.  I'm not sure exactly how much you have, but manufacturers often over-rate their products, calling 1,000,000 a megabyte.  See [whatsabyte.com](http://www.whatsabyte.com/).

It may be this, or you may have a defective RAM stick.

---

### Post by yo2boy on 2009-10-13
> **Hellow said:**
> There could be a few things that are causing this:

[LIST=1]
[*]Linux could be reading the RAM differently
[*]Some of the ram could be reserved for system use
[*]You could have bad ram and not know it
[/LIST]
Have you ran a memory check yet?

Memory check? I'll try that.

---

### Post by yo2boy on 2009-10-18
Bump

I did a Memory Check and I successfully passed. I DO have 512mb of ram. I still don't understand why it's saying I have 497.6mb of ram.

---

### Post by mechro on 2009-10-18
Have you got on board graphics using system ram?

---

### Post by yo2boy on 2009-10-18
@[mechro]("http://ubuntuforums.org/member.php?u=922703")

I'm not sure. How do I check? The system monitor?

---

### Post by DGortze380 on 2009-10-18
Two most common causes...

512mb is not really 512mb, sorry.
Your ram manufacturer is likely calling 512,000,000 B 512MB.
Really there is 1024B in a kB, and 1024kB in a MB ... that works out to 488.28MB

More likely is that you do have 512MB of RAM, but are using onboard video which reserves a portion of that memory, thus it is not available to the OS.

---

### Post by kauboy on 2009-11-04
If you had a closer look at System Monitor reporting your RAM, it's in MiB, not MB used by Windows. I suggest you check out [http://en.wikipedia.org/wiki/Mebibyte]("http://en.wikipedia.org/wiki/Mebibyte") for a comparison. There is probably no problem at all in it reporting 497 MiB! :D

---

### Post by fluffman86 on 2009-11-04
RAM is always listed in MiB, so 512 is 512.  You probably just have a few megs set aside for onboard video.

In other words, if you didn't install a video card, you have onboard video, and that requires RAM to run.

---

### Post by gordintoronto on 2009-11-04
> **fluffman86 said:**
> RAM is always listed in MiB, so 512 is 512.  You probably just have a few megs set aside for onboard video.

In other words, if you didn't install a video card, you have onboard video, and that requires RAM to run.

I have a Compaq SR1055CL with "512 MB" of RAM, and a PCI video card.  System Monitor says I have 497.4 MiB of memory.

My other system has 4 GB of memory, and a video card.  System monitor reports 3.8 GB of memory.

---

### Post by 3rdalbum on 2009-11-04
I have 6 gigabytes of RAM and only 5.8 GiB of RAM.

I never thought of it before, but I'm sure this must be the explanation: RAM manufacturers now must be treating a megabyte as one thousand kilobytes.

---

### Post by PRC09 on 2009-11-04
I have a system similar to your Compaq and also a PCI video card as well.The spec on your machine says it has onboard video with up to 64 meg shared memory for video.On my machine altho I have added the pci card the bios still is assigning 16 meg for onboard video.Thus 512-16=496.Some machines automatically disable onboard video but in this case obviously it hasnt.Hope this helps.*NOTE* When I disabled this setting after installing 9.04 it would not boot so I had to turn it back on again.......

---

### Post by gordintoronto on 2009-11-05
> **PRC09 said:**
> I have a system similar to your Compaq and also a PCI video card as well.The spec on your machine says it has onboard video with up to 64 meg shared memory for video.On my machine altho I have added the pci card the bios still is assigning 16 meg for onboard video.Thus 512-16=496.Some machines automatically disable onboard video but in this case obviously it hasnt.Hope this helps.*NOTE* When I disabled this setting after installing 9.04 it would not boot so I had to turn it back on again.......

Thanks!  That adds clarity, although there doesn't seem to be anything I can do about it.

---

### Post by ezsit on 2009-11-05
> although there doesn't seem to be anything I can do about it. 

Was the difference between 497 and 512 really causing so much concern? Did the missing memeory prevent something from running? I really don't get all the hoopla over ~16MB of ram. ;-)

---

### Post by wnderinguy34 on 2009-11-06
512MB US = 497.6MB Cdn ;)

seriously though,512mb is a little low,I'd up the total X2 at least.

---

### Post by SunnyRabbiera on 2009-11-06
Well with RAM readings in both windows and linux are never exactly the same, windows and linux detect and use RAM in completely different ways from eachother.
But often Linux is actually more accurate at detecting true HD space and RAM, it mighty say 70GB on the side of the box when you look at your HDD but you really only have 68GB , 64GB after a install of Linux as linux can take up 4GB in a install.
RAM usage is simular, linux utilizes RAM much differently then windows and only uses it when it is needed.
Also consider your 3GB of ram issue too, if you are using Ubuntu 32bit you have a limit of 3GB of RAM.
This is not Linux specific though, 32bit kernels have a 3GB RAM limit.

---

