---
title: "Gigabyte GA-MA785GM-US2H and ATI Hybrid CrossFireX"
date: 2009-10-08
forum: General Help
---

### Post by euphgeek on 2009-10-08
I just bought a new motherboard, a Gigabyte GA-MA785GM-US2H and apparently it has an onboard ATI Hybrid CrossFireX video card.  I can't seem to get the video card to work.  I've tried the ati driver but all I get is either a maximum of 800x600 resolution or a screen that is so misaligned it's unreadable.  But when I boot to the CD, I get a perfect 1280x1024 resolution just the way I want it.  I just can't figure out how to configure it when I boot from the hard drive.  I checked the xorg.conf file when booted from the CD but it didn't say which driver it was using.  I hate to think that I'd have to reinstall Ubuntu, but is that my only choice or would that not help at all?  I am running version 8.04.

---

### Post by khelben1979 on 2009-10-08
According to [this link]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=3141") from Gigabyte, you have an inbuilt ATi Radeon 4200 graphics chip on that one.

I would advice you to go to [this website]("http://support.amd.com/us/gpudownload/Pages/index.aspx") from ATi to get better drivers.

---

### Post by euphgeek on 2009-10-08
So I have to use a proprietary driver for this video card?  That's disappointing.  Why is it that booting from the CD works without the use of a proprietary driver?

---

### Post by euphgeek on 2009-10-08
I was just looking into how to reconfigure X from the command line and found this command:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

I ran it and now suddenly my video card works perfectly at 1280x1024.  I looked into my xorg.conf file and nothing is configured as the video driver.  All it says is this:

```
Section "Device"
     Identifier     "Configured Video Device"
EndSection
```

Is there any way to tell what driver it's using?

---

### Post by khelben1979 on 2009-10-08
> **euphgeek said:**
> Is there any way to tell what driver it's using?

Well.. I would advice you to test some heavy graphics now to see if it's fast enough. If it isn't, then it's back to ATi.com..

---

### Post by Toadmund on 2009-10-10
I am considering buying the same MoBo, and I am searching the net for Linux problems with it, but, it is new and there is not much out there.
I would really like to know how you make out with it.

My current MoBo is a 4 year old MSI rs480, I am looking for a big improvement even though this board has served me adequately for my needs.

Would you recommend it euphgeek?
Have you overcome your trials and tribulations?

Thanks.

---

### Post by MaindotC on 2009-10-15
I've been trying since last night to get this to display properly.  I installed the video drivers by using the Hardware Drivers option, and it's always messing up.  I tried the 9.x drivers from ATI's website and I'm still having lots of problems.  All I want to do is wine Counterstrike that runs decently on my specs listed below, but this new mobo I got isn't working for me :(

Can you see if you can run Counterstrike?  Please?

---

### Post by euphgeek on 2009-11-06
> **Toadmund said:**
> I am considering buying the same MoBo, and I am searching the net for Linux problems with it, but, it is new and there is not much out there.
I would really like to know how you make out with it.

My current MoBo is a 4 year old MSI rs480, I am looking for a big improvement even though this board has served me adequately for my needs.

Would you recommend it euphgeek?
Have you overcome your trials and tribulations?

Thanks.

Yes, I have overcome the trials and tribulations.  My problem was that I removed my old motherboard and put in the new motherboard without reconfiguring Ubuntu.  Using the command:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```will make the on-board video card work.  You can also download the driver from ATI's website which works just as well, if not better (I haven't tested any heavy graphics on it).

---

### Post by okane on 2010-07-02
When configured to 8 GB, Ubuntu 10.04 64 bit freezes on large (>1 GB) file transfers. Removing one 2GB memory resolved the problem (from four 2 GB cards initially to three 2 GB cards finally). System freeze is total - requires reboot.

---

