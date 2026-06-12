---
title: "why Xubuntu 12.04 LTS applications crash?"
date: 2012-05-21
forum: General Help
---

### Post by Marzata on 2012-05-21
In the new Xubuntu 12.04 LTS (i386) Xfce 4.8 so many applications crash contrary to Xubuntu 11.10 (i386). Why? How to fix this?

---

### Post by MG&amp;TL on 2012-05-21
New releases tend to be less stable. I'm afraid it's a fact.

Options:

-Go back to 11.10 and wait it out.

-Stick with it and update regularly.

Oh, and please report bugs. Otherwise it won't improve.[http://launchpad.net]("http://launchpad.net")

---

### Post by vasa1 on 2012-05-21
> **Marzata said:**
> In the new Xubuntu 12.04 LTS there are so many applications' crashes contrary to Xubuntu 11.10 where there were none. Why? How to fix this?

I'm not sure it's a general problem or there'd be more such posts.

I'm not using Xubuntu but 12.04 with Xfce 4.10 and I'm quite satisfied.

In any case, could you give more details? Have you installed any additional software or tweaked something?

---

### Post by Marzata on 2012-05-21
We have installed Xubuntu 12.04 LTS on variety of computers and VM and the app crash all the time. Even after a fresh install in VM.

---

### Post by Elfy on 2012-05-21
I'm not seeing lots of apps crashing here.

What ones are crashing?

Are you reporting them?

---

### Post by drawkcab on 2012-05-21
The only one that crashes on me regularly is Docky.  It may have to do with the fact that I've got XFCE 4.10 installed.  Maybe I should just try cairo or awn.

---

### Post by Rodney9 on 2012-05-21
I am using Xubuntu 12.04 64bit on my laptop and have not had one crash, even with a 3 day uptime.

Rodney

---

### Post by BlinkinCat on 2012-05-21
I have had about four apparent crashes, but as a result of installing XFCE version 4.10 it is my understanding that bug reports wouldn't be accepted.
In any case I decided to do a fresh install of original version. I will be keen to see if it works out to be more stable.

Cheers - :)

p.s. I have 64 bit also.

---

### Post by BlinkinCat on 2012-05-21
> **Elfy said:**
> I'm not seeing lots of apps crashing here.

What ones are crashing?

Are you reporting them?

I like your new name [COLOR=Red]Elfy[COLOR=Black] - ):P[/COLOR][/COLOR]

---

### Post by vasa1 on 2012-05-21
> **BlinkinCat said:**
> ... XFCE version 4.10 it is my **understanding** that bug reports wouldn't be accepted...

> Please note that only Xfce 4.8 is officially supported on Xubuntu 12.04. Therefore, any bug report filed with this PPA enabled is likely to get rejected, or you may be asked to reproduce the issue with Xfce 4.8. The first Xubuntu release to feature Xfce 4.10 will be Xubuntu 12.10 (Quantal Quetzal).[https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10](https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10)

---

### Post by Morbius1 on 2012-05-21
> **MG&TL said:**
> New releases tend to be less stable. I'm afraid it's a fact.
I installed Xubuntu 12.04 a day after it was released and found it to be surprisingly unstable. Multiple freezes through the day - hard reboot kind of freezes. As time passed and after more updates things have settled down. I keep getting the crash notification things pop up from time to time - I don't remember them from earlier installs so I don't know if this is a new mechanism to report them or whether this was always happening but never reported to the user.

Some folks wait until the LTS reaches the .1 release level as in 12.04.1. Sort of like the old corporate adage that you don't deploy a new version of Windows until it reaches the SP1 level.

Remember that Linux in general , at least outside of kernel development and the server space, is not regarded as a product but as an ongoing software development project.

---

### Post by Jose Catre-Vandis on 2012-05-21
I posted about crashes a couple of weeks ago

