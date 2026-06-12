---
title: "Various web browsers crashing/screen freezing. What is going on?!"
date: 2010-10-22
forum: General Help
---

### Post by interconnect on 2010-10-22
Hi, I'm having a problem with various browsers crashing on me.  Firefox 3.6.11, Chromium 6, Google Chrome 7, they all crash or freeze on me and I can't figure out what is going on.  I'm on a fresh/clean install of 10.10 with all updates installed.  I've tried reviewing all the logs in /var/logs/ but didn't find anything unusual although I might have missed something.  I'm using the proprietary nVidia driver for my video card (GeForce FX 5500 - 173.x drivers) so I'm not sure if that may have something to do with it or that it may be my NIC card?  I've gone to the NIC card manufacturers website (Realtek) for updated drivers, but the site says the drivers are built in to the kernel and there is no download available.

It seems as though the only time it crashes or the screen freezes (sometimes with the lights blinking on my keyboard) is when I'm browsing the internet.  Any help would be greatly appreciated!

---

### Post by TeoBigusGeekus on 2010-10-22
Any particular sites where this happens?

---

### Post by interconnect on 2010-10-22
> **TeoBigusGeekus said:**
> Any particular sites where this happens?

No, seems to be at random. Sometimes they'll crash at launch, sometimes just when reading a particular page.  I am out of ideas on how to diagnose what is going on here.  I've also ran memtest and scanned my drive for errors, both of which turned up nothing.

---

### Post by TeoBigusGeekus on 2010-10-22
Launch the browsers via command line and post us any error messages.

---

### Post by interconnect on 2010-10-22
> **TeoBigusGeekus said:**
> Launch the browsers via command line and post us any error messages.

How do you do that?  Will error messages print in terminal?

---

### Post by Erin on 2010-10-22
Disable all the add-ons and plug-ins. Then see if the browser is stable. Then, re-enable them one by one until it keels over again.

Erin

---

### Post by TeoBigusGeekus on 2010-10-22
> **interconnect said:**
> How do you do that?  Will error messages print in terminal?
Open terminal, type 
```
firefox
```
and press enter.
When the browser crashes, you should see some error messages in the terminal.
Repeat for chromium
```
chromium
```
and chrome
```
chrome
```

---

### Post by interconnect on 2010-10-25
I got this the last time Firefox crashed:

Add-ons: [email]langpack-en-CA@firefox-3.6.ubuntu.com:3.6,langpack-en-GB@firefox-3.6.ubuntu.com:3.6,langpack-en-AU@firefox-3.6.ubuntu.com:3.6,langpack-en@firefox-3.6.ubuntu.com:3.6,ubufox@ubuntu.com[/email]:0.9rc2,{972ce4c6-7e08-4474-a285-3208198ce6fd}:3.6.11
BuildID: 20101013120202
CrashTime: 1288017623
EMCheckCompatibility: true
FramePoisonBase: 00000000f0dea000
FramePoisonSize: 4096
InstallTime: 1287688983
ProductName: Firefox
ReleaseChannel: default
SecondsSinceLastCrash: 257741
StartupTime: 1288015906
Theme: classic/1.0
Throttleable: 1
URL: [http://www.nytimes.com/2010/10/25/business/media/25ipad.html?_r=4&src=twt&twt=nytimesbusiness](http://www.nytimes.com/2010/10/25/business/media/25ipad.html?_r=4&src=twt&twt=nytimesbusiness)
Vendor: Mozilla
Version: 3.6.11

This report also contains technical information about the state of the application when it crashed.

---

