---
title: "Ubuntu 12.04 acting like windows"
date: 2012-09-26
forum: General Help
---

### Post by blackmail on 2012-09-26
Hello people, i have ubuntu 12.04, and it is acting much like windows, it is actually giving those a critical system error occured, or sometimes when i start an application, it closes for no apparent reason, and then i get an error prompt, that the program closed unexpectedly, and i have the option of relaunch or cancel... sometimes i am not sure if i have an ubuntu or a windows with ubuntu theme...

Can someone point me in the right directions on how to get this solved, mainly where to read if i have stuff as broken installations and how to get rid of them and if there is anything else that i should be doing?

---

### Post by Statia on 2012-09-26
This is normal behaviour for Ubuntu. The developers spend their time on making it look flashy instead of thoroughly testing that included software is stable and plays nice with other parts of the system. They prefer bleeding edge, latest version software over stable and well-tested versions. See for example the inclusion of an unstable development version of Abiword.
I too run into applications that crash right after fresh installation. Ironically, even the bug report screen that appears after that gives me an error, so I can't even report these errors.
You could switch to a distribution that puts the emphasis on stable and well tested software over eye-candy and living on the bleeding edge, like Debian or Slackware.

---

### Post by jerrrys on 2012-09-26
No this is not normal behaviour for Ubuntu.  I think statia has greatly exaggerated.  Or worst, has been bit by a troll.

One thing to try is open your programs in terminal and see if you get an error report when a failure occurs.

What kind of video are you running?  The wrong driver can give you grief like this.

---

### Post by Statia on 2012-09-26
> **jerrrys said:**
> No this is not normal behaviour for Ubuntu.  I think statia has greatly exaggerated.  Or worst, has been bit by a troll.


Just describing my own experiences. Have a look at my unsolved threads, which don't even describe all I've encountered so far.
The Abiword débâcle is also extensively documented here.

---

### Post by jerrrys on 2012-09-26
> **Statia said:**
> This is normal behaviour for Ubuntu.

..:confused:

---

### Post by doktorOblivion on 2012-09-26
Jerrys could be right, if you recently installed ubuntu probably did not install the latest nvidia drivers.  This can cause trouble.  Check that first.  Then check dmesg for any unusual errors or exceptions to try narrowing it down.  You also need to supply more information, kernel, etc...otherwise it will be difficult for people to help.

---

### Post by blackmail on 2012-09-27
well the drivers are the bumble bee drivers for sandy bridge... they are at the latest version. also the updates cannot be done, i have had to force the updates to be installed using the dist-upgrade command with apt-get.

the optirun gives me also errors, but these problems where before... i know i should not be trolling but honestly i think that ubuntu just went down the hill from 11.04, when they forcefully implemented the unity desktop, it was when i realized that the option for choice was greatly undermined. They have a wondeful interface, if you tear out the unity part, which is what i did. but yeah this is still linux so we are supposed to get our hands dirty and report stuff and try to fix it, if it gets broken, with the community, by the community, for the community 
:lolflag:

so then the output of uname -a is:
```
blackmail@diaryofamadman:~$ uname -a
Linux diaryofamadman 3.2.0-29-generic-pae #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012 i686 i686 i386 GNU/Linux

```

also there was no bad news in todays issue of dmesg magazine for me :p

regarding nVidia drivers the part that is annoying is with the optirun part which even for testing purposes when i run the glxspheres it gives an error like this:

```
[101971.407068] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver

[101971.407109] [ERROR]Aborting because fallback start is disabled.

```

if you need any more info just let me know

---

### Post by blackmail on 2012-09-27
i have just reinstalled bumblebee, and i know for a fact that when i restart it won't work again... this is so friggin frustrating.

---

### Post by HiImTye on 2012-09-27
> **blackmail said:**
> i have just reinstalled bumblebee, and i know for a fact that when i restart it won't work again... this is so friggin frustrating.
get mad at nVidia, whose drivers are proprietary, not at Ubuntu, who are giving you a product for free.

---

### Post by Statia on 2012-09-27
> **jerrrys said:**
> No this is not normal behaviour for Ubuntu.  I think statia has greatly exaggerated. 

As if to prove my point, when I came back to my computer after a few hours, there were 21 dialog boxes waiting for me to inform me of KWin crashes.

Now let me clarify myself further, this is not a Ubuntu-only rant, nor is it an attack against Ubuntu. It holds true for other distributions and OSS projects as well. For instance, Kubuntu never should have included the early KDE 4.x releases in a distribution. They should have stuck with KDE 3 until KDE 4 was stable and mature enough for everyday use. Now all they achieved was to scare people away from KDE, so now that KDE is fast, stable, userfriendly and pretty again, there are still lots of people who won't go near it.
It also holds true for more open source projects and software. A lot of developers prefer adding more features over fixing bugs. (And don't even start about producing documentation)

See more for yourself on Ingo Molnar's page:

[https://plus.google.com/109922199462633401279/posts/HgdeFDfRzNe]("https://plus.google.com/109922199462633401279/posts/HgdeFDfRzNe")

Or follow the recent Torvalds / de Icaza debate.

---

### Post by sandyd on 2012-09-27
> **blackmail said:**
> well the drivers are the bumble bee drivers for sandy bridge... they are at the latest version. also the updates cannot be done, i have had to force the updates to be installed using the dist-upgrade command with apt-get.

the optirun gives me also errors, but these problems where before... i know i should not be trolling but honestly i think that ubuntu just went down the hill from 11.04, when they forcefully implemented the unity desktop, it was when i realized that the option for choice was greatly undermined. They have a wondeful interface, if you tear out the unity part, which is what i did. but yeah this is still linux so we are supposed to get our hands dirty and report stuff and try to fix it, if it gets broken, with the community, by the community, for the community 
:lolflag:

so then the output of uname -a is:
```
blackmail@diaryofamadman:~$ uname -a
Linux diaryofamadman 3.2.0-29-generic-pae #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012 i686 i686 i386 GNU/Linux

```

also there was no bad news in todays issue of dmesg magazine for me :p

regarding nVidia drivers the part that is annoying is with the optirun part which even for testing purposes when i run the glxspheres it gives an error like this:

```
[101971.407068] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver

[101971.407109] [ERROR]Aborting because fallback start is disabled.

```

if you need any more info just let me know
Nvidia Optimus chipsets have always been a problem with Ubuntu, even with Bumblebee and Ironhide. Its sort of a hit-and-miss problem at the moment, not only with Ubuntu, but any other distro.

Furthermore, Ubuntu does not develop the Bumblebee or Ironhide drivers.

---

### Post by Statia on 2012-09-27
Well, if you are running experimental code (Bumblebee) you can expect it to crash.
This is just a case of hardware support on Linux lagging behind because of lack of cooperation by hardware vendors.
(Lack of QA/QC by distributions is another, unrelated topic)

I see you are still running 3.2.0.29; the upgrade-fairy has already taken me to 3.2.0.31. You could try if a kernel upgrade might help.

---

### Post by QIII on 2012-09-27
Never mind

---

### Post by blackmail on 2012-10-02
I am not angry at ubuntu for the part where the drivers and Bumblebee fails, i am mad for the other ubuntu-isms like the fact that it crashes many times and that they are investing ever more time in interface design and less time in the testing so that it may be stable and good...

---

