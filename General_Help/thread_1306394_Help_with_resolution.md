---
title: "Help with resolution"
date: 2009-10-30
forum: General Help
---

### Post by sudoer541 on 2009-10-30
My resolution now is 1152 X 864 (4:3) @ 75Hz
When I try to set the resolution to 1440 X 900 (16:9) @ 75Hz it works but the graphics lag and I see no wallpaper and icons on my desktop. any suggestions?

---

### Post by sudoer541 on 2009-10-30
can someone please help?

---

### Post by Tibuda on 2009-10-30
What's your video card? Have you already installed the drivers in System > Admin > Hardware drivers (or restricted drivers)?

I suppose you are on 9.04, that's right?

---

### Post by sudoer541 on 2009-10-30
> **danielrmt said:**
> What's your video card? Have you already installed the drivers in System > Admin > Hardware drivers (or restricted drivers)?

I suppose you are on 9.04, that's right?

its 9.10 actually. My video card is ATI radeon 9250 or something like that. 
I never needed the restricted drivers.

---

### Post by VastOne on 2009-10-30
> **sudoer541 said:**
> its 9.10 actually. My video card is ATI radeon 9250 or something like that. 
I never needed the restricted drivers.

At this site

[http://www.hexus.net/content/item.php?item=20822](http://www.hexus.net/content/item.php?item=20822)

I found this


It's that time of the month again, folks.

ATI's driver team just released version 9.10 of the Catalyst drivers.

Here's what new, according to ATI:

Official ATI Catalyst WHQL release supporting ATI Radeon HD 5800 series GPUs

    * ATI Catalyst 9.10 now includes full GPU support for the award winning ATI HD Radeon 5800 series GPUS!

Super Sample Anti-Aliasing for the ATI Radeon HD 5800 Series

    * ATI Catalyst 9.10 provides support for a new Anti-Aliasing method on the ATI Radeon HD 5800 Series.  Users can now experience the high level of anti-aliasing image quality using Super Sampling anti-aliasing while maintaining good performance levels. 

Highlights of the ATI Catalyst™ 9.10 release for Linux includes:

New Features

Support for new Linux operating systems

    *
          o This release of ATI Catalyst driver for Linux introduces support for the following new operating systems:
                + Ubuntu 9.10 early look support

---

### Post by cariboo on 2009-10-30
ATI no longer supports your video card, you'll have to use the open source drivers.

To get the resolution you want you may have to add the horizontal sync and vertical refresh rates to you /etc/X11/xorg.conf:


```
Section "Monitor"
    Identifier     "Configured Monitor"
    HorizSync       28.0 - 95.0
    VertRefresh     50.0 - 120.0
EndSection
```

The above is what it looks like on my system. **Don't try the above on your system** I have a 19" crt, so the rates in the above example may damage your monitor.

---

### Post by sudoer541 on 2009-10-30
> **cariboo907 said:**
> ATI no longer supports your video card, you'll have to use the open source drivers. 
My computer used to work perfectly with the resolution I posted above. since I downloaded 9.10 I can still select the desired resolution, but I cant see the desktop wallpaper and the desktop icons. My computer lags and I have to wait like 2-4 seconds to move a window. 
this is very strange and disappointing.


just to recap I want to be able to use the edit 1440 X 900 (16:9) @ 75Hz resolution without any lags and black screens.
Thanks!

---

### Post by sudoer541 on 2009-10-30
OMG when I go to youtube I can hardly scroll to the button of the page. I cant even see the video properly. This resolution and flash thing is driving me crazy!

---

### Post by sudoer541 on 2009-10-31
if there is any way to fix this I would appreciate it! I never had this problem on previous version of ubuntu.

---

### Post by misfitpierce on 2009-10-31
Make sure the ATI driver is installed. Hit synaptic package manager and make sure xserver-xorg-video-ati and xserver-xorg-video-radeon are installed I guess instead of any FGLRX packages... FGLRX no longer supports your card as said etc... Also if you can, hit User CP at top of forums and under info change your distro to 9.10 please since you are using that one so people know right away which OS exactly your on... May help you out in future faster.

---

### Post by geoffree on 2009-10-31
Im also having monitor adjustment problems.  Running 9.10 on IBM with extreme 82865G integrated card.  There are no menus for adjusting resolution such as "Screen & Graphics". I've tried the fixes suggested such as adding Hz rates to xorg.conf which does not list any.

Please help.  

Geoffree  [email]zeno@empire.net[/email]

---

