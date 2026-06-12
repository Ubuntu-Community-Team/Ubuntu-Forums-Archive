---
title: "Firefox nightmare on 9.10"
date: 2010-04-09
forum: General Help
---

### Post by Anuovis on 2010-04-09
9.10 is my first Ubuntu, I jumped to it straight away without dual booting and found out it is not hard to handle. It recognised most of my hardware, at least all the essential pieces. As I was using a lot of open source software on Windows, the transition with applications was not that hard either. 

However, the overall experience is not nearly as smooth as in Windows. Things work but a lot of them seem to be choppy, buggy or just outright random.

Now, I can live with sound bug that gets everything muted every now and then, disappearing internet connection that needs to be reinitialized or window manager not loading the whole title bar whenever it feels like it. No, I can not replicate any of these, they just happen. Can not even file a bug report.

But here comes Firefox, my beloved browser, that I was using for the past 7 years or so on Windows. In Ubuntu, I can not view flash content properly because it flickers, the fonts are not rendered properly and it crashes almost every time a big picture needs to be displayed. I tried numerous solutions to all of these issues, read the threads, googled, read, read... neither helped. 

Sometimes Firefox just crashes. Compared to all the versions I have used in Windows, it is simply a wreck of a browser.

This is becoming a serious issue and I am considering leaving Ubuntu for the first time. I am willing to give 10.04 a chance before though. I can put up with many inconveniences and headaches this OS has brought to me. I find myself happy when something actually starts functioning after long hours of struggle, forgetting that in Windows all things just worked by default. That is OK. What is not OK is not being able to browse the web with a default Firefox.

Sorry for the long post. My two questions.

1. Was Firefox always more buggy and annoying in Ubuntu?
2. Is it reasonable to hope that 10.04 will be more stable and usable, starting with this web browser?

---

### Post by Sef on 2010-04-09
Moved to General Help.

> 1. Was Firefox always more buggy and annoying in Ubuntu?
2. Is it reasonable to hope that 10.04 will be more stable and usable,  starting with this web browser?

1) Everyone's experience is different.  Most people have not had problems with it.

2) It has worked fine for me.

If you want to install 10.04 when it comes out, I would recommend, a clean install as that will give you a better chance of resolving the problem that you are currently having.

---

### Post by Anuovis on 2010-04-09
Not sure if moving the post was a good idea since there are separate threads for each of the problem I have mentioned. Besides, 10.04 is coming out soon... 

> **Sef said:**
> Moved to General Help.
1) Everyone's experience is different.  Most people have not had problems with it.

Which I can not really comprehend. What causes these different experiences? 

I had to reinstall 9.10 after a few days of using it because managed to break something and it did not boot again. The first installation and the second had different initial problems despite the same hardware. Then I reinstalled it once again, a few months later. And got some weird combination of minor bugs from the 1st and 2nd install. 

This has made me to stop and rethink my general understanding about software. Up until Ubuntu I thought that bugs exist in the source code and should be consistent until fixed.

How come my Ubuntu can boot without any issues one time, the next time it mutes sound, the third time something else? Nothing really serious, I am just curious.

---

### Post by mikewhatever on 2010-04-09
First, thanks for sharing your experience and welcome to the forums.

> **Anuovis said:**
> 
1. Was Firefox always more buggy and annoying in Ubuntu?

No, and I suspect Firefox has nothing to do with your problem. Flash, on the other hand is much less developed for Linux, and is known to be the reason for many Firefox related problems like crashing.

> 2. Is it reasonable to hope that 10.04 will be more stable and usable, starting with this web browser?

If Flash is the issue, then no. Adobe is mainly interested in developing for Windows, with other platforms being far down their priority lists.

---

### Post by lovinglinux on 2010-04-09
> **mikewhatever said:**
> No, and I suspect Firefox has nothing to do with your problem. Flash, on the other hand is much less developed for Linux, and is known to be the reason for many Firefox related problems like crashing.

+1

Perhaps you have hardware issues.

