---
title: "Freezes in Ubuntu 11.10"
date: 2011-11-23
forum: General Help
---

### Post by qasmobi on 2011-11-23
Hi
 
i am a total newbi and my first experience with linux is with ubuntu
 
i get the odd freeze prob every five minutes for a minute. i have searched and searched and for a solution and tried various solutions but nothing worked, so here is my first post on unbuntu :)
 
i have heard it could be the graphics driver i downloaded the ati graphic driver from:
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English)
 
now i have followed the instructions and it comes back with;
error .default_policy.sh does not support version, Default::v2:i686:lib: :none:3.0.0-13-generic; make sure teh version is being correctly set by --iscurrentdistro
 
but it is the correct driver!.......
my system it is old, details are; 
p4 2.5, 2gb ram
ati radeon 9700 pro graphics card.
 
please help, also keep in mind i am a newbi :)
 
if you need for info let me know, thanks
 
also i have notice dwhen i go into system info there is no graphics listed...

---

### Post by coffeecat on 2011-11-23
AMD no longer supports your Radeon 9700 card with its proprietary driver. See here:

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English)

What you have downloaded will not work with your card, and you have no alternative to the open source driver that came with your machine. System freezes can be caused by some video driver/card combinations, but I believe it is unlikely with yours, and that you need to investigate other causes. The first thing to try to exclude is faulty RAM. Because Linux uses RAM differently from Windows, it is more likely to uncover the faulty bits. Try running memtest from the grub menu for several hours. A single pass is not enough.

Because there are several possible causes for system freezes, not just video driver issues, you would be better off with a different thread title and this thread moving to another sub-forum in order to attract more help. Post back if you want that.

---

### Post by qasmobi on 2011-11-23
now you have made me proper confused :confused:  thats the link i sent you, but why will they list the 9700 as the driver and give you the driver to download
 
ok so how do i install a graphics driver? because in system info, no graphic card info is listed...
 
sorry i dont understand 'Try running memtest from the grub menu' you mean in terminal?
 
 
im a newbi trying my best to learn.....

---

### Post by coffeecat on 2011-11-23
> **qasmobi said:**
> now you have made me proper confused :confused:  thats the link i sent you, but why will they list the 9700 as the driver and give you the driver to download

Apologies, I missed that you posted the same link. But if you look at the text in it, it says:

> The Linux ATI Catalyst&#8482; driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above.

As far as Ubuntu is concerned, "distributions prior to February 2009" means only legacy and now obsolete versions of Ubuntu. The version of the xserver, the underpinnings of the GUI, is newer in each newer release of Ubuntu and the proprietary drivers have to be built to be compatible with the xserver. AMD Catalyst drivers that can run your card, such as the one you downloaded from that site, are only compatible with now legacy versions of the xserver and hence legacy versions of Ubuntu, Ubuntu 8.10 and earlier.
 
> **qasmobi said:**
> ok so how do i install a graphics driver? because in system info, no graphic card info is listed...

You already have a graphics driver which came as default in your installation and is capable of running that card. It's the open source driver. It's possible that it's the cause of freezes, but I think you need to look wider than video driver issues. My guess is that the references you found to graphics drivers and freezes were about different cards and different drivers.
 
> **qasmobi said:**
> sorry i dont understand 'Try running memtest from the grub menu' you mean in terminal?

Are you running Ubuntu as a dual-boot with Windows, or by itself? If you have only Ubuntu on that machine, press the shift key while the POST/BIOS screen is showing and that should cause the "grub" boot menu to show. Memtest will be a few down on the list.

Back to video driver issues - I'm not discounting them, just think them unlikely. There are some boot options you can try, but you need to be able to see the grub menu to do this, so let's make sure you can do so first.

**EDIT**: [s]by the way, which version of Ubuntu are you running?[/s] Scratch that! :) I can see from "3.0.0-13-generic" in your first post that you are running 11.10.

---

### Post by qasmobi on 2011-11-23
ohhhh yep and it shows im a newbi :)
 
thanks
 
yes i installed ubuntu 11.10 standalone, no dual boot.
 
ok when i get home i will give that a try and run memtest, thanks and i will post back the results.
 
i just found this
[http://manpages.ubuntu.com/manpages/jaunty/man4/radeon.4.html](http://manpages.ubuntu.com/manpages/jaunty/man4/radeon.4.html)
 
will this help me? and how? it does list my graphics card.
 
i appreciate all your help.

---

### Post by coffeecat on 2011-11-23
> **qasmobi said:**
> 
i just found this
[http://manpages.ubuntu.com/manpages/jaunty/man4/radeon.4.html](http://manpages.ubuntu.com/manpages/jaunty/man4/radeon.4.html)
 
will this help me? and how? it does list my graphics card.

Yes, that's the open source ati/radeon driver for your card. The options listed there were not the boot options I was thinking about, but might be useful.

Do you want me to rename this thread and move it to another sub-forum? I would suggest General Help, as this forum is used mostly for multimedia issues.

---

### Post by qasmobi on 2011-11-23
Yes thanks you can move it, sorry i was not sure if this was the correct sub-forum

---

### Post by qasmobi on 2011-11-23
im sorry for totally newbi questions and how tos....
 
how would i install the below drivers?
[[COLOR=#000000]http://manpages.ubuntu.com/manpages/.../radeon.4.html[/COLOR]]("http://manpages.ubuntu.com/manpages/jaunty/man4/radeon.4.html")

---

### Post by coffeecat on 2011-11-23
> **qasmobi said:**
> Yes thanks you can move it

Done. I've renamed it to get more help for you.

> **qasmobi said:**
> 
how would i install the below drivers?
[[COLOR=#000000]http://manpages.ubuntu.com/manpages/.../radeon.4.html[/COLOR]]("http://manpages.ubuntu.com/manpages/jaunty/man4/radeon.4.html")

It's already installed. If you want reassurance that this is so, open a terminal and run this command:

```
sudo lshw -C video
```

You'll be prompted for your password, but you won't see anything echoed to the screen when you type it in. Don't worry; it is going in. In the output you should see "driver=radeon".

---

### Post by qasmobi on 2011-11-23
ok i will give those a try and post back my findings

---

