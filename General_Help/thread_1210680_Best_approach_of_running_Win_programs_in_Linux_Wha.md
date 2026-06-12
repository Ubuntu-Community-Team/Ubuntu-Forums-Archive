---
title: "Best approach of running Win programs in Linux? What's your opinion?"
date: 2009-07-11
forum: General Help
---

### Post by masterton on 2009-07-11
In your opinion what is the best approach to run Windows programs in Linux environment? So far those are the _feasible_ options that I'm aware:
[LIST=1][*]Wine
[*]OS Virtualization (eg. VMware)[/LIST]
Is there any other approach that I'm unaware of?
How do you comment/compare on each approach? Which is better?

The following factors come into mind:
[LIST][*]Compatibility (ie. how many programs can I start successfully and run with as few flaws as possible?)
[*]Performance (how much resources does it consume more than if I run Windows programs natively, generally speaking?)[/LIST]
I'm using ubuntu right now. Hopefully ubuntu has the best support to run Windows programs on it. If not, please tell me alternative Linux distro so I can try out too.

Any input is appreciated. Share your views. :)

PS:
1. Assume modern PC like dual-core CPU, 2x2 GB RAM. They are cheap anyway.
2. Production PC, not for modern games. I would like to know roughly about the performance drain when running advanced 2D video/graphic editors like Photoshop, or analysis/statistics software like SAS.

---

### Post by Yvan300 on 2009-07-11
Well it is according your system specs. Although wine is lighter on the system, a lot of programs would not run as good in a VM. That being said a VM aproach would only be better if you have more than 1GB of ram. Also playing games in a Vm would me kinda more difficult than in wine due to the additional system drain. Buttom line it is determined by the system you are running.

---

### Post by Finalfantasykid on 2009-07-11
I would have to go with virtualization.  You may not get quite as much performance as with wine, but my personal experience with wine has not been that great.  The compatability is not that great IMO.

I would use VirtualBox for running other operating systems.  I find it has better performance and flexibility than VMWare.  You can even download the Windows 7 RC from microsoft's servers and install it.  I've tried it out and it works!

---

### Post by XCan on 2009-07-11
Firstly it depends very much if you're refering to games or not. For modern games I would always choose Wine (although Vbox is starting to gain the possiblity for acceleration but as of right now I would choose Wine).

Actually, I would always choose Wine if the program is working. I've noticed that many programs even use less resources, and people have reported higher performance in Wine.

---

### Post by nice_like_rice on 2009-07-11
Yes - games running with OpenGL often run better with wine than natively! However directx games usually don't.

Have you heard of seamless virtualization, it's a great alternative if wine doesn't support that application.

---

### Post by masterton on 2009-07-11
1. Assume modern PC like dual-core CPU, 2x2 GB RAM. They are cheap anyway.
2. Production PC, not for modern games. I would like to know roughly about the performance drain when running advanced 2D video/graphic editors like Photoshop, or analysis/statistics software like SAS.

---

### Post by masterton on 2009-07-11
> **XCan said:**
> Actually, I would always choose Wine if the program is working.
Let's say you try a new program in Wine (you never run it in Windows since you haven't used Windows for quite some time). It runs fine but it seems have a bit minor quirks. This makes you wonder which is the culprit - a bug in the program or Wine.

I wonder how compatible it is if I run it in virtual OS. Will it work nearly as perfect as how you run it natively.

> **XCan said:**
> I've noticed that many programs even use less resources, and people have reported higher performance in Wine.
That's new to me. I supposed it's usually, if not always, suffer from performance drain, even if it's tiny.

---

### Post by masterton on 2009-07-11
> **nice_like_rice said:**
> Have you heard of seamless virtualization, it's a great alternative if wine doesn't support that application.
What is seamless virtualization? How well does it do in terms of compatibility and performance?

---