Anyway, see [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by stalkingwolf on 2010-04-09
I have experienced all of the symptoms you describe at different times
and on different machines.  What I have found is that they can be caused
by different hardware or software  Issues.
A flaky HDD can cause these seemingly random Occurances, a degrading
install CD, Heat.  The list goes on.  Sometimes just a different software package can fix them.

I use a flash 10 .deb for flash that i downloaded from getdeb i think.
various packages from medibuntu, etc etc.

Also things like a dirty heat sink can cause random issues do to increased heat.

---

### Post by wmikes on 2010-04-09
> **Anuovis said:**
> 9.10 is my first Ubuntu, I jumped to it straight away without dual booting and found out it is not hard to handle. It recognised most of my hardware, at least all the essential pieces. As I was using a lot of open source software on Windows, the transition with applications was not that hard either. 

However, the overall experience is not nearly as smooth as in Windows. Things work but a lot of them seem to be choppy, buggy or just outright random.

Now, I can live with sound bug that gets everything muted every now and then, disappearing internet connection that needs to be reinitialized or window manager not loading the whole title bar whenever it feels like it. No, I can not replicate any of these, they just happen. Can not even file a bug report.

But here comes Firefox, my beloved browser, that I was using for the past 7 years or so on Windows. In Ubuntu, I can not view flash content properly because it flickers, the fonts are not rendered properly and it crashes almost every time a big picture needs to be displayed. I tried numerous solutions to all of these issues, read the threads, googled, read, read... neither helped. 

Sometimes Firefox just crashes. Compared to all the versions I have used in Windows, it is simply a wreck of a browser.

This is becoming a serious issue and I am considering leaving Ubuntu for the first time. I am willing to give 10.04 a chance before though. I can put up with many inconveniences and headaches this OS has brought to me. I find myself happy when something actually starts functioning after long hours of struggle, forgetting that in Windows all things just worked by default. That is OK. What is not OK is not being able to browse the web with a default Firefox.

Sorry for the long post. My two questions.

1. Was Firefox always more buggy and annoying in Ubuntu?
2. Is it reasonable to hope that 10.04 will be more stable and usable, starting with this web browser?

==========================================================

i haven't seen any of the problems you describe but all my machines are newer with fresh hardware.  are you sure the disc medium has been checked for integrity (md5 sum, slower burn, etc.)?  use the disc checker during install.  maybe go to 8.10 for now or 10.4 like you were saying.  also use "ubuntu-restricted-extras" in the repositories as it has flash, mplayer codecs, etc.  i have been using ubuntu since version 4 and it will be a windows killer someday if not already.  have fun.

:P

---

### Post by lovinglinux on 2010-04-09
> **wmikes said:**
> ==========================================================

i haven't seen any of the problems you describe but all my machines are newer with fresh hardware.  are you sure the disc medium has been checked for integrity (md5 sum, slower burn, etc.)?  use the disc checker during install.  maybe go to 8.10 for now or 10.4 like you were saying.  also use "ubuntu-restricted-extras" in the repositories as it has flash, mplayer codecs, etc.  i have been using ubuntu since version 4 and it will be a windows killer someday if not already.  have fun.

:P

I'm using since 8.04 and it kills Windows easily. Much more stable, much better features and possibility of customization, much less maintenance requirements, much better performance, much better security...the list goes on. The only complain I have is about flash, but with a dual core is not much of a problem. I kind of miss to play some games (mostly America's Army) but I can live without it.

---

### Post by kellemes on 2010-04-09
Don't let some bad experience with an individual browser (or some flash-plugin) have you leave the os. There are a gazillion very good browsers available for Linux, most of them a hole lot more stable than FF.
Some time ago I left Firefox for Google Chrome and never looked back, and it's still very much beta. Well, only my bank depends on Firefox for my online banking, but surely that will change soon..

---

### Post by bhencetotozo on 2010-04-09
> **Anuovis said:**
> 

1. Was Firefox always more buggy and annoying in Ubuntu?
2. Is it reasonable to hope that 10.04 will be more stable and usable, starting with this web browser?

... For me yes...

I have been using redhat for a Longgg time...

When i first jumped to Ubuntu, I got 7.10 Gutsy Gibbom, which I still have... I had no major issues with 7.10 ... and I really liked how easy it was to change the login screen and such ... and there was no visible bugs..

Now, on 9.10 Karmic, firefox doesnt always bug but... when im opening a Flash Website, I can see the flash's back layers, and it flashes white and i see the html's background, and its a bit annoying... I don't know why Im still using 9.10 when I have 7.10 running better but... I guess we have to, in order to help our mates, and our developers to find out bugs, so they can fix things on their next release..


Also, a big bug that I have with 9.10 is, If i allow my system to update every single update, the system will boot in a SSH screen. Which made me break a keyboard because of my temper.

Other than that, im happy with ubuntu. But i hope the next final release is better than 9.10, or atleast equal to 7.10 ....

I would defnatelly not blame any issues on my machine... It is pretty universal, and fast .


