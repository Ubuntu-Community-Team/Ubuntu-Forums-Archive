---
title: "Flickering Windows"
date: 2011-06-14
forum: General Help
---

### Post by Jeffdude on 2011-06-14
So I downloaded ubuntu 10.04 about a month ago, due to some issues i was having with windows XP. Ever since I started using it, the windows would flicker rapidly to where I can't see what is on them. Also if i close out of a window its image would still be left on the screen. The only temporary fix to this would be to either open or close another window each time i open or close a window (normally i would just open the home folder or Terminal). However, with some programs, doing this really slows down my computer, so i would like to fix this issue.

Here's some information that may be helpful

Computer

hp Compaq dx2000 MT

Monitor

NEC AccuSync 120 21"

Resolution  

1600x1200

Graphics Card
```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:01.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 86)

```

---

### Post by seawolf167 on 2011-06-14
The flickering and ghost images could be your monitor - aged LCD/CRT monitors can flicker and display off-colors.

One thing you can easily do to see if it helps is to install any available graphics card drivers under System -> Administration -> Hardware Drivers

---

### Post by Jeffdude on 2011-06-15
I don't have a tool called hardware drivers. I do have one called additional drivers though, but that just displays a message "No proprietary drivers are in use on this system".

Sorry if this is inconvenient since i didnt have that tool i checked to see what version i am running and apparently its 11.04 instead, but i don't know how to be certain that it is cause both look similar... My friend who downloaded ubuntu for me had told me it was 10.04.

---

### Post by seawolf167 on 2011-06-15
Not a problem - the additional drivers & hardware drivers do the same thing, they are just named differently in different versions. You can see your exact version with the following command if you are interested

```
uname -a
```

Are there any entries under the additional drivers window that you are able to activate? Did the monitor flicker when you had Windows XP installed? Has it only occurred with Ubuntu? Do other monitors flicker as well?

---

### Post by Jeffdude on 2011-06-15
> Are there any entries under the additional drivers window that you are able to activate? Did the monitor flicker when you had Windows XP installed? Has it only occurred with Ubuntu? Do other monitors flicker as well?

There are no additional drivers listed in the tool. The monitor was fine with windows XP, and it didn't flicker until i installed ubuntu. As for working with other monitors i could probably check that in a day or so.

---

### Post by wildmanne39 on 2011-06-16
> **Jeffdude said:**
> There are no additional drivers listed in the tool. The monitor was fine with windows XP, and it didn't flicker until i installed ubuntu. As for working with other monitors i could probably check that in a day or so.
Hi, log out and click on your user name go to the bottom of the screen and click on ubuntu classic with no effects and see if your problem clears up.

---

### Post by seawolf167 on 2011-06-16
> **wildmanne39 said:**
> Hi, log out and click on your user name go to the bottom of the screen and click on ubuntu classic with no effects and see if your problem clears up.

Aye - just thought, do you have Compiz effects enabled?

---

### Post by Jeffdude on 2011-06-16
> Hi, log out and click on your user name go to the bottom of the screen and click on ubuntu classic with no effects and see if your problem clears up.  

The Classic Ubuntu worked!  

> Aye - just thought, do you have Compiz effects enabled?

I don't know if i do, so probably. 

Since this is fixed ill probably go and look into the features ubuntu has.


Thankyou!

---

### Post by wildmanne39 on 2011-06-16
> **Jeffdude said:**
> The Classic Ubuntu worked!  



I don't know if i do, so probably. 

Since this is fixed ill probably go and look into the features ubuntu has.


Thankyou!
Hi, your welcome, in unity compiz is used by default, unity is a plugin in compiz so do not disable unity or you will lose your desktop. If you want to change settings in compiz it has to be done a certain way. You can use this link to change settings while logged into unity if you want too. 
[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html) 
would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

