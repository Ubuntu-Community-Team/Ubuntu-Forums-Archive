---
title: "Which version??"
date: 2010-09-21
forum: General Help
---

### Post by chris0108 on 2010-09-21
Hi there,
   I have been using ubuntu 9.04 on my laptop for about a year now. I have a few issues with it (keeps crashing etc) just wondering if i would be better with a different version of unbuntu (xubuntu, kubuntu, lubuntu etc).
   The laptop is quite old, its a samsung v20, running 512mb and an intel pentium 4 2.0ghz processor, i have looked on the various websites and cant find recommened specs for the systems. I have tried to run and install ubuntu 10.04 and it just wont run at all, crashes and just freezes up.

Can anyone give some guidence please?
Many thanks Chris

---

### Post by drpjkurian on 2010-09-21
Hi
You can use the version known as 'alternate version of Ubuntu 10.04' It will support lower version old machines. it is meant for that

---

### Post by WorMzy on 2010-09-21
With those specs lubuntu and xubuntu would certainly be more ideal. I'd expect Kubuntu to perform the same, if not worse, than normal ubuntu.

---

### Post by chris0108 on 2010-09-21
Thanks for the quick responce, i was thinking of trying lubuntu and then saw xubuntu too, just didnt know which would be best, is it best to run them from disc first to see?

Where do i find the "alternative version to ubuntu 10.04?

---

### Post by coffeecat on 2010-09-21
> **drpjkurian said:**
> Hi
 You can use the version known as 'alternate version of Ubuntu 10.04' It  will support lower version old machines. it is meant for that
 
 Point of information: if you mean the alternate CD, that is not correct.  The alternate CD for Ubuntu is a text installer and you can't run a  live session, but the installed version of Ubuntu that you get with it  and the live CD is identical. The purpose of the alternate CD is to  provide more advanced installation options than are available with the  live CD.
 
 Having said that, the OP should  be able to install Ubuntu 10.04 with  the alternate CD but they might run into the same booting problems with  the HD install as with the live CD. I think there is a more fundamental  problem here.
 
 > **chris0108 said:**
> The laptop is quite old, its a samsung v20,  running 512mb and an intel pentium 4 2.0ghz processor, i have looked on  the various websites and cant find recommened specs for the systems. I  have tried to run and install ubuntu 10.04 and it just wont run at all,  crashes and just freezes up.
 
 I don't think the 512 MB memory is the issue here. It is quite adequate  for running Ubuntu whether from the live CD or from a HD install. Don't  let anyone tell you it is inadequate; I've done it myself. So, although  you could try the lighter Xubuntu or Lubuntu, I think there's a  different problem.
 
 10.04 comes with a later kernel than 9.04 - hence newer drivers.  Unfortunately, that means that sometimes support for older hardware  disappears in the newer version. This may be what is happening here in  which case the 10.04 versions of Xubuntu and Lubuntu wouldn't help.

You could try installing with the alternate CD, but it might mean that  the HD installation won't boot up. I hope not, but be aware that this  might be so.
 
 > **chris0108 said:**
> Where do i find the "alternative version to ubuntu 10.04?

Here: [http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

---

### Post by VCoolio on 2010-09-21
Downloads [here](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download). Lubuntu is probably more lightweight than xubuntu, but most important is the applications you run (pcmanfm or thunar instead of nautilus; claws-mail instead of evolution, that kind of stuff. There is a list [here](http://wiki.archlinux.org/index.php/Lightweight_Applications) you may find useful.

---

### Post by chris0108 on 2010-09-21
Thanks guys for the replies, funny in that last one you mention about things i am running, it only ever happens when browsing the internet with google chrome, iv done all the updates and keep checking them.
The one thing that is really strange is when it does crash the mouse still works (pointer moving) but i havent tried using the menu's at the top, think ill get it running and see if its just google thats crashing it.

---

### Post by VCoolio on 2010-09-21
Hm, I was in fact just replying on the title 'what version?', as in: what version goes well with your hardware. About the crashes, we can't do much without error reports. If it's chrome, try to run it with error output to a file, so if it crashes, you can always read back. Like: ```
google-chrome > ~/chromeoutput.txt 2>&1
```. If things crash, you can reboot or relogin or whatever ( try alt+printscreen+k, or: ctrl+alt+f1, killall google-chrome, ctrl+alt+f7) and read back the output of chrome in ~/chromeoutput and see if there is something wrong.

---

### Post by perspectoff on 2010-09-21
> **WorMzy said:**
> With those specs lubuntu and xubuntu would certainly be more ideal. I'd expect Kubuntu to perform the same, if not worse, than normal ubuntu.

What are you, some sort of troll?

I have Kubuntu on all my machines, old and new. It runs as well as Ubuntu and I like it better. Xubuntu is slower than Ubuntu, nowadays (although long ago it was faster). Gnome is undergoing a major upgrade (to be more like KDE in Kubuntu), and Gnome is the desktop in Ubuntu. KDE of Kubuntu went through the upgrade a few versions ago, with some pain. I expect there to be some pain with the Gnome upgrade, too.

Besides, 512Mb RAM is plenty for all versions.

The problem in Lucid is the Plymouth splashscreen, which is incompatible with a whole lot of graphics cards, including Intel integrated graphics, ATI Radeon, NVidia, etc.

A user with an older computer has to figure out their graphics card and then hunt around on the forums for the tweak specific to their graphics card, if he/she wants to use Lucid. I have answered the questions personally dozens of times now and am tired of doing it. There must be hundreds of threads on Ubuntu forums about problems booting, and the answer is always the same: graphics.

If Lucid doesn't install (and you don't want to hunt for the graphics solution), Karmic should be used.

But every user who wants to make the decision should download and burn a LiveCD for each version he is considering and then just compare.

My CDs cost me about 3 cents each, these days, and downloading is free. For that price you can try lots of distros on LiveCDs.

Lastly, I have never seen much support for Xubuntu, and Ubuntu has no specialized wikis for Xubuntu. They merely slap a Xubuntu header on the Ubuntu wiki and pretend it is a Xubuntu wiki.

(This is a similar problem with Kubuntu, but at least there has been a Kubuntu wiki called Kubuntuguide for over 3 years).

Support wikis and forums are important when choosing a distribution.

---

### Post by DarthScape on 2010-09-21
I think Phoronix did a benchmark and came out that 8.04 is better for pentium 4 machines, and since it is still LTS, it may be better.

---

### Post by perspectoff on 2010-09-21
> **DarthScape said:**
> I think Phoronix did a benchmark and came out that 8.04 is better for pentium 4 machines, and since it is still LTS, it may be better.

Very much agree. I have two very old machines with Hardy 8.04 (and KDE 3.5, i.e. Kubuntu) and they have run like tops for several years, now. Not a single problem.

You are also right about the Alternate Install CD. It requires less memory (192 Mb, I believe) for installation, which means it can install on systems with minimum RAM capabilities (the normal installer requires 256 Mb RAM). It also installs fewer accessory programs, and has a few different installation options. but once a desktop is installed (over the network), its running requirements are the same (a desktop usually needs at least 384 Mb RAM to run).

 These are moot points for someone with 512 Mb RAM, so the Alternate installer is not needed.

---

