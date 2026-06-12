---
title: "Why Is Linux Slow???"
date: 2009-10-12
forum: General Help
---

### Post by sumantagogoi on 2009-10-12
I am running Kubuntu 9.04 on an IBM thinkpad R50e with the following configuration:

1.6 GHz Intel Centrino CPU
1.25 GB 333 MHz  RAM
Intel 855 GMA Onboard Graphics
40 GB hard drive.

Windows XP and Kubuntu are both installed in dual-boot.

All This is far higher than the requirements for kubuntu.

I only recently switched from Windows XP to Open Source and I am very disappointed at the performance of kubuntu. 
applications take a long time to start after initiation. 
scrolling seems to be lagging in almost every application specially web browser and music player (banshee & songbird) takes almost half a second before responding to the scroll wheel.
The whole GUI feels like i am remotely controlling a computer on the other end of the earth  separeted by a dial-up connection.
When I go back to XP seeing the speed at which the applications respond to the mouse makes me feel as though i just bought a new top-range PC.

Is there some type of tune up that i can do to get better response from the computer???

---

### Post by PrePenguin on 2009-10-12
> **sumantagogoi said:**
> I am running Kubuntu 9.04 on an IBM thinkpad R50e with the following configuration:
 
1.6 GHz Intel Centrino CPU
1.25 GB 333 MHz RAM
Intel 855 GMA Onboard Graphics
40 GB hard drive.
 
Windows XP and Kubuntu are both installed in dual-boot.
 
All This is far higher than the requirements for kubuntu.
 
I only recently switched from Windows XP to Open Source and I am very disappointed at the performance of kubuntu. 
applications take a long time to start after initiation. 
scrolling seems to be lagging in almost every application specially web browser and music player (banshee & songbird) takes almost half a second before responding to the scroll wheel.
The whole GUI feels like i am remotely controlling a computer on the other end of the earth separeted by a dial-up connection.
When I go back to XP seeing the speed at which the applications respond to the mouse makes me feel as though i just bought a new top-range PC.
 
Is there some type of tune up that i can do to get better response from the computer???
 
 Honestly I like ubuntu but there is no performance notice to me than windows if a windows machine is kept properly clean and updated maybe less memory leakage.. Thats my experience anyways.

---

### Post by cwbar_1 on 2009-10-12
I suspect a graphics driver problem. Search the forums for threads containing your Intel graphics.  You should find the solution.

---

### Post by delcypher on 2009-10-12
cwbar_1 is probably right Intel Graphics cards aren't renowned for their graphical performance.

Personally I think you should not use KDE, the thing's a resource hog. You need quite a fast machine to use it acceptably (from what I've experienced).

