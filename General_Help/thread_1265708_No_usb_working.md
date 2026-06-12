---
title: "No usb working?"
date: 2009-09-13
forum: General Help
---

### Post by yescdr on 2009-09-13
Hello, I just installed ubuntu on another computer, after the install my usb mouse and usb keyboard won't work.

Not sure why, they do light up when the computer is turned on, but the light go out and they not working once ubuntu is booted.

They both work on other computers, so they do work.

Any ideas?

---

### Post by Don1500 on 2009-09-13
Me too
Jaunty

Curiously, my Wolverine SS USB hard drive is recognized, but since my mouse and keyboard aren't I can't open it.

---

### Post by yescdr on 2009-09-14
wow nobody has a idea?

---

### Post by Don1500 on 2009-09-14
bump

---

### Post by P4man on 2009-09-14
well, you're not alone:
[http://ubuntuforums.org/showthread.php?t=1266095](http://ubuntuforums.org/showthread.php?t=1266095)

I suggest someone experiencing the problem opens a bug report on launchpad.

---

### Post by Don1500 on 2009-09-14
Actually that was a hardware problem.
>  Re: Help get my wireless mouse working
Okay, so I did some searching around, and it turns out that the problem is the hardware on my USB. I figured it out because it was doing it in windows vista a little while ago. It just so happened to be doing it while I installed ubuntu. I took the computer apart and found a loose connection that was near one of the cooling fans. The fan would spin and knock it in and out of alignment.

So weird 0_o

Thanks so much for the help though.
My problem is that none of the USB connections work. I am using the wireless keyboard and mouse right now on Windows, and it works on Karmic Kubuntu, it also worked with Jaunty Ubuntu until yesterday when I tried to load Karmic Ubuntu. Karmic didn't work and it screwed up my grub so I had to reinstall Jaunty to get that back (I reinstalled without reformatting the /home partition.) At that time I was able to log into Jaunty, and it looked fine, until I went to move my mouse, and it didn't. And the keyboard won't work either. I connected a wired keyboard and mouse, that didn't work either. They were connected to different ports than the wireless. That's where I am now, I tried to log in to Recover but the USB ports are dead there, too. I have tried three Kernels with the same results. 

If I can't input anything how can I fix this? I'm getting ready to just reload Jaunty completely and re do everything. I have all my important stuff on a different drive.

---

### Post by yescdr on 2009-09-15
So weird, I have a wireless keyboard and mouse that work fine on my main ubuntu computer.  On the other one Im building its the regulars usb keyboard and mouse that won't work once the grub loads. I'm not having a wireless issue, just a usb issue on this one computer.  I have installed ubuntu on serveral computers only this one has this problem, could there be a problem with compatibility  , has a old AMD K-6 processor, Motherboard is a XA100 Plus? If that helps.

---

### Post by Don1500 on 2009-09-15
Yes, it's actually weirder than that, I lost the USBs after a reinstall. It worked fine for over 5 months (since a little after 9.04 was released).

---

### Post by Alex888 on 2009-09-15
Alright, about to install ubuntu, keeping my fingers crossed.
 
 
 
 
 
[DigiKun.com]("http://digikun.com")

---

### Post by Drone022 on 2009-09-15
I lost proper usb function after I put in an ATI graphics card, couldnt fix the problem, got a new keyboard and mouse instead (I needed them anyway).

---

### Post by Don1500 on 2009-09-15
> **Don1500 said:**
> Yes, it's actually weirder than that, I lost the USBs after a reinstall. It worked fine for over 5 months (since a little after 9.04 was released).

Weirder still, I reinstalled /root and now everything works. I lost all my packages (Firefox, Audacity, etc) And I'll need to reinstall them, but it works. 

Wait a sec, gonna try the sound........Works. Had to reinstall gstreamer, but it works.

---

### Post by ram2500 on 2009-09-15
Have you tried using other USB devices such as a flash drive? If you can't access any USB device, I think it's likely that the USB controller is not supported (unlikely) or the wrong driver is supplied. Is it a wireless keyboard/mouse you're using?

---

### Post by Don1500 on 2009-09-15
> **yescdr said:**
> Hello, I just installed ubuntu on another computer, after the install my usb mouse and usb keyboard won't work.

Not sure why, they do light up when the computer is turned on, but the light go out and they not working once ubuntu is booted.

They both work on other computers, so they do work.

Any ideas?

Since you were never able to do anything with your installation you should not have anything except the installation on the partition. Reinstall and see what happens.

---

### Post by Don1500 on 2009-09-15
> **Drone022 said:**
> I lost proper usb function after I put in an ATI graphics card, couldnt fix the problem, got a new keyboard and mouse instead (I needed them anyway).
Did that fix your problem? If it did it wasn't what I had.

---

### Post by yescdr on 2009-09-16
I reinstalled ubuntu, still no usb mouse or keyboard. Ive tried different mouses and keyboards,  I'll try and see if it will read my flash drive tomorrow.  If that don't work I will install windows on it see if It also has the same problem.

---

