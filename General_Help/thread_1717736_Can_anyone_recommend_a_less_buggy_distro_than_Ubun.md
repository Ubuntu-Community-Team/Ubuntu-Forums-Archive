---
title: "Can anyone recommend a less buggy distro than Ubuntu?"
date: 2011-03-30
forum: General Help
---

### Post by Torp3x on 2011-03-30
I installed Ubuntu 10.10 a month ago and while I'm impressed with it when it does work, I'd say I've spent 80% of my time with it fiddling with it trying to get it to work, and scouring the internet for solutions to problem after problem. Some problems don't even have solutions- mostly bugs to do with compiz and emerald- but also problems regarding external hardware (no drivers) and even internal hardware, (laptop touchpad- no driver).

Can anyone suggest a Linux distro with a stable, unbuggy desktop environment and better hardware support? Or are the bugs and driver issues in Ubuntu likely to exist across different distros? (Is Ubuntu 10.04 even a better choice perhaps?)

---

### Post by Rubi1200 on 2011-03-30
> **Torp3x said:**
> I installed Ubuntu 10.10 a month ago and while I'm impressed with it when it does work, I'd say I've spent 80% of my time with it fiddling with it trying to get it to work, and scouring the internet for solutions to problem after problem. Some problems don't even have solutions- mostly bugs to do with compiz and emerald- but also problems regarding external hardware (no drivers) and even internal hardware, (laptop touchpad- no driver).

Can anyone suggest a Linux distro with a stable, unbuggy desktop environment and better hardware support? Or are the bugs and driver issues in Ubuntu likely to exist across different distros? (Is Ubuntu 10.04 even a better choice perhaps?)
Sorry to hear this is proving to be more difficult than you anticipated.

But, here is my advice:

1. try another version such as 10.04 or one of the other desktop environments such as Xubuntu or Lubuntu

2. post the specifications for the computer so we known what you are dealing with

3. if you want stability and don't need/want the latest and greatest, consider Debian Squeeze (the latest version)

---

### Post by donkyhotay on 2011-03-30
> **Rubi1200 said:**
> if you want stability and don't need/want the latest and greatest, consider Debian Squeeze (the latest version)

Be aware you'll be trading features for stability. There is always a tradeoff, might try it but I started with debian originally for the stability and moved to ubuntu because of the lack of features and how old the software was (though it was stable as a rock).

---

### Post by lithopsian on 2011-03-30
Debian.

---

### Post by Anzan on 2011-03-30
Debian Stable (Squeeze) is a rock. Debian Testing (Wheezy) is more stable than an Ubuntu LTS (ever since 8.04).

Or you can go for one of the Linux Mint versions based on Debian Testing. Or Saline OS or Crunchbang which are both Debian Stable.

---

### Post by supershin on 2011-03-30
Check your laptop compatibility. There is a page that lists the issues with certain laptops and their solutions. You may find a fix there or some helpful advice as to another version to use.

---

### Post by lithopsian on 2011-03-30
Good idea.  Debian can be described as less buggy but it will not contain such up-to-date drivers.  New laptops and netbooks are renowned for installing bizarre bits of hardware that simply aren't properly supported yet by drivers in Linux.

---

### Post by ivanovnegro on 2011-03-30
It would not be bad to post here your hardware specs and to say what is not working in your case before to go on with other distros. Maybe you should also consider to disable Compiz as it needs a little bit more performance of your computer and if it is an older one you could have problems with it, like a slow down of the system.
For another distro and for me also less buggy like you say is PCLinuxOS, it has a great hardware support, especially for older machines even with KDE.

---

### Post by Torp3x on 2011-03-30
Ok cheers. But it's beginning to look like I can't get the best of the following:

Hardware support.
A good looking desktop environment.
Stability.

I get the impression that each distribution excels in one or two, but not all of these areas. 

Now the thing is, I'm still in the process of switching from Windows 7, and when Ubuntu works it's an awesome replacement. However, Ubuntu 10.10 does hardware support, GUI and stability to a pretty reasonable degree but it doesn't excel at any of them. As much as I do want to switch to Linux, if Windows has a great looking OS, supports all the hardware and is stable, then I can't convince myself to switch. 

