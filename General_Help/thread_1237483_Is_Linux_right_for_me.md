---
title: "Is Linux right for me?"
date: 2009-08-11
forum: General Help
---

### Post by HollyD on 2009-08-11
Hi!

I've been interested in Linux for years, and have several friends who love it.  I've tried switching over several times but have always run into some sort of problem and ended up switching back to XP.  After upgrading computers we now have two running Vista though, and I've been very unimpressed with it.  I'd like to switch to Ubuntu (using Wubi), however, I'm wondering if it's practical to switch because I really need it to work with:

dual monitors (two Acer LCD X223W monitors, the computer has two NVIDIA GeForce 9800 GT video cards)

Wacom Bamboo Fun graphic tablet

Photoshop CS4 and Photoshop Elements 6.0 (I do a lot of graphic and web design for work and spent hundreds on the software so obviously want to keep it.  Yes, I've used GIMP for years but can't switch back for work.)

World of Warcraft (my husband bought this computer for gaming and now I've kind of taken it over for work, but if we have to reboot and go back and forth from Linux to Windows for gaming that's not practical.  

Obviously since I already have the hardware I really need them to work well, but other than those programs I'm perfectly fine finding an alternative.  I already use Firefox and Open Office on Windows.  I've read that there are ways to install the software but I wasn't sure how well they'd run, can someone tell me about their experience running them on Linux?  Is it practical for me to switch to Linux with these issues or do I just need to stick with Windows?

Thanks in advance for your help!

---

### Post by snowpine on 2009-08-11
Hi Holly D, 

I recommend you burn an Ubuntu Live CD so you can test it on your system with absolutely no commitment or changes to your computer:

[https://help.ubuntu.com/community/GettingUbuntu](https://help.ubuntu.com/community/GettingUbuntu)

I predict that you will like a lot of things about Ubuntu, but that you'll want to "dual boot" with Windows for Adobe CS, Photoshop, and WoW. Windows applications will always run better in Windows than Linux, by their very nature.

---

### Post by jeffersonbenson on 2009-08-11
First off, thank you for looking into the world of linux. I myself am quite new to the whole thing and don't have all the answers. I can tell you though that I have both a desktop that runs windows, and a laptop which is completely ubuntu. 

Growing up a windows geek my life, I found that there wasn't a whole lot of freedom. After switching to linux, there is so much that I can do and make my desktop mine. 

Now that the testimony part is over, on to your questions. Wacom has made great tablets that run just fine with linux. I have a sister who just got one as a Christmas present. One afternoon I decided to plug it in to my laptop and see if it would work. With no problem the mouse started to react to the pen without the need for drivers and other such problems. It just worked.

For some of your more windows proprietary applications, I would consider looking to wine [[link]]("http://www.winehq.org/"). People across the board have had great results with world of warcraft [[link]]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=17421") and photoshop [[http://appdb.winehq.org/appview.php?appId=17]](http://appdb.winehq.org/appview.php?appId=17]). 

Good luck with your research and I hope that this helps.

---

### Post by jocko on 2009-08-11
If you really need photoshop for work, I would say you should keep windows. It is possible to install some versions of photoshop in wine (a windows compatibility layer), but cs4 does not work yet according to [http://appdb.winehq.org/appview.php?appId=17](http://appdb.winehq.org/appview.php?appId=17).

It is also possible to install windows within a virtual machine to run the programs, but the performance will not be as good as running them directly in a normal windows install. But if you have lots of memory and a fast processor it may still work well enough...

I'm sure there should be no problems setting up dual displays using nvidia-settings (once you have installed the nvidia graphics driver).

But, if you have some hard drive space, why not install ubuntu and dual boot for a while to see what you can do? If you use wubi you can even do it without changing the partitioning of your hard drive, and if you decide you don't want to keep ubuntu you can just uninstall it from within windows.

---

### Post by ubudog on 2009-08-11
> **snowpine said:**
> Hi Holly D, 

I recommend you burn an Ubuntu Live CD so you can test it on your system with absolutely no commitment or changes to your computer:

[https://help.ubuntu.com/community/GettingUbuntu](https://help.ubuntu.com/community/GettingUbuntu)

I predict that you will like a lot of things about Ubuntu, but that you'll want to "dual boot" with Windows for Adobe CS, Photoshop, and WoW. Windows applications will always run better in Windows than Linux, by their very nature.

Yes, that would be the best option by far, but when I used the live cd, it didn't pick up my wireless, but in the main install, it did.  You may have to enable some stuff in Restricted Drivers.  Hope that helps! :P

---

### Post by furuno on 2009-08-11
Hello to you to!

First, I guess it's OK for you to switch to Ubuntu. Since looks like all of your hardware will be supported properly without many hassle. And it seems that Photoshop CS4 runs quite well under Wine, so you should be able to do all of your work too. However, be prepare, application launch time with Wine can be took quite long since Wine will try to ...er... emulates Windows (Wine = Wine is not an emulator :( ).

Firefox and OpenOffice is already pre-installed in Ubuntu. All you need is to install your graphic card driver and wine to get up and running fine. All of those installation should be very easy and can be done from the Add/Remove programs feature.

Some people says that disk performance is slower if you install Ubuntu under Wubi. Well, I'm also installing my Ubuntu under Wubi and it seems that I don't have a noticeable performance penalty for that. All things runs smoothly in my Ubuntu installation.

For maximum gaming experience however, I still think that Windows is much better. I'm also switch to Windows only when I want to do some intense gaming (I like FPS and combat flight sims). However much lighter games (like some of my online games and visual novels) runs very well with quite a good performance.

Indeed, when you're switching to another operating system there will be some kind of learning curve, altough it should be very easy to switch from Windows and Ubuntu. The most important thing you'll need to learn when switching from Windows to Linux is I think to learn about the differences about how Linux handles files and drives.

My experience using Ubuntu as my primary work operating system is very positive. It installs very quickly and easy (under Wubi). All I need to get it up and running for all of my needs (I'm a Java application developer) is simply installing ATI graphic card driver, Sun Java SDK and NetBeans IDE. It's done very easily with no hassle.

Sometime I'd also play with Compiz and customize my desktop with a lot of eyecandy. Compiz is great because I have controls about everything. For example, I think that animations when opening something is very counter-productive (you need to wait until the animation complete), and I can disable the opening animation completely, but still having some nice closing animation.

The only thing that bothers me in Ubuntu is that you cannot completely hide the taskbar. It'll take up a single pixel line (which is slighly annoying) at the very least :(.

Well, I hope this helps...

---

### Post by martinbaselier on 2009-08-11
I would recommend a full install and not wubi. Ubuntu will automatically create it's own partition. It's always possible to remove it later, if you don't like ubuntu. It will just work better in it's native form. 

WOW runs fine on wine, from the reports I heard. (no personal experience). Photoshop CS3 does too. Though it works fine, under windows it will still work better, 

If you take in consideration what you want to do, I guess you'd be better off to stick to windows. If you've got a spare computer, you could use it for testing. And you can always try with dualboot. To see if and how well a program runs under wine, check:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

edit: to be exact, wine is an implementation of the windows api (application programming interface), so it's an open source implementation of all the standard functions in windows (create a window, keyboard/mouse input, directx, etc )

---

### Post by ubudog on 2009-08-11
> **martinbaselier said:**
> I would recommend a full install and not wubi. Ubuntu will automatically create it's own partition. It's always possible to remove it later, if you don't like ubuntu. It will just work better in it's native form. 

WOW runs fine on wine, from the reports I heard. (no personal experience). Photoshop CS3 does too. Though it works fine, under windows it will still work better, 

If you take in consideration what you want to do, I guess you'd be better off to stick to windows. If you've got a spare computer, you could use it for testing. And you can always try with dualboot. To see if and how well a program runs under wine, check:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

edit: to be exact, wine is an implementation of the windows api (application programming interface), so it's an open source implementation of all the standard functions in windows (create a window, keyboard/mouse input, directx, etc )

Yes, that would also be a good option.

---

### Post by scouser73 on 2009-08-11
Hi Holly D, I have Googled some results for using your present applications on Ubuntu using WINE **[Wine Is Not an Emulator]**.

1 - [[COLOR="Red"]**Adobe Photoshop CS4 On Ubuntu**[/COLOR]]("http://www.sucka.net/2009/08/installing-adobe-cs4-in-wine/comment-page-1/")

2 - [[COLOR="Red"]**Using Dual Monitors On Ubuntu**[/COLOR]]("http://www.ubuntugeek.com/dual-monitors-with-nvidia.html")

3 - [[COLOR="Red"]**Wacom Bamboo Fun Graphics Tablet On Ubuntu**[/COLOR]]("http://collegegeek.org/2009/05/13/wacom-bamboo-in-ubuntu-904/"). This article mentions that using the Wacom Tablet with Ubuntu is easy.

4 - [[COLOR="Red"]**World Of Warcraft On Ubuntu**[/COLOR]]("https://help.ubuntu.com/community/WorldofWarcraft")


All the best.

---

### Post by khelben1979 on 2009-08-11
If you're interested in Linux, I would suggest you go for a dual boot solution. Installing Linux on a second harddrive would be to recommend, in my opinion.

---