I hope we get our firefox fixed. :D

---

### Post by bhencetotozo on 2010-04-09
> **kellemes said:**
> Don't let some bad experience with an individual browser (or some flash-plugin) have you leave the os. There are a gazillion very good browsers available for Linux, most of them a hole lot more stable than FF.
Some time ago I left Firefox for Google Chrome and never looked back, and it's still very much beta. Well, only my bank depends on Firefox for my online banking, but surely that will change soon..



Yup !!!... thats why Im using opera browser instead of firefox

---

### Post by Objekt on 2010-04-09
It's the add-ons and extensions that have made me stick with Firefox for the last few years.  No other browser had such a huge selection available.  But that is changing.

Google's Chrome is pretty darned good, and might be the answer for those having problems with Firefox.  Chrome is lightning quick, that's for sure.  People are making all kinds of extensions for it: [https://chrome.google.com/extensions]("https://chrome.google.com/extensions")  Already there are Chrome versions of Adblock and Flashblock, two of my favorite Firefox extensions.

Firefox doesn't crash mysteriously for me, and I don't have any problems with Flash video, but I've been thinking of switching to Chrome lately anyway.  Firefox in Linux isn't getting any faster.  Don't know why, I just know the same version (3.6.3) is pokier under Ubuntu than in Windows XP, for no apparent reason.  No such anomaly occurs between the Windows and Linux versions of Chrome.

---

### Post by Anuovis on 2010-04-09
Thank you all for the feedback, much appreciated.

Theoretically, it might be hardware but I have never experienced anything like that while using Windows. Even in the brief period in-between two 9.10 installations. Besides, most of the problems in Firefox are not random, they are just very hard to fix.

And no, I will not change my browser. I have tried Chrome and Opera, they both lack tons of features and add-ons that make Firefox so great. An OS without this browser is simply not for me.

I will have to wait until 10.04 and see how things go from there.

---

### Post by lovinglinux on 2010-04-09
> **Objekt said:**
> Firefox in Linux isn't getting any faster. 

That's not true. Firefox has been improving performance with every new major release. The difference between Firefox 3.0 and 3.5 for instance is amazing.

---

### Post by ladypcer on 2010-04-09
I had trouble with FF crashing on a 64bit Linux distro. I found the fix here-[http://ubuntuforums.org/showthread.php?t=1263905]("http://ubuntuforums.org/showthread.php?t=1263905")
I ultimately ended up installing 32bit OS, and problems stopped. 
For me, FF has been pretty stable until that instance. 
No problems so far here in Ubuntu 10.9.

---

### Post by cbecker78 on 2010-04-09
I wonder if you have 64bit or 32 bit installed?  I originally installed the 64bit OS and was having some similar issues/irregularities.

Changing to the 32bit version after 1 day, things seem much better (though I don't know why- I never did md5-check the 64 iso).  I can now predict with stunning accuracy when something is about to crash, lockup, or act weirdly.:P (And that's pretty much just when I start something my laptop is not designed to handle)

---

### Post by Anuovis on 2010-04-10
I am using a 32 bit Ubuntu. My machine is a Dell Inspiron 6400 laptop with a 2GHz Dual core Intel and 512 RAM.
(I probably should add the hardware specs to my signature already...)

I also did the check sum before installing.

I know Ubuntu is a bit capricious with laptops but this is the default browser we are talking about. What could possibly be so wrong with my hardware that I could not use the Internet comfortably... Besides, no such issues ever emerged while using Windows on the very same machine.

Frankly, I am not feeling like looking for any of the fixes any more. That is why this thread was originally posted in *Testimonials* section. I really tried to solve them but these are not problems with some obscure piece of hardware (like my modem) or some third party software (like Skype) that are not functioning properly. And there are no easy-to-find solutions.

We are talking about a default browser on a common machine. If Firefox was running on this laptop with Windows XP for 4 years, it should run on Ubuntu. I am really not going to compile my own web browser.

Sorry, if that sounds arrogant or lazy. I was eager to learn, to be patient and adapt. I am not allergic to a command line, not looking for .exe files and not expecting perfect hardware support. But something like a web browser should be ready and usable in Ubuntu.

I know I am not alone with the flash flickering problem at least, I was subsribed to at least 3 threads for more than 6 months now. And actually, there is a solution. To change the kernel. Several people who did that said that everything went fine. So apparently, it is not entirely Adobe's fault. Besides, Opera displays things properly, it is just that the buttons on flash applications do not work there. 

Just waiting for 10.04 now...

---

