---
title: "Word/Excel in Ubuntu"
date: 2012-08-26
forum: General Help
---

### Post by coloreporter on 2012-08-26
I'm someone who regularly uses Word and Excel.  I'm forced to used these programs at school and work so I'm wondering how I'll be able to access files at home on Ubuntu.  Does LibreOffice read/write docx and xlsx files without any errors or would I be better off just using Excel and Word through Wine?

---

### Post by vexorian on 2012-08-26
LibreOffice does an ok job in opening those files. Sharing them with people in situations where both of you edit the files continuously is an issue though because between Office not implementing their own format correctly and they not documenting it well, there is high probability of small changes between a program to the other.

If you need very good MSOFfice document format compatibility, I would recommend VirtualBox and run MSOffice in there. (With things like seamless windows and easy sharing between host machine and guest it is not very painful to do) . Perhaps WINE can do an ok job to do. 

Worst case scenario, you might need to dual boot.

---

### Post by coloreporter on 2012-08-26
> **vexorian said:**
> LibreOffice does an ok job in opening those files. Sharing them with people in situations where both of you edit the files continuously is an issue though because between Office not implementing their own format correctly and they not documenting it well, there is high probability of small changes between a program to the other.

If you need very good MSOFfice document format compatibility, I would recommend VirtualBox and run MSOffice in there. (With things like seamless windows and easy sharing between host machine and guest it is not very painful to do) . Perhaps WINE can do an ok job to do. 

Worst case scenario, you might need to dual boot.
Thanks for the response.

Why do you recommend VirtualBox above Wine?  Is it your preference for running any Windows programs in Ubuntu?

I'm currently dual booting, but would like to move to only Ubuntu eventually.  I suppose it's not a big deal though to have two operating systems on one computer.

---

### Post by Petro Dawg on 2012-08-26
> **coloreporter said:**
> I'm someone who regularly uses Word and Excel.  I'm forced to used these programs at school and work so I'm wondering how I'll be able to access files at home on Ubuntu.  Does LibreOffice read/write docx and xlsx files without any errors or would I be better off just using Excel and Word through Wine?


The biggest issue is when macros and/or VBA is involved.  If you use excel sheets that require macros in the calculations you will have issues using/editing them in Calc.

If you just do basic spreadsheet calculations it'll convert pretty well.  I haven't ran into much problem with Word and Writer compatibility.  However I will admit, I rarely use writer.

---

### Post by vexorian on 2012-08-27
> **coloreporter said:**
> Thanks for the response.

Why do you recommend VirtualBox above Wine?  Is it your preference for running any Windows programs in Ubuntu?

I'm currently dual booting, but would like to move to only Ubuntu eventually.  I suppose it's not a big deal though to have two operating systems on one computer.
I like WINE better, but it has less success with complex GUI apps. And MSO are the epitome of apps that have issues running in WINE.

VirtualBox I don't like, because it is almost like dual boot (you need a windows license). But I know that for things that do not use a lot of GPU, it works great. So you will be more likely to have a 100% good experience without random crashes or glitches and since it is basically running inside windows, results would be identical.

---

### Post by Ravi5kumar on 2012-08-27
> Why do you recommend VirtualBox above Wine?

Wine installs a lot of dependencies......:mad:. Virtual box is best for windows apps. Wine is probably better for games....

---

### Post by Paqman on 2012-08-27
> **coloreporter said:**
> 
Why do you recommend VirtualBox above Wine?

Virtualbox is used to run a 100% authentic copy of Windows, so you can guarantee Windows apps will work perfectly. The downside is that it consumes a lot of resources, since you're running two operating systems at once.

Wine is a native Linux app, so doesn't gobble the resources as much, but it's pretty hit-and-miss how well an individual Windows program will run under it.

---

### Post by vexorian on 2012-08-27
> **Ravi5kumar said:**
> Wine installs a lot of dependencies......:mad:. Virtual box is best for windows apps. Wine is probably better for games....
Meh, the dependencies are not a big deal really. (And in reality, since Virtual Box requires a whole different OS, it needs a lot more dependencies )

Also I am gonna bet you are under a 64bit ubuntu, most of the dependencies are actually libraries that you already have installed, but they are the 32bit support version (WINE is a 32 bit app).

---

### Post by Mark Phelps on 2012-08-27
> **coloreporter said:**
> Thanks for the response.

