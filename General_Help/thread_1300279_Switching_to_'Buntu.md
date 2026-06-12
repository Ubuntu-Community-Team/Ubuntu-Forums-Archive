---
title: "Switching to 'Buntu"
date: 2009-10-24
forum: General Help
---

### Post by bds28338 on 2009-10-24
hey there, I'm just recently decided to make the jump to Linux. I'm cleaning up my computer right now and transferring everything to my ExternalHD. I had a few questions and thoughts before I go any further.

My computer is a Compaq Presario F712NR, full specs are right [HERE]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01168646&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&lang=en&product=3561974"), only change I've made is thrown in an extra gig of RAM.

My first question would be, which edition of 'Buntu should I use? I would prefer most graphic intensive, feature intensive, and polished edition, but I know I also need to keep in mind I don't have the greatest laptop in the world.

Are there any known compatibility problems with my computer? I've read that wireless networking with my Broadcom card can be a hassle.

32-bit or 64-bit? I believe my computer is x86 but I'll just ask anyway.

I also took a look on the Ubuntu Studio website, what exactly is that? Is it just Ubuntu with a bunch of art stuff added? Will it run the same way Ubuntu does?

Lastly, can I get a driver from my video card in order to get games to play well?














EDIT NEW QUESTIONS

what bling options does Kubuntu have?

what logic should I have behind installing 64-bit? will it boot faster or any programs run faster? I haven't read up on it much but I believe the program actually has to be written specifically to take advantage of 64-bit. So unless I find myself using programs with a 64-bit compatibility mode, they won't actually preform any better?

---

### Post by oboedad55 on 2009-10-24
Go with normal Ubuntu, either 9.04 or if you're feeling brave, 9.10. Since it's your first install I'd go with 9.04 as it is stable. Smart move, backing up. Enjoy the experience. BTW, your hardware looks good to go.

---

### Post by iMisspell on 2009-10-24
Not sure if you know or not, but atleast with Ubuntu (which is what ive changed over to from windows) you can download the iso, burn and when it loads you can run the OS off the cd to get a feel for things, im sure the other flavors will do the same.

Coming form windows myself (after about 10 years) i really really like Ubuntu from a programers point of view... The OS's "desktop/gui" will do everything for you or if you want to script and use command line stuff that is there as well.

And... this forum is has alot of great threads if you run into a jam...

Personaly i would downlaod and run a few different ones off the cd to find what you want/like.

_

---

### Post by howefield on 2009-10-24
> **bds28338 said:**
> My first question would be, which edition of 'Buntu should I use? I would prefer most graphic intensive, feature intensive, and polished edition..

Sounds like Kubuntu for the bling, but for feature intensive and polish, my vote goes to Ubuntu with a few kde apps thrown in. But beauty is in the eye of the beholder, so your mileage may and probably will, vary :)

> Are there any known compatibility problems with my computer? I've read that wireless networking with my Broadcom card can be a hassle.

A lot of progress has been made with wireless recently and you have a strong chance of success. My laptop has a broadcom which needs a wired connection to get the hardware drivers downloaded, but very easy.

> 32-bit or 64-bit? I believe my computer is x86 but I'll just ask anyway.

Your machine is capable of 64 bit but you may not see any significant difference between it and 32 bit, depending on what you are using the machine for,  but imo if the hardware is capable then 64 bit is the way to go.

> I also took a look on the Ubuntu Studio website, what exactly is that? Is it just Ubuntu with a bunch of art stuff added? Will it run the same way Ubuntu does?

Didn't you say you had been to the Ubuntu Studio website, it is pretty obvious from the homepage what it is about.

> Lastly, can I get a driver from my video card in order to get games to play well?

Nvidia is well supported in Ubuntu, but it depends on what you mean by playing games...

---

### Post by ad_267 on 2009-10-24
Get the 64 bit version to take advantage of your 64 bit processor.

Ubuntu studio is Ubuntu with some audio and video production software installed by default, as well as a real-time kernel which is better for audio applications.

For your video driver, go to System - Administration - Hardware drivers after you've installed and select the recommended drivers.

