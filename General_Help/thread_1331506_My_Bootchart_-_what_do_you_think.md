---
title: "My Bootchart - what do you think?"
date: 2009-11-19
forum: General Help
---

### Post by megamania on 2009-11-19
1 minute and 20 seconds to boot looks a bit too long for me. Since I tested Karmic since Alpha, I clean-installed it when the Beta was released.

Can you please take a look at my bootchart and give your opinions?

I'm using a 4-month old Acer 6930g laptop, 4GB RAM, Intel Core 2 Duo P7350 2.0GHZ.


EDIT: I see the picture was automatically resized and is unreadable... I'll have to find a way to post it in a readable format.

---

### Post by megamania on 2009-11-19
I uploaded the image here:

[http://img682.yfrog.com/img682/7195/laptopkarmic200911191.png](http://img682.yfrog.com/img682/7195/laptopkarmic200911191.png)

Thanks for any help!

---

### Post by fluffman86 on 2009-11-19
I can't read your attachment, but when I installed Karmic I noticed that it was slow to boot as well, and most of the time was just loading Grub2.  Turns out, my /boot was on my slave drive, and my MBR was on my primary drive.  I just changed my boot order in BIOS to boot the other drive.

edit: well, now that I can read it I see that it's stalling out for about 10 seconds on ureadahead.  It's pink, so that means you're in an I/O wait period when not a lot is going on.  Try searching around for that.  Other than that, not sure what else to speed up, except Xorg.  I guess you could just not use X. :P

---

### Post by Giblet5 on 2009-11-19
I'm pretty sure you're spending more time playing with bootchart than your system will spend booting over the next year.

That's the only possible boot problem I can see at this point. The fix is easy too.

---

### Post by QLee on 2009-11-19
[QUOTE=fluffman86]I can't read your attachment, but when I installed Karmic I noticed that it was slow to boot as well, and most of the time was just loading Grub2.  Turns out, my /boot was on my slave drive, and my MBR was on my primary drive.  I just changed my boot order in BIOS to boot the other drive.
[/QUOTE]
Huh? The MBR used is always the one on the primary drive (the one booting). If you switched the boot order in BIOS you must have had GRUB written to the MBR of that drive too or the system couldn't have booted.

---

### Post by fluffman86 on 2009-11-19
Hahaha...Giblet5 has a point. :D

I seriously shut down my computer like twice a month, and that's only because I have the backported kernels coming in.  And half the time that I reboot my desktop it's while I've run updates via ssh from my laptop, and I'm not even in the same town.  :\

edit @ QLee: Whoa, sorry, that was kinda confusing.  My point was that grub started to load, and was looking for /boot on my Primary drive.  /boot was on another drive, so it was taking like 30 seconds just to load grub.  I changed my boot order in BIOS and now I have like a <1min boot time.

---

### Post by megamania on 2009-11-19
> **fluffman86 said:**
> I can't read your attachment, but when I installed Karmic I noticed that it was slow to boot as well, and most of the time was just loading Grub2.  Turns out, my /boot was on my slave drive, and my MBR was on my primary drive.  I just changed my boot order in BIOS to boot the other drive.

You probably got it right at your first attempt. :-)

My laptop has 2 500GB hard disks. I didn't want to delete Vista (even if I've never used it), so I installed Ubuntu on the second hard disk. I was hoping the MBR would be written on the Ubuntu hd (it was set as boot disk in the bios), but the installer set-up a dual-boot.

So the MBR is on the first hd and ubuntu on the second.

I'll try deleting the dual-boot and writing a MBR for each disk.

> **fluffman86 said:**
> 
edit: well, now that I can read it I see that it's stalling out for about 10 seconds on ureadahead.  It's pink, so that means you're in an I/O wait period when not a lot is going on.  Try searching around for that.  Other than that, not sure what else to speed up, except Xorg.  I guess you could just not use X. :P
:-) I don't need a super-fast boot time. But Karmic on the laptop boots slower than 9.04 on my 3-year old desktop...


> **fluffman86 said:**
> I seriously shut down my computer like twice a month, and that's only because I have the backported kernels coming in.  And half the time that I reboot my desktop it's while I've run updates via ssh from my laptop, and I'm not even in the same town.  :\
I installed bootchart yesterday and rebooted twice to see if it worked. I'm not a hardware freak. :-)

Since I use my computer at home only at night, I shut it down every day and I can tell it boots slowly.

Thanks for your suggestions, fluffman86. :p

---

### Post by BarisBlaq on 2009-11-19
I have the same laptop as the OP, only with a slightly different cpu..

And woohoo I beat your time!!
=)))

