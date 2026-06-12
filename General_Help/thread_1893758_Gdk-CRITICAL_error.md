---
title: "Gdk-CRITICAL error"
date: 2011-12-11
forum: General Help
---

### Post by Rikeshar on 2011-12-11
Hello everyone, got a question for you. I'm getting errors when trying to run Hulu Desktop, but I have a feeling it's not a problem with the application itself, but something called GDK (I'm not familiar enough with back end linux things to know too much about that, sorry!)  

The errors I'm getting are: 

```
(huludesktop:2368): Gdk-WARNING **: gdk_window_new(): parent is destroyed


(huludesktop:2368): Gdk-CRITICAL **: IA__gdk_window_get_display: assertion `GDK_IS_WINDOW (window)' failed

(huludesktop:2368): Gdk-CRITICAL **: IA__gdk_x11_get_xatom_by_name_for_display: assertion `GDK_IS_DISPLAY (display)' failed

(huludesktop:2368): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.6/gdk/x11/gdkdrawable-x11.c:952 drawable is not a pixmap or window

(huludesktop:2368): Gdk-CRITICAL **: IA__gdk_x11_display_get_xdisplay: assertion `GDK_IS_DISPLAY (display)' failed
Segmentation fault
```

It seems to me that the program and GDK aren't talking... any ideas?

I've had this application installed before, and it worked. I recently removed and tried reinstalling it and this is what I'm getting. To remove it I did

```
sudo apt-get purge huludesktop
```

and then I ran auto-remove as well. Is it possible that auto-remove took out a dependency that's not getting reinstalled? I'm at a loss here on how to get this working again.

Thanks in advance for any help!

---

### Post by Rikeshar on 2011-12-12
As an update: I tried installing Hulu Desktop on a clean install of Mint 12, and I'm getting the same errors. Anyone with any ideas?

---

### Post by oldtimer7777 on 2011-12-12
> **Rikeshar said:**
> As an update: I tried installing Hulu Desktop on a clean install of Mint 12, and I'm getting the same errors. Anyone with any ideas?

Did you install it from the Hulu web site?

[http://www.hulu.com/labs/hulu-desktop-linux](http://www.hulu.com/labs/hulu-desktop-linux)

And did you use the deb file to install it from that page?

Install it with gdebi this time.

sudo apt-get install gdebi

---

### Post by Rikeshar on 2011-12-12
I did, and I made sure to use the correct architecture too (32bit)

EDIT: Didn't see the end of your post here. When on Ubuntu just double clicking the .deb would install it, but I'm pretty sure on Mint I had to use Gdebi. What is the difference exactly?

---

### Post by oldtimer7777 on 2011-12-12
I'm sorry I should have said that you need to post this question in the proper Mint forum because this just installed fine on my Ubuntu system with the deb file from the hulu web site.  Ask if anyone else has trouble installing it in Mint first, by posting your question to a Mint forum on the Mint web site discussion board. 

> **Rikeshar said:**
> I did, and I made sure to use the correct architecture too (32bit)

EDIT: Didn't see the end of your post here. When on Ubuntu just double clicking the .deb would install it, but I'm pretty sure on Mint I had to use Gdebi. What is the difference exactly?

---

### Post by Rikeshar on 2011-12-12
What version of Ubuntu are you using? I cannot get it to install on 11.10, I get those errors I mentioned. I only mentioned Mint because in my frustration in not being able to get it to work with Ubuntu 11.10, I decided I didn't have anything to lose except a few hours by clean installing, and I took that opportunity to try Mint. I, however, got the exact same issues in Mint 12 as I did in Ubuntu 11.10, so the question is still valid here!

I'm thinking I might just have to go back to using 11.04 for a while, since I didn't have any issues with it there.

The program will -install- fine, but I get those errors when I try to run it.

---

### Post by oldtimer7777 on 2011-12-13
I am using 11.04. :) lol

It works just fine. Perhaps Hulu hasn't tested their application in the latest released version of Ubuntu yet.  You should email them to let them know about your experience.

> **Rikeshar said:**
> What version of Ubuntu are you using? I cannot get it to install on 11.10, I get those errors I mentioned. I only mentioned Mint because in my frustration in not being able to get it to work with Ubuntu 11.10, I decided I didn't have anything to lose except a few hours by clean installing, and I took that opportunity to try Mint. I, however, got the exact same issues in Mint 12 as I did in Ubuntu 11.10, so the question is still valid here!

I'm thinking I might just have to go back to using 11.04 for a while, since I didn't have any issues with it there.

The program will -install- fine, but I get those errors when I try to run it.

---

### Post by Rikeshar on 2011-12-13
Aha! Well, a rollback it is then! That program is a critical part of my home entertainment, since we finally ditched cable TV. Thanks for your help, and for verifying that it still works fine on 11.04. It worked fine on 11.10 for a while too, so maybe there was an update pushed that broke something. 

Anyways, thanks again.

---

### Post by oldtimer7777 on 2011-12-13
> **Rikeshar said:**
> Aha! Well, a rollback it is then! That program is a critical part of my home entertainment, since we finally ditched cable TV. Thanks for your help, and for verifying that it still works fine on 11.04. It worked fine on 11.10 for a while too, so maybe there was an update pushed that broke something. 

Anyways, thanks again.

I wish I could be more help with that Hulu installation in Ubuntu 11.10..  I would report the issue with Hulu if I were you, for all the trouble.  They need to test that themselves to fix it for everyone. 

Don't forget to mark this thread solved above with Thread Tools. Thanks. 

Cheers.

:popcorn::popcorn:

---

### Post by Rikeshar on 2011-12-13
Okay now I'm COMPLETELY at a loss. I've installed a clean copy of 11.04 and I'm STILL getting the same errors. What could this be?!

Could it be something with my Nvidia drivers and/or xorg.conf? How could I go about testing this?

UPDATE: Well, if I run my 11.04 live CD, Hulu desktop works fine there, so there's some update between then and now that breaks it. :(

---

### Post by oldtimer7777 on 2011-12-13
> **Rikeshar said:**
> Okay now I'm COMPLETELY at a loss. I've installed a clean copy of 11.04 and I'm STILL getting the same errors. What could this be?!

Could it be something with my Nvidia drivers and/or xorg.conf? How could I go about testing this?

UPDATE: Well, if I run my 11.04 live CD, Hulu desktop works fine there, so there's some update between then and now that breaks it. :(

I think you are installing something that is causing a conflict too.  You will have to try again and slowly try to figure out which package install is causing it, one at a time, and let us know.

---

### Post by Rikeshar on 2011-12-21
Sorry it took me so long to respond. I've actually found out what is causing the errors. Using flash-aid for firefox I installed the beta version of flash, and this caused hulu desktop to give out those GDK errors. I tried using the plugin to install the stable version and now it's doing the same thing it was which caused me to start messing with it (and thus get the GDK errors in the first place), it's freezing up my computer when navigating the screen. 


UPDATE: The version that causes Hulu Desktop to freeze (on startup of the program now) is: Shockwave Flash 11.1 r102

The version that causes the GDK errors: Shockwave Flash 11.2 d202

UPDATE 2: I removed the libflashplayer.so from /usr/lib/mozilla/plugins (where the 11.2 d202 flash gets installed) and I removed it from /usr/lib/flash-installer (i think that's what it was [where the 11.1 r102 version gets installed]) 

I then installed the "Adobe Flash 10" plugin from the Ubuntu Software Center, and it installed to /usr/lib/adobe-flashplugin When using this one, Hulu Desktop will run, but the video is back to not tracking well, which is what it did when first installed on the previous version of Ubuntu, and which the flash-aid plugin for firefox fixed.

ANy ideas?

---

### Post by Rikeshar on 2012-08-08
UPDATE: Just to close out an old thread. The solution was to download an older version of flash and point the hulu config file to it.

---