The thing is, I do really want to continue using Linux. But I'm kinda being the devil's advocate to myself: should I really be using Linux if it gives me a hundred more problems that Windows? How can I then convince other people to try Linux?

And if some laptops contain hardware that isn't supported by Linux, then it makes sense to purchase machines which will be compatible with the OS. But hang on- isn't that like having to live with a Mac??

---

### Post by Rubi1200 on 2011-03-30
I think one of the first things to do is download and burn to CD a few different distros. Try them as LiveCDs first to see how they perform and if you like the look of them.

Then, do some reading to find out if that particular distro can provide what you want.

Finally, install and hopefully enjoy.

---

### Post by 3Miro on 2011-03-30
CentOS is the most stable distro that I know of (and I don't know them all). However, reading your post it is far more likely tha either you are doing something very wrong or you have hardware that is very incompatible with Linux; either way, another distro will not solve the problem.

Consider getting a machine with Linux pre-installed, then you will not have to deal with any drivers or issues of this type.

---

### Post by TBABill on 2011-03-30
> **Torp3x said:**
> Ok cheers. But it's beginning to look like I can't get the best of the following:
 
Hardware support.
A good looking desktop environment.
Stability.
 
I get the impression that each distribution excels in one or two, but not all of these areas. 
 

 
Not necessarily the case. Debian can be made to look exactly like Ubuntu. Ubuntu doesn't become itself till they customize Debian anyway....so... In terms of looks, they're pretty much the same if you add themes, change backgrounds, etc.
 
Hardware support on Debian is great. If you need a newer kernel, just download the liquorix kernel (2.6.37) and run it on Squeeze, testing, sid, whatever. And I think 2.6.38 is coming soon, but not positive on that one.
 
You won't find better stability. Testing has the occasional glitch for a day or so with single packages occasionally as older packages get replaced with new ones and it takes more than one update cycle to complete the change, but I have yet to have a machine borked by an update. I think VLC was the last package breakage I saw and that lasted all of a day or two till a single file was updated. And they post on the forums every time an update can break your system, advising users in advance who are sharp enough not to run every update as soon as it is available. Waiting a day or two after updates are available on Debian testing can keep a system problem free and you never need to reinstall.
 
Those users who claim the software is old are partly correct. It is certainly usually behind Ubuntu, and for good reason. Stability is the goal with Debian and things are tested heavily before being deemed ready for stable. Once released as stable the apps are already behind the curve compared to Ubuntu, Fedora, PCLinuxOS, Sabayon, Arch, etc. BUT, it's rock solid.
 
It's all about preference. Debian Testing really is more stable than any Ubuntu release. Debian Stable can't really even be compared to Ubuntu because they're different animals for different purposes. Ubuntu wants to be cutting edge, which leads to breakage and bugs by default (as with Fedora and others). That's the nature of the beast. New = bugs. Well tested and stable = Debian.

---

### Post by philinux on 2011-03-30
> **Torp3x said:**
> I installed Ubuntu 10.10 a month ago and while I'm impressed with it when it does work, I'd say I've spent 80% of my time with it fiddling with it trying to get it to work, and scouring the internet for solutions to problem after problem. Some problems don't even have solutions- mostly bugs to do with compiz and emerald- but also problems regarding external hardware (no drivers) and even internal hardware, (laptop touchpad- no driver).

Can anyone suggest a Linux distro with a stable, unbuggy desktop environment and better hardware support? Or are the bugs and driver issues in Ubuntu likely to exist across different distros? (Is Ubuntu 10.04 even a better choice perhaps?)

Can you let us know exactly the specs of the machine in question.

---

### Post by Torp3x on 2011-03-30
It's a Sony Vaio E. It's mid-range but more than capable. The problems I'm having aren't related to the machine's performance; I've researched the problems and found out that they are all known bugs. But some of them, bugs relating to compiz and emerald mainly,  have been known bugs since around 2008. As an aside, Windows 7 runs perfectly on the same machine, so assuming the specs have anything to do with it is like admitting that Ubuntu can't handle the jandal.

Here's a list of my main annoyances, if they can all be fixed then I'll eat my words and remove Windows completely :)

1. My touchpad doesn't work. I have to load it as a generic mouse, which leads to dysfunctional operation. It's an Alps touchpad, and there is no driver available for it currently. Low priority, unassigned issue = not getting fixed any time soon.