Why do you recommend VirtualBox above Wine?  Is it your preference for running any Windows programs in Ubuntu?
Virtualbox, using MS Windows, is really the ONLY way to guarantee full compatibility with MS Office files.  MS Word files using the .docx extension have problems being rendered and updated properly in anything other than MS Word.  So, if that is important to you on a daily basis, you really have no useful alternative than to use MS Office in MS Windows.

> I'm currently dual booting, but would like to move to only Ubuntu eventually.  I suppose it's not a big deal though to have two operating systems on one computer.
Great goal -- but impractical as long as you remain dependent on MS Office apps (or other MS Windows apps) that only run properly in MS Windows.  Lots of us continue to dual-boot just for this reason.

---

### Post by coloreporter on 2012-08-27
Thanks for the responses.

I would very much like to work in the Linux equivalent programs, but don't have that option as I work with others that don't.  I use macros and other more advanced functions so absolute compatibility is essential.

It sounds like my best bet is to continue dual booting.  I can use Windows for programs like Office, Photoshop, AutoCAD, and Matlab and Ubuntu for everything else.

---

### Post by PGScooter on 2012-08-27
> **coloreporter said:**
> Thanks for the responses.

It sounds like my best bet is to continue dual booting.  I can use Windows for programs like Office, Photoshop, AutoCAD, and Matlab and Ubuntu for everything else.

Why do you prefer this to Virtual Box? I'm sure there are reasons, but I am curious.

---

### Post by Vaphell on 2012-08-27
indeed, any modern machine should have no problem sparing 1 or 2 cores and 1gig of ram for xp installation. Granted, some heavier PS/ACad/Matlab jobs may require 100% available resources and booting windows is a natural choice then, but i don't consider MSO a heavy use, millions of people do that every day on underpowered cheapass laptops with no problem.

---

### Post by coloreporter on 2012-08-28
> **PGScooter said:**
> Why do you prefer this to Virtual Box? I'm sure there are reasons, but I am curious.
I figure as long as I'm dual booting it would be easier to just use Office on Windows (Vista for me) rather than figuring out Virtual Box.  If that was the only set of Windows programs I needed to run I would definitely go the Virtual Box route.

---

### Post by Petro Dawg on 2012-08-28
> **coloreporter said:**
> I figure as long as I'm dual booting it would be easier to just use Office on Windows (Vista for me) rather than figuring out Virtual Box.  If that was the only set of Windows programs I needed to run I would definitely go the Virtual Box route.


Dual boot is the way to go.

---

### Post by PGScooter on 2012-08-28
> **coloreporter said:**
> I figure as long as I'm dual booting it would be easier to just use Office on Windows (Vista for me) rather than figuring out Virtual Box.  If that was the only set of Windows programs I needed to run I would definitely go the Virtual Box route.

Sounds reasonable. Do note that Virtual Box is extremely easy to set up.

---

### Post by mastablasta on 2012-08-28
> **PGScooter said:**
> Sounds reasonable. Do note that Virtual Box is extremely easy to set up.
 
yes it is very easy to setup. all it takes s basically ot tick the box to boot the virtual computer from the Cd drive and then you stick the windows CD/dvd in the drive and proceed with install just like you would normally.
 
another option is to run linux in virtual box inside windows. also very easy to setup ([http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)) i use it like that because i mostly need windows on one maschine. 
 
you can even run live linux directly from image. this is very good if you need to quickly test a distro and don't want to burn and CD or write the image to USB.
 
office 2007 does install in wine, but i am not sure how well the programmes in it work.

---

### Post by travisf on 2012-08-28
I went down the Virtualbox path a number of years ago with no major  complaints from from my other half who has to use some windows specific  programs for accounting for my business activities. There are absolutely  no compatibility problems because you are not running an emulation but a  real installation which has access to your hardware.

If your  computer specs are reasonable there is never any reason to dual boot  unless you really want to play games which might not work well in WINE.  If you are an avid gamer you might want to run Ubuntu in Virtual box on  Windows and use the Ubuntu side play around with another operating  system or maybe just use it for Internet access. You will probably never  get a virus or malware if you use your Linux instance for internet  access instead of windows.