[http://ubuntuforums.org/showthread.php?t=1970355](http://ubuntuforums.org/showthread.php?t=1970355)

I don't remember seeing "apport" before in previous releases so perhaps this is something new in 12.04?

---

### Post by MG&amp;TL on 2012-05-21
> **Jose Catre-Vandis said:**
> I posted about crashes a couple of weeks ago

[http://ubuntuforums.org/showthread.php?t=1970355](http://ubuntuforums.org/showthread.php?t=1970355)

I don't remember seeing "apport" before in previous releases so perhaps this is something new in 12.04?

Nope, apport's been around a while. Maybe it's because Ubuntu's so amazing.  ;)

---

### Post by Morbius1 on 2012-05-21
> **Jose Catre-Vandis said:**
> I posted about crashes a couple of weeks ago

[http://ubuntuforums.org/showthread.php?t=1970355](http://ubuntuforums.org/showthread.php?t=1970355)

I don't remember seeing "apport" before in previous releases so perhaps this is something new in 12.04?
Read your other thread. Yes I get one of those on colord at least once a day. If I knew what it was I was doing to cause it I'd stop doing it :wink:

---

### Post by Marzata on 2012-05-21
So, we are not alone.

---

### Post by rai4shu2 on 2012-05-21
> **Marzata said:**
> So, we are not alone.

No, you probably are in good company.

Now, do us a favor and give us specifics so we know you aren't just a troll working for Apple or Microsoft or just in this for the kicks.

---

### Post by Jose Catre-Vandis on 2012-05-21
You can stop it telling you when it happens the next time, just follow the crash report process and tick the box before sending info to developers

---

### Post by 71GA on 2012-05-26
I allso experience a lot of crashes, while i had none previously with a debian distro "CrunchBang". Was a nice distro, and i swiched to Xubuntu 12.04, so i could use latest Gimp, but it was not worth it.

---

### Post by DarkShades on 2012-05-29
Yes it's crashy for some people. 

I posted a similar question thread the other day.

Either apport is just very twitchy or, some applications are having conflicts, or something else isn't quite right.  Sometimes a binary that runs at boot time will randomly show a crash.

I can say this though.  I have 32bit and 64bit systems, some with lots of RAM some much lighter.  One  32bit system is running XFCE 4.10 PPA just to see if it fixed the crashing.  It didn't.

The error reports still happen even when I also install kubuntu-desktop via apt.  So this problem is not specifically an XFCE problem.  Nor is it hardware specific.

---

### Post by rai4shu2 on 2012-05-29
> **DarkShades said:**
> Yes it's crashy for some people. 

... Nor is it hardware specific.

Oh really?

I've seen a lot of vague reports, but no one ever posts precisely what's going on with their system. I've seen system freezes, but only on ATI machines running with Catalyst. I think many of these reports are caused by AMD's lackluster support for OpenCL.

---

### Post by DarkShades on 2012-05-29
> **rai4shu2 said:**
> Oh really?

I've seen a lot of vague reports, but no one ever posts precisely what's going on with their system. I've seen system freezes, but only on ATI machines running with Catalyst. I think many of these reports are caused by AMD's lackluster support for OpenCL.

Well all my machines are running ATI graphics cards.  But some are old like a T41 Thinkpad with an ATI Mobile 7000 series.  My server has an ATI Radeon 9250.  Another has a integrated 4250, and another has a discreet 5450 because I became tired of the limitations of the Intel graphics chip integrated into the motherboard.

I don't know if OpenCL is even a factor in the older cards.

I haven't personally had system freezes.  More often either a piece of software hits a snag when it starts, or the crash indication happens when I exit the program.

One program.  MyPaint, wouldn't start and set off apport.  I went to GetDeb for the latest version on offer and the problem was solved.

XBMC runs into an error on program exit.  Otherwise it runs just fine.

---

### Post by cottfcfan on 2012-06-05
I must admit I switched back to Ubuntu because of crashes with Xubuntu 12.04lts.
Ubuntu & Kubuntu run smoothly without hitch, as did Xubuntu 11.10.
But in Xubuntu 12.04, many crashes, usually it was cairo-dock, so I switched to Docky, but same issue. I also recall other apps crashing as well. That and the fact I could never get system sounds to work sent me back to Ubuntu & Unity, which I find rock solid.

---

### Post by DarkShades on 2012-06-06
> **cottfcfan said:**
> I must admit I switched back to Ubuntu because of crashes with Xubuntu 12.04lts.
Ubuntu & Kubuntu run smoothly without hitch, as did Xubuntu 11.10.
But in Xubuntu 12.04, many crashes, usually it was cairo-dock, so I switched to Docky, but same issue. I also recall other apps crashing as well. That and the fact I could never get system sounds to work sent me back to Ubuntu & Unity, which I find rock solid.

But what is there that is so fundamentally different between those three desktop environments.  I mean I use KDE on my Xubuntu install and get the same sorts of errors so I would think it's not the DE that causing issues.

Maybe I'm wrong and there is something in Xubuntu that is tripping programs up that wouldn't be in Ubuntu or Kubuntu.  I don't know for sure since I always install Xubuntu as my base and then KDE as another DE that I run from time to time instead of XFCE.

---

### Post by Marzata on 2012-09-22
```
sudo nano /etc/default/apport

```
Change enabled from "0" to a "1" so it looks like this:

enabled=1    

To turn it off make it:

enabled=0

to turn it off at boot, and then turn it off with a ```
sudo service apport stop
```

---

### Post by ezsit on 2012-09-22
I too had crashes in tumblerd every few minutes. I isolated that problem to having thumbnails turn on in Thunar and viewing directories with media files, usually any directory containing media files. I also had crashes in colord, but not as regularly as the crashes with tumblerd.

My solution was to turn off thumbnails in the File Manager settings and I also removed all traces of tumbler with Synaptic. Removing tumbler also removed xubuntu-desktop, which was fine by me since updates will not not pull tumbler back in.

I've had zero crashes since then, my Thunar surfing is faster, and I do not have to wait for useless thumbnails to load, eating all my memory, spiking my CPU usage, and causing application crashes. Good by tumbler!

Reading up on the launchpad about tumbler, it has been buggy for years.

---