2. Compiz just doesn't work that well. You can sort of get some good window decorations on the go if you combine it with Emerald, but then you have to deal with annoyances such as the wrong or garbled text in the titlebar of certain browsers, Emerald and/or Compiz not starting correctly or at all on startup (both unsolved problems as far as I've been able to research). A good test would be to see if you can replicate Window's Aero Glass effect in Ubuntu. You sort of can, but it's a cheap imitation. For example, you can get a Glassy titlebar with Gaussian Blur, but you can't then add the reflection effect because a) the reflection spills over to the window shadow and b) the titlebar text is choppy and unreadable unless you enable the glow effect, but then the glow spills over to the window shadow too. The end result is something that looks like a knockoff imitation and it's pretty poor. So you're stuck with a basic looking desktop from 10 years ago.

3. I installed Gnomenu so I coud have a decent looking main menu instead of the default one which looks like a post-it note. But Gnomenu can't mount a drive. So I can't access my Windows filesystem from the main menu; I have to go to places>mount filesystem or do it via Nautilus. Not a major problem really, I'll just remove the icons for the unmountable filesystem from the menu. Oh wait- I can't. So again, it's a good looking menu that doesn't work properly, or the default unaesthetic one.

4. I had to install Amarok 6 times before it worked. Each other time there was a problem, like it wouldn't open properly and just display half a screen, or it would open but I couldn't click any items in the window- that sort of crap. There's no explanation as to why it worked (so far) the 6th time, but I'm sure it will stop working soon, like what Firefox does. Sometimes for no reason, an element of Firefox will fail, the last time it was Adblock. Just stopped working, for no reason. After reinstalls and reboots, the only fix was to purge firefox manually (locating and deleting files from their location!) then reinstalling. And for no reason- so when might it happen again? This inconsistent behaviour happens with other applications too.

5. I have a Sony Walkman because I care about music quality. Unsurprisingly, it's another device that Ubuntu has problems with. I can use it as a USB mass storage device, so I can copy music etc but I haven't found an application that will recognise it. Plugging it in even crashes Amarok. Rhythmbox is a no-go too. What other media devices will be incompatible? That sort of thing is going to be embarrassing when I try to copy music from a friend I've just tried to convert to Ubuntu when plugging in their player makes me have to reboot my system.

6. I installed Google Earth. Then I tried to open it by clicking on the icon:- nothing. No Google Earth. Now I know it's not Ubuntu's fault that installing Google Earth takes a bit more than just downloading it but couldn't I have had a warning that the version I downloaded from Google was incompatible? Couldn't it have said 'incompatible version' then not installed it instead of leading me on like that? Things like this just give the user the impression that it's a broken operating system. 

There are countless other little problems and niggles that can usually be fixed via the terminal but it would be nice if things just worked instead of me having to fiddle around for hours, punching in code and googling the issues I have in the hope of someone else having had the same problem, and someone answering them with a fix. I understand that Ubuntu is a different OS and it takes some learning and getting used to but where does it end? I still have a new problem every day after a month; is this conducive to any kind of productivity? Would you keep a car that you spent more time fixing than driving?

---

### Post by 3Miro on 2011-03-30
Emerald doesn't work well on Intel Video (Emerald is too heavy). Use gtk-windows-decorator, not as "shiny", but your hardware simply doesn't allow for more. This would be the case with any distribution.

Google Earth also has many issues. I can hardly get it to work on my ATI.

Also, Amarok shouldn't be the first choice in Ubuntu. Amarok is KDE application, which means that it will not run as well under Gnome (Ubuntu uses Gnome). Have you tried Totem, Banshee, Rhythmbox and/or Audacious.

For the other hardware problems, I don't think there is any solution other than get a new laptop. The kernel is more or less universal for all distributions and that means the drivers too. If you want a Linux laptop, you will have to take an extra step to find proper hardware or just get one with Linux pre-installed.

---

### Post by lithopsian on 2011-03-30
Half the stuff you mention works just fine for most people.  Sounds like one of your problems is that your graphics card drivers are rubbish.  Quite likely there is a better set out there and half your problems will go away.  Some of the effects you mention are pretty heavy for a Sony Vaio E, but that would very much depend on the graphics card you have.  Mostly laptops don't have high-end cards but still your problems are more likely down to the drivers than a limitation of the hardware,