My computer specs for reference.  Thinkcentre M57P SFF, 3GHz E8400, 8 Gigs Ram, Nvidia GT430 Video, 64bit  Ubuntu 12.04. Quite an old machine but upgraded to the max and probably  slow compared to whats available now. My Virtualbox install of WIndows 7  Pro (32bit, haven't tried 64bit) gets to a usable desktop much faster  than my Toshiba I5 64bit Windows 7  Home Premium Laptop. No doubt the  laptop is also trying to load some Toshiba bloatware but I have removed  much of it. When benchmarked though the Laptop is significantly  faster  than the Virtualbox instance. With 8 Gigs of ram I allocate 2 gigs to  the Windows instance and it does run reasonably fast. In my experience  it is best use a 64bit operating sytem as the host system. I found that  loading very large Excel files painfully slow with a 32bit Ubuntu host and 32  bit Windows. When I changed to a 64bit Ubuntu host the files loaded at least  twice as fast.

Best of luck in what you decide but running  Virtual box in either Ubuntu or WIndows does have a number of advantages  depending on your hardware specs and how fast you really need your  hosted OS to be.

---

### Post by vexorian on 2012-08-28
I have not needed to boot my computer into windows since 2006. And in fact, the only reason I booted it was so I could write work reports like "Works in windows but not in WINE". I leave the dual boot option only because the computer is not only mine.

There are always trade offs.

I think both virtualBox  and dual boot are equal in regards to difficulty of setting them up (they are both non-trivial, in my opinion).

VirtualBox has the disadvantage that you need good RAM. Although I found that in order to run windows XP with a single program (e.g: Excel) you don't need a lot of RAM, seems 500MB is all right.

The main advantage of VirtualBox, to me is that rebooting takes ages to be done. It can break your work flow greatly. VirtualBox on the other hand allows you to start windows without further headache. Since the windows has no internet connection and only has vital packages like MSOffice, it boots very fast and is very light.

VirtualBox has a seamless mode, which means that beyond booting your virtual machine, you can otherwise run the windows app in question in your desktop just fine. You can Copy paste from your Linux programs to windows.

The second advantage I would say is disk space. Separate partitions are a headache when you assign too many space to one OS and too little to the other. With virtualBox, besides of some GB destined to the OS and its apps, you can otherwise use a folder from ubuntu as a "network disk" in VirtualBox and you go on editing your documents.

VirtualBox also gave me the gift of hardware support. There was a time in the last years in which my scanner would not work in ubuntu (It works now), so I needed to run my VirtualBox window (It has USB support, which is great).

Finally, it sets you for a better transition to ubuntu. You keep using your Ubuntu Desktop Environment of choice and get used to it. As opposed to booting into windows and using the old taskbar. It prevents you from sticking to windows apps that can be replaced with ubuntu apps. Like Firefox/Chromium or media players.
---
Dual boot has the advantage that it is easier to allow other people to use windows in your computer with a guest account or an account of their own. And it also has less RAM requirements and can use the GPU full (this means it can run games, virtualBox is not that good at games).



(For games, I use WINE. Now that is a case in which dual booting takes much less work than not dual booting.)

---

### Post by Vaphell on 2012-08-28
> I think both virtualBox and dual boot are equal in regards to difficulty of setting them up (they are both non-trivial, in my opinion)

imho not really, partitioning part to set up nice dual boot is the most annoying step possible (especially when OEMs thoughtfully have used up all 4 primary partitions on your laptop), repartitioning takes a lot of time, there is a non-zero risk of data loss.
Nothing on the vbox side can match that. Move bunch of sliders to define size of storage, available memory etc, run iso/cd, next, next, next, ok, done. If you mess up and can't change the required settings, you don't have to repartition again, just wipe the image and start from scratch.

I have like 5 different ubuntu releases in my vbox for testing purposes, because install is braindead easy and takes 20 minutes (+10 to download iso), most of which you spend watching youtube. Partition for test installs of the latest ubuntu releases sees my activity maybe once per month.

---

### Post by coloreporter on 2012-08-28
Two things I have going for me:
-I don't need to boot Windows for anyone else that uses my computer.
-I enjoy games, but none that are too demanding of resources.  Also, Humble Bundle games from what I remember seem to usually/always have a Linux download option.

What I don't have going for me is my computer is an older laptop (~5/6 years) with 3 gigs of RAM.  I recall wanting to upgrade and finding out it can only handle 1 more gig.  The hardware seems to be the limiting factor there.

So it's having an older computer combined with wanting to use demanding Windows programs like Photoshop that makes me think I should dual boot.  Maybe however many years down the road when I have enough cash for a new computer it will be a better choice to use VirtualBox for my Windows program needs.  I like the point that using VirtualBox would force me to get used to the Ubuntu environment.

---