As a first step you could turn off all the visual effects on KDE. There probably are a few performance tweaks ([http://www.tuxradar.com/content/tweak-kde-4-your-liking]("http://www.tuxradar.com/content/tweak-kde-4-your-liking")) you could apply, turning off all the unnecessary eye candy is a good start.

Personally I would go with GNOME instead of KDE (install the package gnome-desktop-environment), you'll get much better performance from that and even better from xfce.

---

### Post by OpenGuard on 2009-10-12
Get rid of that bloatware, called KDE, and install something lighter, like XFCE ( Xubuntu ).

---

### Post by PrePenguin on 2009-10-12
Yea alot of ubuntu issues are directly related to Graphic card problem or a wireless problem seems to be the majority of initial installer problems.

---

### Post by kpholmes on 2009-10-12
> **OpenGuard said:**
> Get rid of that bloatware, called KDE, and install something lighter, like XFCE ( Xubuntu ).

ya, thats what i was thinking. 

1.6ghz proc with integrated graphics running kde 4, its going to use alot more resources the xfce or even regular ubuntu. 

i had ubuntu 9.04 running on an intel atom 330 with no problem. of corse no desktop effects and it wasnt slow at all.

are you dual booting? cause if your kubuntu partition was installed after any other os, its on the outer side of the hd disc so the the it has to move farther/faster to get the same amount of data compared to the inner circle. dont know how much that makes a difference but i heard it before. might be worth mentioning.

---

### Post by andw on 2009-10-12
I went from Kubuntu to Ubuntu for the same reasons on my netbook (MSI Wind).
No problem with speed under regular Ubuntu.
I originally chose kubuntu as the interface seemed more 'windowsy' (having come from a loooong time being a windows user).
But once I set up my panels the way I like them (one at the bottom), the panel is more like an XP taskbar.

---

### Post by CatKiller on 2009-10-12
> **sumantagogoi said:**
> I am running Kubuntu 9.04 ... Intel 855 GMA Onboard Graphics


There is a known (and quite widely reported) performance regression with 9.04 and Intel graphics. I have no idea whether it was fixed in the Jaunty lifecycle, or if it's being fixed with the upcoming release of Karmic, since I don't have Intel graphics and thus haven't followed it that closely.

To OpenGuard & delcypher: KDE is no worse than Gnome, and Xubuntu isn't really that much better than Gnome. For resource-constrained systems - which, apart from the weak graphics, the OP doesn't have - LXDE is the lightweight choice.

To the OP: If there isn't a current solution (as I said, I haven't looked) and Karmic doesn't fix it (or you neither wish to wait nor run the current beta of Karmic) then give Hardy (8.04 LTS) a try. It's the current Long-Term Support release, and doesn't exhibit the performance regression that happened with Jaunty.

---

### Post by ApEkV2 on 2009-10-12
> **OpenGuard said:**
> Get rid of that bloatware, called KDE, and install something lighter, like XFCE ( Xubuntu ).

Xfce isn't all that lghtweight actually. Compared to regular Ubuntu (gnome) I'd say they are close the same.
The fastest I've used so far is Linux Mint (the Fluxbox version). It is also based off of Ubuntu.

---

### Post by chillicampari on 2009-10-12
Xfce and Gnome flavors have ended up being really similar response-wise for me using the same hardware for each. KDE has always been the slowest. Right now I'm using an unofficial Ubuntu distro/remix (CrunchBang) and liking it a lot, but (to the OP), it's not at all MS Window like.

---

### Post by kpholmes on 2009-10-12
> **ApEkV2 said:**
> Xfce isn't all that lghtweight actually. Compared to regular Ubuntu (gnome) I'd say they are close the same.
The fastest I've used so far is Linux Mint (the Fluxbox version). It is also based off of Ubuntu.

i loaded it up on my machine last week and its pretty nice, i figured id keep it around for a while. 

the only thing i miss is ubuntu one, that was really convenient

---

### Post by jcm1107 on 2009-10-12
I use Ubuntu (hardy) and it is faster than windows, I mean I can run a ton of stuff and still have the same speed as running just one window in windows so I would say you have a problem that can be fixed or it is kubuntu causing your problem. If I were you I would try and find a fix for it. If there is no fix try a different linux such as ubuntu or xfce. I use ubuntu 99.9% of the time now I never need windows it seems and I love it!!!

---

### Post by Linux&amp;Gsus on 2009-10-12
What ever other people might say, I use Kubuntu 9.04 on a similar spec Toshiba laptop just fine. Well, I have an ATI onBoard video card, that might perform better than the OPs Intel. It might be the essential difference. I don't think that the 100MHz faster processor makes it all that much faster...

Having said that. I am fully aware of what I'm running here. Besides the fact that 9.04 seems to be a bit slower (as others indicated already) but I think that it's also worth mentioning/remembering that this OS came out in April 2009. When was XP originally released, was it 2003? There is a huge gap.
You might be better off comparing the last LTS to Vista. Or wait for Win7 to be released and compare it to Kubuntu 9.10.
I have 9.10 beta w/ ext4 running on an old junkie test machine. I'm shocked how fast it boots compared to my current laptop.

@OP If you just playing around with it atm (since you just installed it recently from what I understood for the first time) and not using it for production use, you might want to try a few other options.

E.g. Ubuntu with Gnome, maybe you like it, how you know if you never used it, even though it's not looking so "Windowsy", as you put it.
Or try Kubuntu 9.10 with the newer EXT4 file system, if you really like KDE. I use KDE because I like it, not because of the "Windows look". Even though I wouldn't even agree with the "Windows look" in the first place. A panel at the bottom can hardly be called "Windowsy".

Or try a total different distro, openSuse is often recommended for KDE.

I would recommend to play around for a bit, try out some different things. Well, be careful to not mess up your Windows accidentally, have a good backup of your data, etc.
A big difference between GNU/Linux (the OpenSource world in general, I might say) and Windows is that you have options. For many people it might seem overwhelming at first. But be encouraged to look around and find what suits your needs.

Cheers,
L&G

---

### Post by vipulkelkar on 2009-10-12
I have Jaunty installed on my PC and i havent faced a speed problem as yet..
Rather i found it a bit faster...

AMD athlon 64x2   2.1
I GB DDr2
NVidia GeForce 6150

---

### Post by 98cwitr on 2009-10-12
gnome ftw...only GUI worth having imho

---

### Post by 3rdalbum on 2009-10-12
Turn off the Kwin compositing; in Ubuntu 9.04 the speed of Intel graphics has decreased from "low" to "pathetic". Or, try upgrading to 9.10 where the Intel drivers are reportedly better.

---

### Post by utnubuuser on 2009-10-12
+1 CrunchBang for sheer responsiveness.  Sidux is probably the fastest KDE

---

### Post by hoppipolla on 2009-10-13
KDE can be a little slower than Gnome or XFCE at times but it's a more ambitious desktop.

Ruling out things like incorrect graphics drivers (did you check up on this? Make sure you have the right driver for your graphics hardware :) ), I guess it's a trade-off...

Additionally, you might want to make sure you're running the latest version of KDE which is KDE 4.3.2, which is actually quite speedy even on my fairly old pc :)

---

### Post by surfed on 2009-10-13
The Intel VGA Driver in 9.04 sucks. I just upgraded my netbook to 9.10 beta and the performance boost is amazing, specially with Desktop Effects.

---

