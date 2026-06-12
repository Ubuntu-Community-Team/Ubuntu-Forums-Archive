---
title: "Unclear grpahic images in Ubuntu."
date: 2010-08-31
forum: General Help
---

### Post by AnkurGel on 2010-08-31
Hi everyone,
I just bought a 17.5" widescreen. I have installed Ubuntu 10.04 via Wubi through Windows XP. 
In Windows XP, every image is amazingly clear but in Ubuntu all images are a bit hazy; let it be 1920*1080 wallpapers or small images while surfing web.
I searched about the reason for this on ubuntuforums.org and read this: [http://ubuntuforums.org/showthread.php?t=1488286](http://ubuntuforums.org/showthread.php?t=1488286) .
In response to: 
```
lspci
```I get following output
> 00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
and for ```
lspci | grep VGA
``` I get following output:
> 00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
Please guide me to sort out this problem. I don't think there is any driver need to be installed for this. It doesn't have any dedicated Graphic Card.

-AnkurGel

---

### Post by inso_741 on 2010-08-31
try this till you get a better response.... 
```
sudo apt-get update && sudo apt-get install xserver-xorg-video-intel
```

---

### Post by AnkurGel on 2010-08-31
> **inso_741 said:**
> try this till you get a better response.... 
```
sudo apt-get update && sudo apt-get install xserver-xorg-video-intel
```

Nothing happened. All what I got in response is:
> 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                                    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                                
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                                    
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources    
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 255 not upgraded.

What should I do next?

---

### Post by Grenage on 2010-08-31
I assume you're after the native res, and it's not using it.  Double check in Preferences/Monitor, and ensure you have the right res selected, if it will let you.

Failing that, could you post your monitor make/model, and the desired resolution?  I'll jot you a quick xorg.conf file when I got back from lunch, if it's not working by then.

---

### Post by coffeecat on 2010-08-31
Try pressing the auto button on the monitor to retune it to the signal from the graphics card when you boot into a different OS. Even with the same graphics card, there seem to be differences in the frequency, or something, with the Windows and Linux graphics drivers. A new-ish monitor *should* autotune for you, but it's worth trying.

---

### Post by AnkurGel on 2010-08-31
> **Grenage said:**
> I assume you're after the native res, and it's not using it.  Double check in Preferences/Monitor, and ensure you have the right res selected, if it will let you.

Failing that, could you post your monitor make/model, and the desired resolution?  I'll jot you a quick xorg.conf file when I got back from lunch, if it's not working by then.

Resolution looks good on Ubuntu. I almost get same resolution in Windows XP too. This monitor is LG Flatron W1943C 17.5" Widescreen. The resolution which Ubuntu prompts is : 1360*768(16:9). After this resolution only 4:3 resolution of 1024*768 is available.

---

### Post by inso_741 on 2010-08-31
can you post some screenshots.........???

---

### Post by AnkurGel on 2010-08-31
> **coffeecat said:**
> Try pressing the auto button on the monitor to retune it to the signal from the graphics card when you boot into a different OS. Even with the same graphics card, there seem to be differences in the frequency, or something, with the Windows and Linux graphics drivers. A new-ish monitor *should* autotune for you, but it's worth trying.
I tried AutoSet just now. Nothing great happened except alignment of borders which was already in it's place before. This is what confusing me.. there is no problem in graphics on XP but it is jut dim and hazy-around-the-edge on Ubuntu. 
I even thought that maybe Wubi installation is problem.. So I tried Live Version.. but the problem remains.

---

### Post by AnkurGel on 2010-08-31
> **inso_741 said:**
> can you post some screenshots.........???
Oh! Sure.
[IMG]http://img841.imageshack.us/img841/8656/screenshotmonitorprefer.png[/IMG]
I have no idea why it shows Goldstar Company Ltd... I just noticed it.
[IMG]http://img683.imageshack.us/img683/2135/screenshotfa.png[/IMG]
This is all-clear pic which is looking unclear on my desktop. I doubt if it will look the same way on yours.
EDIT: This is the original link of the pic mentioned above. [http://sphotos.ak.fbcdn.net/hphotos-ak-snc4/hs392.snc4/45472_120113271373091_100001232573399_123501_5529828_n.jpg](http://sphotos.ak.fbcdn.net/hphotos-ak-snc4/hs392.snc4/45472_120113271373091_100001232573399_123501_5529828_n.jpg)

---

### Post by AnkurGel on 2010-09-01
Please, can anyone help me in sorting this out?? I really need to get over this problem.. It's forcing me to swap back to XP. :( which I never want to.

---

### Post by wesleybailey on 2010-09-01
Did you try adjusting the refresh rate? In your screenshot it is set to 60Hz. 

You could check what refresh rate Xp has detected.

Start, then Settings, then Control Panel, and then double-clicking the Display icon to bring up the Display Properties window. Click on the "Settings" tab and then push the "Advanced" button which brings up the Properties page for your particular video card and monitor. Click on the "Monitor" tab. Check the Refresh Frequency.

Latest tutorial: How to convert [.uif to iso]("http://wesleybailey.com/articles/uif-to-iso-converter") with Linux or Windows

---

### Post by AnkurGel on 2010-09-01
> **wesleybailey said:**
> Did you try adjusting the refresh rate? In your screenshot it is set to 60Hz. 

You could check what refresh rate Xp has detected.

Start, then Settings, then Control Panel, and then double-clicking the Display icon to bring up the Display Properties window. Click on the "Settings" tab and then push the "Advanced" button which brings up the Properties page for your particular video card and monitor. Click on the "Monitor" tab. Check the Refresh Frequency.
Nice Idea. Will do that now. But apparently there is only 60Hz available in Ubuntu for me. :(

---

### Post by AnkurGel on 2010-09-01
This is the output from Windows XP:
[http://img4.glowfoto.com/images/2010/09/01-1026569028L.jpg](http://img4.glowfoto.com/images/2010/09/01-1026569028L.jpg)

It is also using same frequency, 60Hz. Can it have anything to do with dot-per-inch(dpi)?

---

### Post by inso_741 on 2010-09-01
to me atleast the fonts on ubuntu screenshot look better then those on xp.....

---

### Post by AnkurGel on 2010-09-01
> **inso_741 said:**
> to me atleast the fonts on ubuntu screenshot look better then those on xp.....

I guess that it will obviously look cool on your screen as it doesn't have any problem. Even when I am seeing it from XP now is making it perfectly clear. It's in 'this' ubuntu installation that it is looking hazy.
I have tried Live Ubuntu 9.10 (Karmic)to see if it has same problem and it does.

---

### Post by wesleybailey on 2010-09-01
In my opinion DPI should not affect the clarity of the images displayed. 

Can you humor me and run this command, and show me the output. 
```
xrandr
```

---

### Post by inso_741 on 2010-09-01
you say that you just bought the monitor...so did the problem start with this new monitor or was it present on the previous monitor too???
also try searching for linux drivers on manufacturers website for the new monitor and provide some info on the monitor

---

### Post by AnkurGel on 2010-09-01
> **wesleybailey said:**
> In my opinion DPI should not affect the clarity of the images displayed. 

Can you humor me and run this command, and show me the output. 
```
xrandr
```

Output:
> 
VGA1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 406mm x 229mm
   1360x768       60.0*+
   1024x768       75.1     75.0     60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1 


---

