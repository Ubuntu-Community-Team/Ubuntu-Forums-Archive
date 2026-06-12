---
title: "Moved to Linux.Need Macromedia Flash. What are my posibilities?!"
date: 2006-05-19
forum: General Help
---

### Post by seth0x2b on 2006-05-19
Hey guys. First of all I know there are alot of Macromedia related threads on this forum. I did a search but I didn't find anything too relevant to my situation.
I work in advertising.
My daily basis tools are Alias Maya 7, Photoshop 7(for some reason I hate CS :) ), Gimp, Corel Draw 12.
My Maya package comes with a Linux version and I got it up an running in notime thanks to Ubuntu :) 
I used Fedora Core 3 for about 1.5 years and I couldn't even get my ATI 9200SE set up(on this topic..if anyone can help me boost  up my FPS.:( I still have no replies to this thread [http://www.ubuntuforums.org/showthread.php?t=174865&highlight=9200se+fps](http://www.ubuntuforums.org/showthread.php?t=174865&highlight=9200se+fps)  so probably no one has a solution..but maybe...just maybe :) ).
So: Maya is ok. Gimp is already there. I am now installing Photoshop 7 through  wine, but I don't think I'll have any problems there(on Fedora it worked just fine).
My questions are about Corel 12 and Macromedia Flash 8:
I read a How To on a Suse forum regarding Flash 8 instalation, I tried it with no luck so I gave up. I am still looking for one on Corel Draw 12. Anyone that can share the knowledge is very welcomed to do so.
So: I am going to erase my windows partition and install one of the 2 posibilities:
a) QEMU: I want it because it's open source, but I read on the wiki that it has no "special" drivers. What does that exactly mean?! I can't install video drivers and if so, does that hurt my Flash performance?!(I know this is not really a Linux question but I figure i'm not the only one trying to emulate Flash on Linux :) )
2) I (well my boss actually) will buy VMWare if is has something extra over QEMU, but only if it improves my Flash performance, or keep it close to what Windows offers.
Second "problem" is Corel Draw 12. If I can't install it via wine, and wish to use it with an emulated Windows install, I have the same "problems" as with Flash: will I have poor performance with QEMU, or will it run nice?!

My system specs are AMD 2000+, Ati Radeon 9200SE, 640 MB Ram(for now).

I thank everyone that shows interest in my thread and welcome any hint/advice.

Cheers

---

### Post by Lord Illidan on 2006-05-19
I would advise you to dualboot for the time being. Is there any specific reason you want to delete windows partition?

---

### Post by seth0x2b on 2006-05-19
Well apart from not liking to boot every time(it's no hastle..but it is time wasted), I am tired of Windows crashing for some reason I don't know and have no way of finding out.( I know that the same crashes can happen in the emulated install, but at least I can freeze - from what I know - Windows at a certain state and boot in in like 5 seconds or so..).
I know windows has it's advantages on the software part, and I really don't plan on turning this into one of other 1000+ antiwin flamewars.
I thought I'll give it a go, and if I am satisfied with the result, abandon Windows booting. That's all.

You're advice is more than welcomed.I'll wait some time for other(or the same) opinion before I proceed to erase.

Cheers

---

### Post by nzmoose on 2006-07-26
It's not an amazing solution. But have you considered Using VMware server to run a windows virtual machine?
At least it would cut down on boot time

---

### Post by ifokkema on 2006-07-28
> **seth0x2b said:**
> 2) I (well my boss actually) will buy VMWare if is has something extra over QEMU, but only if it improves my Flash performance, or keep it close to what Windows offers.
VMWare is nice, but you don't have to buy it. You can download VMWare server from [their website]("http://www.vmware.com/products/server/") and it'll allow you to create a Windows virtual machine. VMWare Player, which has a package in the dapper repositories, has been free for a longer time but doesn't allow you to create virtual machines.

---