Touchpads are a pain.  Sometimes you can find a driver for them, sometimes not.

No ideas about Amarok and Sony Walkman (although I know people who can connect them to Linux boxes), but there is stuff you mention failing that works fine for 99% of people.  Firefox works fine in Ubuntu, try 4.0.

You installed Gnomenu and you're complaining that Ubuntu doesn't work properly?  Try getting the operating system as supplied to work properly and then add on things which are not even provided in the repositories.  If you want decent menus, there are other routes I'd go first but then I don't know exactly what you're looking for.

Install Google Earth from the repository and it should be fine, subject to your graphics card and drivers.  Unless they are spot on then it will be rubbish, so slow it is unusable.  Open source drivers often work better for Google Earth than the proprietary ones because it likes OpenGL.

Sounds to me like it is time for a whole new install and try not to break it this time until you've confirmed whether it works or not ;)  Or just admit you don't have the spine for Linux and go back to Windows.  Ubuntu tries to do everything all flashy and graphics without you needing to know anything that is going on, but it isn't as seamless as Windows and probably never will be.

---

### Post by galacticaboy on 2011-03-30
> **Torp3x said:**
> I installed Ubuntu 10.10 a month ago and while I'm impressed with it when it does work, I'd say I've spent 80% of my time with it fiddling with it trying to get it to work, and scouring the internet for solutions to problem after problem. Some problems don't even have solutions- mostly bugs to do with compiz and emerald- but also problems regarding external hardware (no drivers) and even internal hardware, (laptop touchpad- no driver).

Can anyone suggest a Linux distro with a stable, unbuggy desktop environment and better hardware support? Or are the bugs and driver issues in Ubuntu likely to exist across different distros? (Is Ubuntu 10.04 even a better choice perhaps?)

Most distros have these problems sometimes, none of them are perfect. Then again some just suck! But Ubuntu should work, try a LTS release like 10.04. But most people are saying that or Debian. Just try some different ones to see what you like.

---

### Post by Torp3x on 2011-03-30
> **3Miro said:**
> Emerald doesn't work well on Intel Video (Emerald is too heavy). Use gtk-windows-decorator, not as "shiny", but your hardware simply doesn't allow for more. This would be the case with any distribution.

Emerald mostly runs fine, but there are problems with it that are nothing to do with my hardware, such as the spillover of the reflection, the issue of it not starting at startup every time, etc etc. Sure my graphics card is not one that a serious gamer is gonna be impressed with but it can certainly run Emerald. Emerald not starting at login 50% of the time, and Compiz/Emerald not displaying the correct title of a tab in Firefox would be a huge surprise to me if my graphics card had anything to do with it. And besides, Windows can do it seamlessly with no problem whatsoever. 

Having to change my laptop to run Linux is tantamount to saying that Linux still doesn't have adequate hardware support. I'd have to change my media player too and potentially any other electronic device I might ever need to plug in.

The argument for switching to Linux from Windows falls flat on its face if that's the only answer.

---

### Post by Torp3x on 2011-03-30
Ok please have a look at the links I provide if you think either myself or my laptop are incapable. 

> **lithopsian said:**
> Half the stuff you mention works just fine for most people.  Sounds like one of your problems is that your graphics card drivers are rubbish.  Quite likely there is a better set out there and half your problems will go away.  Some of the effects you mention are pretty heavy for a Sony Vaio E, but that would very much depend on the graphics card you have.  Mostly laptops don't have high-end cards but still your problems are more likely down to the drivers than a limitation of the hardware,
This isn't anything to do with my graphics-