---

### Post by Amstell on 2009-10-24
> My first question would be, which edition of 'Buntu should I use?

Check this out:

Which *buntu to pick?
[http://psychocats.net/ubuntu/whichbuntu](http://psychocats.net/ubuntu/whichbuntu)

> 
32-bit or 64-bit? I believe my computer is x86 but I'll just ask anyway.

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by 3rdalbum on 2009-10-24
Regular Ubuntu, either 32-bit or 64-bit. There aren't really any reasons not to get the 64-bit edition.

The graphics card is really the weak spot of the whole system - the drivers for it are old and you might possibly need to manually edit your /etc/X11/xorg.conf file to get the correct resolutions (like we all had to do in 2005).

---

### Post by bds28338 on 2009-10-24
what bling options does Kubuntu have?

what logic should I have behind installing 64-bit? will it boot faster or any programs run faster? I haven't read up on it much but I believe the program actually has to be written specifically to take advantage of 64-bit. So unless I find myself using programs with a 64-bit compatibility mode, they won't actually preform any better?

---

### Post by ad_267 on 2009-10-24
Kubuntu doesn't have any extra bling as such. It just uses a different desktop environment, KDE, rather than Gnome which is the default in Ubuntu. Have a look at some screenshots to see the difference. 

KDE: [http://en.wikipedia.org/wiki/KDE](http://en.wikipedia.org/wiki/KDE)
Gnome: [http://en.wikipedia.org/wiki/GNOME](http://en.wikipedia.org/wiki/GNOME)

As for 64 bit, if you use 64 bit Ubuntu all the applications you install will be compiled for 64 bit, so most should be able to take advantage of it.

You're not losing anything by using 64 bit, so you might as well use it.

---

### Post by undecim on 2009-10-25
Welcome to Ubuntu!

> **bds28338 said:**
> what bling options does Kubuntu have?

what logic should I have behind installing 64-bit? will it boot faster or any programs run faster? I haven't read up on it much but I believe the program actually has to be written specifically to take advantage of 64-bit. So unless I find myself using programs with a 64-bit compatibility mode, they won't actually preform any better?

You can run Compiz (Gnome's "bling") in Kubuntu, but you may find some quirks with it (mostly just little annoyances involving workspaces.

Although I must say that KDE 4.3 (used in Kubuntu) looks VERY nice, even without all those flashy desktop effects.

As far as 64-bit goes, most of your applications will still be run as programmde for 32-bit, but things such as multimedia will run faster, as they will be designed to make the most of whatever hardware they are installed on. Some other CPU-intensive apps may also be designed to take advantage of 64-bit if the option is available.

All-in-all, you have nothing to lose with 64-bit. There were some compatability issues a few years back, but I run it myself and haven't run into a problem yet.

Also, a note on different flavors of Ubuntu: Any flavor of ubuntu is just the same base system with different software packages installed. You can even get the experience of two or more flavors of Ubuntu in one by installing the packages that come with that flavor.

And remember: The people on these forums are very friendly and helpful, so if you are ever in need of help, don't hesitate to post a question.

---

### Post by shae on 2009-10-25
In terms of 32-bit vs. 64-bit, I think it is still too early to suggest new people to use 64-bit.  Some may accuse me of spreading fud, but I think 32-bit just works and at this point, 64-bit requires more tinkering.

I would also suggest that you use Ubuntu 9.10, which will be released in 5 days.  That will save you the mess of upgrading.  If you are feeling adventurous, you can try the RC.  It does not have any major issues from my experimentation and will upgrade right into the newest version, pending any major issues.  

I am strongly suggesting you use Ubuntu, the GNOME variant because most tutorials are written with GNOME in mind.  Thus, you will have an easier time.

Both GNOME and KDE offer desktop effects, but right now GNOME is more stable and feature complete whereas KDE just released a major overhaul and is still working out some kinks.  I personally found even KDE 4.3+ was still unacceptably unfinished.

If you are unsure, grab both live CDs and see what you think.  This does depend on your connection speed though.

Good luck and I will happily help out any other way I can.
Shae\\:D/

---

