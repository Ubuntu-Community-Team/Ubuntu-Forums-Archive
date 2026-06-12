---
title: "Root/Android"
date: 2010-04-01
forum: General Help
---

### Post by fjsimpkins on 2010-04-01
Hi All...Ive search so many forums and browsed tons of articles but im still not finding it. Ive got the motorola cliq and want to root it and put on a custom rom. I just cant figure it out. Ive only found articles about doing it in windows. Any ideas? Thanks 

Jim

---

### Post by KayakJim on 2010-04-01
> **fjsimpkins said:**
> Hi All...Ive search so many forums and browsed tons of articles but im still not finding it. Ive got the motorola cliq and want to root it and put on a custom rom. I just cant figure it out. Ive only found articles about doing it in windows. Any ideas? Thanks 

Jim

Why would you post this question on an forum for Ubuntu support?

---

### Post by fjsimpkins on 2010-04-02
> **KayakJim said:**
> Why would you post this question on an forum for Ubuntu support?

Because I'm using ubuntu. So I'm looking for help with it.

---

### Post by rykel on 2011-01-16
Hi, I am also hoping to root my Sony Ericsson X10 Mini Pro (Android) from Ubuntu too, instead of Windows. So far, not too many sites on Google pertaining to this issue. Maybe you can help? Thanks, Rykel

---

### Post by Jimbotronics on 2011-01-19
> **KayakJim said:**
> Why would you post this question on an forum for Ubuntu support?

According to a number Android professional developers, Ubuntu is more popular than Windows for Android app development.

The fellow who originated this thread to root his Android handheld is looking for the file

[INDENT][COLOR="Navy"]z4root.1.3.0.apk[/COLOR][/INDENT]

which is available in the Android Market or at this address:

     [http://forum.xda-developers.com/showthread.php?t=833953](http://forum.xda-developers.com/showthread.php?t=833953)

(It's a little hard to find the download link, which is in small type not quite halfway down the page.)

Although the instruction are given for Windows users, the operating system is really irrelevant.  It is just being used to download the file and transfer it to the Android device.  The instructions are not much different for Windows or Ubuntu.  In fact, the process is easier for us.  After all, both Android and Ubuntu are linux systems.  Hope this helps.

---

### Post by piquat on 2011-01-20
Just FYI, they removed it from the market so you have to find it online.

---

### Post by Jimbotronics on 2011-01-20
> **piquat said:**
> Just FYI, they removed it from the market so you have to find it online.

Thanks for the update.

It's kind of depressing.

Easy to understand how Google's legal eagles would be less than excited about rooting software, but this one was so nicely done, and reversible no less(!), you'd think they could have thrown caution to the wind for once.  Obviously not.

---

### Post by piquat on 2011-01-21
Sorry, I didn't mean to imply that you can't still get it or that it doesn't work, you can and it does, you just have to find it elsewhere.

No big deal to me really, only thing the market does is a little vetting.  The sda link is the source for it anyway, no need for googles vetting when you get it straight from the developer, more or less.

---

### Post by rykel on 2011-01-30
Hi, I am interested to root my Sony Ericsson X10 Mini Pro with "One-Click" through Ubuntu as well but here are my questions:

[LIST=1]
[*]Which root file should I download, and how do I know that it is the "latest" version of itself?
[*]HOW do I actually use the file to root the phone using Ubuntu?
[*]Will the file BACKUP my current Android system BEFORE rooting so that I can go back to a "factory state" when I need to reverse my decision to root?
[*]Any other issues to take note of before/during/after rooting?
[/LIST]
Thank you for your assistance and kind words!

---

### Post by rykel on 2011-02-02
Bump.

---

### Post by blueridgedog on 2011-02-02
This is a better forum for these questions:

[http://forum.xda-developers.com/](http://forum.xda-developers.com/)

---

### Post by DouglasAWh on 2011-02-10
> **blueridgedog said:**
> This is a better forum for these questions:

[http://forum.xda-developers.com/](http://forum.xda-developers.com/)

I don't mean to hijack the thread, but there is a lot of Windows-related info on that site.  

I've been looking for info for hours now and unable to figure out how to back up my phone.  Installing CyanogenMod looks pretty easy, but I don't want to do it without a backup first and I need root install Titanium.  

I wanted to use dd, but I can't figure out what the phone is called.

I decided to give some XP instructions a whirl, but I'm waiting for all the SDK stuff to install...I somehow managed to tell the GUI to download several versions...telling it what I wanted was super easy in Linux but meh in Windows.  Maybe that's because the USB driver appears to be built in to Ubuntu.

I'm not sure why they made it so hard.  This was so easy on the G1.

---

### Post by DouglasAWh on 2011-02-10
> **fjsimpkins said:**
> Ive only found articles about doing it in windows.

I bit the bullet and did it on Windows. Sucks, but I spent basically an entire day on it, so I was pretty fed up with it by the end.

Others may have better luck.  I misunderstood some things initially like the difference between clockworkmod and ROM manager. I'm not sure why my clockworkmod version changed after I got CyanogenMod installed, but meh.

If you have 2.2.3, I'd say CyanogenMod is not worth the effort.  I got the GApps installed, but the GMail version on CyanogenMod didn't have priority email, so that was a dealbreaker.  I tried briefly to get my third party apps, but CyanogenMod 6.1 doesn't appear to work with Titanium...or at least the way I did it.  They had to change something in CyanogenMod to make it work for Gingerbread.  I very well could have gotten that to work by packaging Titanium differently, but like I said, without Priority GMail, I wasn't willing to spend any more time on it.

Once I bought ROM Manager Premium and figured out how to use it, going back and forth between ROMs wasn't very difficult, so if you want to try out a lot of ROMs, I'd definitely say give it a shot.  I'm glad I have the app and glad I know I "wasted" $4.  It was a learning experience.  I'd pay more than $4 for an Android class...

---

### Post by blueridgedog on 2011-02-13
The site gives an overview of the process, working with ROMs and moving files too and from the device.  Additionally, if you read a great deal it covers the boot and os load process of the android phone fairly well.  The main issue is to get Adb working in Ubuntu, which would then let you access the phone from a USB connection.  

I use the google site search tool to get what I need from such complex sites:

site:forum.xda-developers.com adb ubuntu

[http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=site:forum.xda-developers.com+adb+ubuntu](http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=site:forum.xda-developers.com+adb+ubuntu)

---

### Post by rykel on 2011-02-19
@blueridgedog Thank you for detailing your experience rooting Android on Ubuntu... It is truly quite a learning curve, and like you, there is so many new terms and things do NOT work like they do on Ubuntu!    :)

---