Here's my bootychart:
[http://i748.photobucket.com/albums/xx129/bblaq/BlackBox-karmic-20091119-2.png](http://i748.photobucket.com/albums/xx129/bblaq/BlackBox-karmic-20091119-2.png)

Sorry in a hurry right now, but will watch this thread and respond more properly later on
=/

---

### Post by fluffman86 on 2009-11-19
> **megamania said:**
> 

So the MBR is on the first hd and ubuntu on the second.

I'll try deleting the dual-boot and writing a MBR for each disk.


No, wait! You don't need to erase anything.  Just when your computer is booting, go into the BIOS, find the boot options there, and it should let you change the boot order.  Make sure you Hard Drives are booting first, then change the order of the hard drives so that the one with Ubuntu on it boots first.

---

### Post by megamania on 2009-11-19
> **fluffman86 said:**
> No, wait! You don't need to erase anything.  Just when your computer is booting, go into the BIOS, find the boot options there, and it should let you change the boot order.  Make sure you Hard Drives are booting first, then change the order of the hard drives so that the one with Ubuntu on it boots first.
Yes, but if I change the bios to get the computer to boot from the second hd, it can't boot because grub is on the first hd.

I'll have to re-create the bootloaders for each disk in order to be able to do what you suggest - unless I'm missing something.

---

### Post by BarisBlaq on 2009-11-19
Ok, first off sorry bout the earlier chart, it resizes.. =/
Attached is my bootchart, hope it works this way..

Things I noticed about your chart:
- usplash - you might try disabling it by removing from kernel parameters in grub
- you have a loong red "init" bar after your avahi-daemon.. i'm not sure what it is, but it seems to use up quiet some resources
- also, your "Xorg" process seems to be a bit too blue, at least compared to mine.. again, I'm not sure why that is, i'm just comparing it to my laptop which is same make as yours

Also, ubuntu on second hd is most probably slowing things down too. I have single hd and only ubuntu installed (though multiple partitions)

---

### Post by megamania on 2009-11-20
> **BarisBlaq said:**
> Also, ubuntu on second hd is most probably slowing things down too. I have single hd and only ubuntu installed (though multiple partitions)
My current situation is:
2 hard disks
hard disk 1: Windows Vista - factory installed
hard disk 2: Ubuntu

I can select the boot order from BIOS (which is what I wanted to do), but the Ubuntu install set things up so that I have to boot from hard disk 1 to get the Grub dual-boot menu.

I'd like to make both disks bootable, and then select what to boot from the bios (that's because I never, ever use Vista).

Any ideas how to proceed?

---

### Post by hal8000 on 2009-11-22
I have just discovered something interesting the timing on bootchart with Karmic is not accurate.
I'm booting with grub controlled by Mandriva (that is grub legacy or grub1).
When I select Karmic it loads in 25 seconds,timed with stop watch.
This is far different from the 1minute 2 secs in the screenshot.

I know bootsplash now starts at grub, I wonder if this is a problem with bootsplash or grub?
Previously Jaunty Jackalope loaded in 18 seconds and both my stopwatch and bootchart agreed.

Try using a stopwatch after you press enter at the grub prompt for karmic, do you see a difference also?

---

### Post by megamania on 2009-11-24
> **hal8000 said:**
> Try using a stopwatch after you press enter at the grub prompt for karmic, do you see a difference also?
I can try this, but I need to know exactly when to start and stop timing, so we have comparable results.

---

### Post by glarrain on 2009-11-26
I have a brand new T400 (4GB, Intel P8700, 7200rpm HDD). I takes pretty long to boot up and I have only installed bootchart and all the updates.

Ubuntu's performance has disappointed me so far.

Time: 01:02.03

Curiosly, between 36 and 58 seconds, the CPU and Disk are almost not used. I wonder what is going on in that. I'll let you know when I find out.

PS: how can I attach the PNG image without it getting downsized in resolution and format (JPG)

---

### Post by megamania on 2009-11-26
> **glarrain said:**
> 
PS: how can I attach the PNG image without it getting downsized in resolution and format (JPG)
You can try an image hosting service like [http://tinypic.com/](http://tinypic.com/)

---

### Post by hal8000 on 2009-11-29
> **megamania said:**
> I can try this, but I need to know exactly when to start and stop timing, so we have comparable results.

Sorry for delay.
Remember I'm using grub legacy boe (or grub 1). 
Highlight the Karmic stanza in grub legacy and zero the stopwatch. As you press enter (to start karmic ) start the stopwatch also. 
End timing when you reach the gnome login screen. Its a lot different to the results shown in bootchart for me.
Bootchart shows 62 seconds when I was using grub2, still shows 62 seconds although its 25 seconds using grub 1.
Hope that helps

---

### Post by megamania on 2009-11-29
> **hal8000 said:**
> 
Highlight the Karmic stanza in grub legacy and zero the stopwatch. As you press enter (to start karmic ) start the stopwatch also. 
End timing when you reach the gnome login screen. 
42 seconds for my computer from Grub to login screen...

---

