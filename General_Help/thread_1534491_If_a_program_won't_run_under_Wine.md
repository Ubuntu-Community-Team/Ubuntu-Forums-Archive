---
title: "If a program won't run under Wine"
date: 2010-07-19
forum: General Help
---

### Post by mcdragon on 2010-07-19
I did it. I finally got somebody else onto Ubuntu. OK, it is my mother but so far so good. I had to install MS Office :-( and then some dictionaries - all under Wine.

Now I have got stuck, there are some legal dictionaries written for Windows, released in 2002/2003 and absolutely DO NOT want to work under Wine.

I tried install under Wine or copying files from a Windows install (from another PC). Can anyone suggest what I can try?
Is my only option VirtualBox and running a virtual Win session just for one lousy program.

There are no linux alternatives as these dicts are for a niche market.

---

### Post by irv on 2010-07-19
You talk about MS Office, which apps, Word, Excel, PP, etc? I quite using MS office a long time ago and use nothing but Open Office. I can open any file from MS Office in Open Office. Why can't she just use Open Office?

---

### Post by techunit on 2010-07-19
It is also almost Identical to office 2003 and earlier... I would recommend that you use OpenOffice... It is preinstalled and very easy to use. I switch my mother and she never new the difference.

---

### Post by clhsharky on 2010-07-19
> Is my only option VirtualBox and running a virtual Win session just for one lousy program.
Maybe don't know for sure, my VirtualBox with XP starts in 1 minute, not much of a inconvenience AFAIC.

---

### Post by etdsbastar on 2010-07-19
**If a program won't run under Wine **better to use [VirtualBox]("http://www.virtualbox.org").

Fast, Reliable and the best ... Vista and XP starts within 50-55 seconds,

---

### Post by mcdragon on 2010-07-21
Thank you clhsharky. I will have to give it a try. It shouldn't be that bad then as the laptop is a brand new budget Lenovo. Do you know if you can start a program from a command that then runs virtualbox and then runs that program automatically?

@etdsbastar: Are you talking about VirtualBox?

@everyone else: please don't make this post about having to use OO.org. I know it should be used but this is my mother we are speaking about. I have files feature requests to add the functionality to OO.org and until it does I have to abide with my mother's wishes/demands and install MS Office despite the fact that I consider it a pollution of the clear linux waters. Even Google Docs has a better feature compared to OO.org - unbelievable.

---

### Post by Mark Phelps on 2010-07-21
To use Virtualbox, you have to actually INSTALL MS Windows -- which means you need to have a spare copy lying around.

Sometimes, stuff that won't run under plain Wine will run under their commercial version -- Crossover.  I believe that you can download a trial version for free from their site.

You also might try posting your questions in the Wine subforum instead of here, in the General Help forum.

---

### Post by mcdragon on 2010-07-21
> **Mark Phelps said:**
> Sometimes, stuff that won't run under plain Wine will run under their commercial version -- Crossover.  I believe that you can download a trial version for free from their site.

Didn't know about Crossover. Will give it a try. Thanks.

> **Mark Phelps said:**
> You also might try posting your questions in the Wine subforum instead of here, in the General Help forum.

Will try that as well. Thanks.

By the way, I experimented some more and as the program is in the Slovene language I tried running under the Slovene locale instead of the default en_UK and that didn't help either. I have been in correspondence with the dicts program support. They only really work in Windows :-(

---

### Post by irv on 2010-07-21
One other option you have if you have to run MS Office is to install PlayOnLinux and you can load and run MS Office under this app in Linux. I use it to run Internet Explorer 7. With this app you call install MS Office from a CD. I have never tried it, because all I use is Open Office.
[ATTACH]164163[/ATTACH]

---

### Post by etdsbastar on 2010-07-21
> **mcdragon said:**
> Thank you clhsharky. I will have to give it a try. It shouldn't be that bad then as the laptop is a brand new budget Lenovo. Do you know if you can start a program from a command that then runs virtualbox and then runs that program automatically?

@etdsbastar: Are you talking about VirtualBox?

@everyone else: please don't make this post about having to use OO.org. I know it should be used but this is my mother we are speaking about. I have files feature requests to add the functionality to OO.org and until it does I have to abide with my mother's wishes/demands and install MS Office despite the fact that I consider it a pollution of the clear linux waters. Even Google Docs has a better feature compared to OO.org - unbelievable.

Yes I am saying about virtualbox if you prefer to use it.

---

### Post by mcdragon on 2010-07-21
> **irv said:**
> One other option you have if you have to run MS Office ...

I had no problems installing and running MS Office but thanks for the feedback.

I have a problem running a 7-8 year old windows software that is a Slovene-English and English-Slovene legal dictionary by Toma&#382; Longyka (programing by [Amebis]("http://www.amebis.si/")). I don't know what it written with but I am not sure it makes a difference, or does it?

---

### Post by mcdragon on 2010-07-21
Just tried crossover and it unfortunately failed with the same error message as in Wine. :-(

---

### Post by mcdragon on 2010-07-22
Thanks to everyone who contributed. After collaborating with the [Amebis]("http://www.amebis.si/") support we did come to a solution that worked. It actually had to do with an internal install configuration that demanded the install file to be under a mapped drive.

So what definitely worked for me was to run from command line from the cd-rom directly. By the way, as my locale is en_UK and this si a Slovene program some letters were not showing up directly so I had to run it in the correct locale:
```
export LANG=sl_SI.utf8 && wine /media/ASAPS/zagon.exe
```
Be aware that your locale might be different or it might not even be installed. To find your installed locales run this in terminal:

```
ls /usr/lib/locale/
```

To make the mapping thing work properly you need to go into the Wine configuration - the Drives tab and click Autodetect, even if it looks like it is correctly mapping the cd-rom drive - IT DIDN'T. Only after doing that the install worked.

See attached screenshot from  wine config

---