### Post by masterton on 2009-07-12
Have anyone tried [Crossover](http://www.codeweavers.com/), another program similar to Wine?

---

### Post by nice_like_rice on 2009-07-12
Nope, never tried it. Sounds like an application whose name I forget (beginning with C? cerrava or something) to run win games on linux, I think wine probably supports more games than that.

[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization) 

There is a wiki page on it somewhere, but I can't find it today for some reason. If you don't need the windows desktop but want the windows applications it's really useful.

---

### Post by 6205 on 2009-07-12
IMO personally i would never rape my ubuntu with win apps, but that's probably not going to help you...

---

### Post by TeamJ on 2009-07-12
Wine is straightforward, fast, easy but doesn't always work cos of the way the application is unable to interact
VMWare will always work, but can be slow

---

### Post by jskandhari on 2009-07-12
unless you planning not to run apps like office or something like that which require multiple libraries and are not a pro use a wine but if you want to run all those complex apps use VM...

games and simple and some complex apps run like butter in wine

---

### Post by Blacklightbulb on 2009-07-12
Have you considered a linux alternative. I know some programs (CAD) have no real linux alternatives but other general purpose programs have hundreds of possibly better linux alternatives.

---

### Post by masterton on 2009-07-12
> **nice_like_rice said:**
> [https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization) 

There is a wiki page on it somewhere, but I can't find it today for some reason. If you don't need the windows desktop but want the windows applications it's really useful.

The pages confuses me. Is Seamless Virtualization a term or some feature/program offered by ubuntu? The first paragraph says I can use **rdesktop** to run virtualized programs directly on your Linux desktop without installing Windows. Then it talks about Wine, Windows XP pro VM, QEmu and VirtualBox.

What is it really talking about? Is it just another page which tells us how to use VMware or QEmu? Hmm...

---

### Post by masterton on 2009-07-12
> **6205 said:**
> IMO personally i would never rape my ubuntu with win apps, but that's probably not going to help you...

> **Blacklightbulb said:**
> Have you considered a linux alternative. I know some programs (CAD) have no real linux alternatives but other general purpose programs have hundreds of possibly better linux alternatives.
Different people have different needs. I would also want to recommend others to try out Linux distros. But most have been too into Windows programs. It take quite some time to find alternatives and do some switches.

Is there any site or way to help people to switch or find alternatives easily?

---

### Post by chriskin on 2009-07-12
> **Finalfantasykid said:**
> I would have to go with virtualization.  You may not get quite as much performance as with wine, but my personal experience with wine has not been that great.  The compatability is not that great IMO.

I would use VirtualBox for running other operating systems.  I find it has better performance and flexibility than VMWare.  You can even download the Windows 7 RC from microsoft's servers and install it.  I've tried it out and it works!


i agree with this one @ 99%
i think, though, that there is good enough compatibility in wine as well. not perfect , i know, but not all that bad

yet virtualbox is better if you really want to do something and wine can't help you

---

### Post by masterton on 2009-07-12
So VMware has full compatility but can be slow (how slow is it? Like 50% off or...?). 
Wine has mixed compatibility (but how well does it go?) but run without performance drain (sometimes even faster than running natively).

I check the Wine compatibility database but there isn't fast way to know roughly how well Wine is doing (eg. how many platinum/gold/silver/bronze/garbage in total?)
I have to check on each entry to check whether it's supported or not.

---

### Post by chriskin on 2009-07-12
> **masterton said:**
> So VMware has full compatility but can be slow (how slow is it? Like 50% off or...?). 
Wine has mixed compatibility (but how well does it go?) but run without performance drain (sometimes even faster than running natively).

I check the Wine compatibility database but there isn't fast way to know roughly how well Wine is doing (eg. how many platinum/gold/silver/bronze/garbage in total?)
I have to check on each entry to check whether it's supported or not.

there is always the full compatibility And fast virtualbox :P

---

### Post by nice_like_rice on 2009-07-12
> **masterton said:**
> The pages confuses me. Is Seamless Virtualization a term or some feature/program offered by ubuntu? The first paragraph says I can use **rdesktop** to run virtualized programs directly on your Linux desktop without installing Windows. Then it talks about Wine, Windows XP pro VM, QEmu and VirtualBox.

What is it really talking about? Is it just another page which tells us how to use VMware or QEmu? Hmm...


I'll explain what it is.  The thing which I personally find annoying with running an app in a VM is that you constantly have to open and close the VM, and see the windows desktop, but what if you wanted for example to use an app in a VM, but also chat with pidgin? With seamless virtualization, the program from windows is given its OWN window under ubuntu. Look closely at the picture on that webpage I sent you, you will see IE is running under ubuntu in it's own window, even though it is in a type of VM.

---

### Post by Slim Odds on 2009-07-12
> **6205 said:**
> IMO personally i would never rape my ubuntu with win apps, but that's probably not going to help you...

Contrary to the belief of some, there are some perfectly good applications that are Windows only.

Personally, I use WINE if it works, otherwise VirtualBox.

It's far easier and more natural to run an application using WINE. You just run it.

With VirtualBox you have to start the new OS and then run the application. That's a little more effort and a little less natural.

---

### Post by masterton on 2009-07-12
> **nice_like_rice said:**
> I'll explain what it is.  The thing which I personally find annoying with running an app in a VM is that you constantly have to open and close the VM, and see the windows desktop, but what if you wanted for example to use an app in a VM, but also chat with pidgin? With seamless virtualization, the program from windows is given its OWN window under ubuntu. Look closely at the picture on that webpage I sent you, you will see IE is running under ubuntu in it's own window, even though it is in a type of VM.
Simply speaking, so the Seamless Virtulization is a way to integrate the VM into ubuntu.

Must I need to install either VMware / QEmu / VirtualBox to work with the "Seamless Virtulaization" thing?

The instructions states: "Start a Windows XP pro VM"
What is Windows XP pro VM? Where can I fire that up?

The instruction is poorly written for new users like me. Many middle steps have been skipped so I can't follow what it says.

---

### Post by masterton on 2009-07-12
> **chriskin said:**
> there is always the full compatibility And fast virtualbox :P
Do you mean there is (nearly) no performance drain if it's run under VirtualBox? Well then it would be best of both world. Sounds really interestin. :D

> **Slim Odds said:**
> It's far easier and more natural to run an application using WINE. You just run it.
One annoyance I find is I couldn't double click to run the program. The program is wrongly handled by an archive manager. I have to right click and select run with wine. :(

---

### Post by Chronon on 2009-07-12
I believe that's a mis-statement.  I believe that VirtualBox probably offers similar performance to other virtualization methods.  I would like to see the "fast" assertion quantified as it's currently only a subjective qualifier.  

It's not a slam on VirtualBox as I use it and think it's quite a nice option for running Windows software if you already own a licensed copy of it.  I simply think it's a bit misleading to suggest that you get to have your cake and eat it too.

Regarding the automatic launching with WINE, you should be able to set it as the preferred application somewhere in your desktop environment.

---

### Post by nice_like_rice on 2009-07-12
masterton, which applications are you specifically trying to use? Overall, wine is usually the best solution (if you cant find an alternative), I am just suggesting seamless virtualisation as an alternative if it doesn't work with wine, and a virtualbox is too annoying. 

> 
Must I need to install either VMware / QEmu / VirtualBox to work with the "Seamless Virtulaization" thing?


Yes

> 
What is Windows XP pro VM? Where can I fire that up?


You must install windows on a virtual machine, you need a windows install disk/iso.

---

### Post by masterton on 2009-07-12
> **Chronon said:**
> I believe that's a mis-statement.  I believe that VirtualBox probably offers similar performance to other virtualization methods.  I would like to see the "fast" assertion quantified as it's currently only a subjective qualifier. 
Okay. It should be too good to be true. 

> **Chronon said:**
> It's not a slam on VirtualBox as I use it and think it's quite a nice option for running Windows software if you already own a licensed copy of it.  I simply think it's a bit misleading to suggest that you get to have your cake and eat it too.
So how does VirtualBox perform?
I think they probably like full compatibility if the performance drain is only a little bit, or not noticeable.

> **Chronon said:**
> Regarding the automatic launching with WINE, you should be able to set it as the preferred application somewhere in your desktop environment.
Well isn't there a bug which prevents this from working:
[http://ubuntuforums.org/showthread.php?t=885111](http://ubuntuforums.org/showthread.php?t=885111)
> Unfortunately, due to a bug in 8.10 and 9.04, you cannot simply double click .exe applications and must right click instead - double clicking will cause file-roller to attempt to open them and give up.

---

### Post by masterton on 2009-07-12
> **nice_like_rice said:**
> masterton, which applications are you specifically trying to use? Overall, wine is usually the best solution (if you cant find an alternative), I am just suggesting seamless virtualisation as an alternative if it doesn't work with wine, and a virtualbox is too annoying. 
No, I don't know. This is a general question which I want to ask before recommending others to use ubuntu/linux to replace Windows. They should have some programs they want to run, or just don't have the time to find alternatives and relearn things. I'd better learn more before I promote it to my fellows.

Yep seamless virtualisation sounds interesting but the documentation is confusing. I don't know how to set this up.

> You must install windows on a virtual machine, you need a windows install disk/iso.
Yes so steps:
1. Install VMware/VirtualBox. 
2. Set up a virtual machine. 
3. Install Windows inside the virtual machine. 
What's next?
(hey, could someone clean up the documentation a bit? It appears the documentation is mixed with instructions of various products here and there which confuse me. Probably I haven't tried any of them yet so I get confused)

---

### Post by frumenti on 2009-07-15
nice_like_rice: I have older version of VMWare and virtual box. I want to run xp/vista on ubuntu. I don't understand your post. Does your version of ubuntu have a "seamless virtualization feature" or are you talking about rdesk or VMWare? I don't run games but I run multimedia and need xp/or vista to use 2 sony 200disc changers. Thanks in advance for any help you can give.

> **nice_like_rice said:**
> I'll explain what it is.  The thing which I personally find annoying with running an app in a VM is that you constantly have to open and close the VM, and see the windows desktop, but what if you wanted for example to use an app in a VM, but also chat with pidgin? With seamless virtualization, the program from windows is given its OWN window under ubuntu. Look closely at the picture on that webpage I sent you, you will see IE is running under ubuntu in it's own window, even though it is in a type of VM.

---

### Post by LinuxBob on 2009-07-17
I want slingplayer to run in 9.04.  Wine does not cut it , not yet anyway.  I also want to run MS access as OpenOffice Base is a bear, particularly when all I need is a single table database to keep track of my home and automobile maintenance records.  While all components of my Office 97 load under Crossover, Access will not (it won't on a true XP machine either due to some conflict with one of the XP SP upgrades).

So I am looking at rdesktop to connect to my Win XP machine residing on my same home LAN.  Not sure if this will display fullscreen on the Ubuntu desktop which is kinda key when wanting to watch SLingplayer. Slingplayer enables me to forego a second or third $13/month cable box.  I also think Office 2007 Access will work with XP SP2.


Alternatively, I am looking at virtualbox.  I do not have, however, Win XP on disk.  What I have is a 7 disk set received when I purchased the HP Media Center PC I am now runnning Ubutnu exclusively on.  Can I use these system recovery disks to load XP under Virtualbox?  If not, can I purchase XP disks or download somewhere?

---

### Post by LinuxBob on 2009-07-17
By the way, I am separately adressing the audio feed from Slingplayer using a wireless transmitter receiver pair from RCA.  I use these now to pipe Pandora, for exmaple, to all my stereo receivers throughout the house.

---

