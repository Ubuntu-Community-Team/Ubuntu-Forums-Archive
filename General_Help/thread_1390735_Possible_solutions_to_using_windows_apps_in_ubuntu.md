---
title: "Possible solutions to using windows apps in ubuntu OS"
date: 2010-01-26
forum: General Help
---

### Post by qarano on 2010-01-26
You are probably asked this all the time but what are some of the better solutions to runnign windows apps in an ubuntu OS? I am getting a new (to me) computer with xp pre-installed, and I want to put linux on it. I want linux to be able to customize my machine and run some of the cooler linux apps, but I also want to be able to run windows programs (not anything specific, but programs for windows in general, mostly exe)

I have looked at virtual machine solutions such as virtualbox and vmware, and while they could work for my purposes, I was hoping for a more streamlined solution. I want to be able to click on an exe file while in linux and have it run it ideally (I know it won't be that simple, but as close as possible would be great)

thankyou for your time.

---

### Post by kako13 on 2010-01-26
> **qarano said:**
> You are probably asked this all the time but what are some of the better solutions to runnign windows apps in an ubuntu OS? I am getting a new (to me) computer with xp pre-installed, and I want to put linux on it. I want linux to be able to customize my machine and run some of the cooler linux apps, but I also want to be able to run windows programs (not anything specific, but programs for windows in general, mostly exe)

I have looked at virtual machine solutions such as virtualbox and vmware, and while they could work for my purposes, I was hoping for a more streamlined solution. I want to be able to click on an exe file while in linux and have it run it ideally (I know it won't be that simple, but as close as possible would be great)

thankyou for your time.

You can use Wine and CrossOver.  With CrossOver the experience for me has been very good especially when installing MS Office 2007.  But neither Wine or CrossOver can run all the Windows apps.

In my case, if I like an application that runs on Windows I always try to use Wine or CrossOver.  As a last resource, I try to find a good replacement on Linux (not always exist :icon_frown:).

---

### Post by t4thfavor on 2010-01-26
wine. It's that simple, almost.

Lots of apps don't work in wine, so YMMV.

Also check to see if there are Linux alternatives to those apps as they usually run better in their native environment than their windows export bretheren.

---

### Post by hemimaniac on 2010-01-26
Depending on which windows app you are trying to run, I would look at [wine-doors]("http://wddb.wine-doors.org/downloads") , unlike wine ( not faulting, just believe sometimes there is an easier way ) they carry their own repos, and the list actually grows all the time. I have used it to run .exe files that normally error in wine (alone). its just an added comparability.

---

### Post by qarano on 2010-01-26
I was looking for somethign that would allow me to run privately developed hacking tools, the kind of program that isn't in wide enough use to be specifically supported by wine and the like.


I guess I'll just have to switch over to use those. thanks anyway. Also, wine should help with more common windows apps, so there's that.

---

### Post by t4thfavor on 2010-01-26
It's possible that if they are standard C++, and use only basic windows calls they will still work.

If they used something like .net, or vb, then I believe you would be sunk in linux for the most part.

---

### Post by El Zoido on 2010-01-26
Hacker tools? :D

I hope you know what you are doing. Or not, depends on what you intend to do... ;)

Anyway, there's always the possibility to go dual-boot and install both Win and Linux if you want to be sure all windows software is going to work.

---

### Post by t4thfavor on 2010-01-26
Like you know l337 and the like What he meant was H4xx0r2!!

---

### Post by mkvnmtr on 2010-01-26
Virtual Box. It is easy.

---

### Post by hhlp on 2010-01-26
these are and usefull information :

[https://help.ubuntu.com/community/Wine]("https://help.ubuntu.com/community/Wine")

[http://appdb.winehq.org]("http://appdb.winehq.org")

---

### Post by snowpine on 2010-01-26
> **qarano said:**
> I am getting a new (to me) computer with xp pre-installed

That's your answer right there. XP will run your Windows apps flawlessly with 100% compatibility. You can dual boot with Ubuntu, or run Ubuntu in VirtualBox.

---

### Post by qarano on 2010-01-26
> **snowpine said:**
> That's your answer right there. XP will run your Windows apps flawlessly with 100% compatibility. You can dual boot with Ubuntu, or run Ubuntu in VirtualBox.
(noob question) what is dual booting? how does it work?

---

### Post by hhlp on 2010-01-26
this is dual-botting

[http://en.wikipedia.org/wiki/Multi_boot]("http://en.wikipedia.org/wiki/Multi_boot")

---

### Post by snowpine on 2010-01-26
> **qarano said:**
> (noob question) what is dual booting? how does it work?

Short answer: The Ubuntu installer has an option to resize your windows partition and install Ubuntu in the freed space. If you do this correctly, you'll be able to choose between Ubuntu or Windows each time you boot up, depending on your needs that day.

Long answer: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