[http://wiki.compiz.org/Plugins/Reflex](http://wiki.compiz.org/Plugins/Reflex)
[http://brainstorm.ubuntu.com/idea/13463/](http://brainstorm.ubuntu.com/idea/13463/)
[http://www.mail-archive.com/dev@lists.compiz-fusion.org/msg00699.html](http://www.mail-archive.com/dev@lists.compiz-fusion.org/msg00699.html)

And another quick google search of 'Emerald not starting at login' brings up a page of results. I believe there are one or two hacks to solve the problem with Emerald- for some people at least- but without guaranteed results. 

> **lithopsian said:**
> Touchpads are a pain.  Sometimes you can find a driver for them, sometimes not.

Known bug. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565543](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565543)

> **lithopsian said:**
> No ideas about Amarok and Sony Walkman (although I know people who can connect them to Linux boxes), but there is stuff you mention failing that works fine for 99% of people.  Firefox works fine in Ubuntu, try 4.0.

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/347902](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/347902)

Another google search brings up many more people with the same issues.

> **lithopsian said:**
> You installed Gnomenu and you're complaining that Ubuntu doesn't work properly?  Try getting the operating system as supplied to work properly and then add on things which are not even provided in the repositories.  If you want decent menus, there are other routes I'd go first but then I don't know exactly what you're looking for.

This is a known bug [https://bugs.launchpad.net/gnomenu/+bug/508062](https://bugs.launchpad.net/gnomenu/+bug/508062)

Again, nothing wrong with me or 'getting the OS to work properly.' Shouldn't the OS work properly as a matter of course anyway?

> **lithopsian said:**
> Install Google Earth from the repository and it should be fine, subject to your graphics card and drivers.  Unless they are spot on then it will be rubbish, so slow it is unusable.  Open source drivers often work better for Google Earth than the proprietary ones because it likes OpenGL.
My point that was downloading 'Google Earth for Linux 32 bit' from Google's site installs a package that doesn't work. But there's no warning of that, Ubuntu just goes ahead and installs a broken package. To get Google Earth to work, as usual you have to go searching online then hack away in the terminal..

[http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/)

> **lithopsian said:**
> Sounds to me like it is time for a whole new install and try not to break it this time until you've confirmed whether it works or not ;)  Or just admit you don't have the spine for Linux and go back to Windows.  Ubuntu tries to do everything all flashy and graphics without you needing to know anything that is going on, but it isn't as seamless as Windows and probably never will be.

Hopefully everything I've posted above may help you realise it's nothing to do with my laptop, or my installation of Ubuntu 10.10 which I'm beginning to think is broken from the outset. And it's not a case of having a spine, it's about wanting to use an operating system that works. If this was the first computer I'd ever used and I had the choice of using Windows or Ubuntu, it would be totally illogical of me at this point to choose Ubuntu.

But I WANT to use Ubuntu, and that's why I need these issues resolved.

---

### Post by Torp3x on 2011-03-30
Ubuntu, in the interim, has suddenly stopped playing a login sound, despite still having 'play login sound' ticked, and not having changed any of the settings. This is what I'm talking about. Buggy as hell.

Perhaps it's my sound card? Can't play a high enough bitrate?

---

### Post by stchman on 2011-03-30
> **Torp3x said:**
> I installed Ubuntu 10.10 a month ago and while I'm impressed with it when it does work, I'd say I've spent 80% of my time with it fiddling with it trying to get it to work, and scouring the internet for solutions to problem after problem. Some problems don't even have solutions- mostly bugs to do with compiz and emerald- but also problems regarding external hardware (no drivers) and even internal hardware, (laptop touchpad- no driver).

Can anyone suggest a Linux distro with a stable, unbuggy desktop environment and better hardware support? Or are the bugs and driver issues in Ubuntu likely to exist across different distros? (Is Ubuntu 10.04 even a better choice perhaps?)

Can you give us your hardware specs?

I run 10.04 on my laptop and it works very well with the new kernel 2.6.32-30.

---

### Post by Torp3x on 2011-03-30
Intel i5, 2.66 GHz, 4GB, Radeon 5470.

Fairly crap but more than enough for my basic needs (not a gamer) and enough to run Aero beautifully. 

I maintain that all of my issues have nothing to do with the graphics card or processor, being that they are mostly confirmed bugs.

---

### Post by ivanovnegro on 2011-03-30
> **Torp3x said:**
> Intel i5, 2.66 GHz, 4GB, Radeon 5470.

Fairly crap but more than enough for my basic needs (not a gamer) and enough to run Aero beautifully. 

I maintain that all of my issues have nothing to do with the graphics card or processor, being that they are mostly confirmed bugs.

Fairly crap, is that a joke?
I have lower specs and Ubuntu 10.10 runs almost perfectly, better said really perfectly, only issue I have, is Flash sometimes. Maybe its the Radeon card that are making some issues?

---

### Post by IWantFroyo on 2011-03-30
**[size=4]d.e.b.i.a.n.[/size]**[size=4]
[/size]

---

### Post by Torp3x on 2011-03-30
Like I said, there's nothing wrong with my hardware, it's Ubuntu. 

ivanovnegro did you create the overrideGPUvalidation file to fix your flash? It worked for me. Of course you shouldn't have to hack it to make it work, which is one of my main points here.

---

### Post by ivanovnegro on 2011-03-30
> **Torp3x said:**
> Like I said, there's nothing wrong with my hardware, it's Ubuntu. 

ivanovnegro did you create the overrideGPUvalidation file to fix your flash? It worked for me. Of course you shouldn't have to hack it to make it work, which is one of my main points here.

No, I did not, Im not using anymore Flash on Ubuntu, Im using it on PCLinuxOS.
I see me more using the other OS right now as I have also some concerns about the new moves of Ubuntu but that said Ubuntu is really great but I think not longer for me in the future. But I have other concerns about it as the hardware support like you.

---

### Post by Anzan on 2011-03-31
> **IWantFroyo said:**
> **[size=4]d.e.b.i.a.n.[/size]**[size=4]
[/size]

As above.

---

### Post by bodhi.zazen on 2011-03-31
> **Torp3x said:**
> I installed Ubuntu 10.10 a month ago and while I'm impressed with it when it does work, I'd say I've spent 80% of my time with it fiddling with it trying to get it to work, and scouring the internet for solutions to problem after problem. Some problems don't even have solutions- mostly bugs to do with compiz and emerald- but also problems regarding external hardware (no drivers) and even internal hardware, (laptop touchpad- no driver).

Can anyone suggest a Linux distro with a stable, unbuggy desktop environment and better hardware support? Or are the bugs and driver issues in Ubuntu likely to exist across different distros? (Is Ubuntu 10.04 even a better choice perhaps?)

Ubuntu has very decent hardware support and you may or may not have similar problems with other distros.

This is what live CD are for, although I suggest you use a flash drive rather then burning a disk.

Although many people said "Debian" , debian is more likely to give you hardware problems due to their policy on proprietary drivers.

I suggest you try Fedora, Centos, Slackware, and / or SUSE Linux.

---

### Post by jerome1232 on 2011-03-31
Your laptop, just has hardware that isn't well supported. Turns out when your hardware isn't well supported, things will work like crap. 

Many manufactures do not provide drivers at all, people who are volunteering their time will backwards engineer a driver so we can use it. When manufactures provide shoddy drivers, it's hardly the developers of Ubuntu's fault that the driver is terrible.

If sony made a terrible driver that crashed windows 7 repeatedly wouldn't you say "Wow sony is terrible" not "Wow microsoft is terrible".

No one is saying your hardware capabilities are shoddy, it's the drivers that are currently available for them that are shoddy.

I'm sorry your hardware isn't working out with Ubuntu, developers are always working hard to work with more hardware. If you do a little research beforehand and obtain supported hardware you experience is much better. Things just work out of the box with much less hassle than configuring a windows machine in my experience.

---

### Post by Don Barzini on 2011-03-31
Some of those E series laptops shipped from the factory with a Linux partition to be used only for browsing the web in a low power/battery saving mode, even though Windows 7 was the primary operating system. I don't know what version of Linux they used.

You said you were trying to get your friends to convert to Linux. Why would you do that when according to you .... you have had nothing but trouble and numerous problems since installing it?

---

### Post by msrinath80 on 2011-03-31
> **Torp3x said:**
> I installed Ubuntu 10.10 a month ago and while I'm impressed with it when it does work, I'd say I've spent 80% of my time with it fiddling with it trying to get it to work, and scouring the internet for solutions to problem after problem. Some problems don't even have solutions- mostly bugs to do with compiz and emerald- but also problems regarding external hardware (no drivers) and even internal hardware, (laptop touchpad- no driver).

Can anyone suggest a Linux distro with a stable, unbuggy desktop environment and better hardware support? Or are the bugs and driver issues in Ubuntu likely to exist across different distros? (Is Ubuntu 10.04 even a better choice perhaps?)

Debian Squeeze.

---

