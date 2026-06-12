---
title: "Interlaced Windows!"
date: 2009-12-07
forum: General Help
---

### Post by DUXBOX on 2009-12-07
Hello everyone,

I just did a clean install of the latest Ubuntu 9.10 on my T42 ThinkPad for the second time and everything seems to be working properly except for some windows and the pop-up notification that appear kinda interlaced.

eg. The following is a screenshot of the "System Monitor" windows.

[http://i47.tinypic.com/30htpau.png](http://i47.tinypic.com/30htpau.png)

I am totally new to Linux and Terminal Commands and I would appreciate any help from this group :)

:popcorn:

---

### Post by JBAlaska on 2009-12-07
Have you installed the video driver in System, Administration, Hardware Drivers?

---

### Post by DUXBOX on 2009-12-07
> **JBAlaska said:**
> Have you installed the video driver in System, Administration, Hardware Drivers?

Thanks for the quick response. :)

No, I didn't install any drivers. I thought Ubuntu detected everything automatically as colors seems to be fine and I can watch movies with no issue.

However, when I click the Hardware Drivers from System > Administration I get the following:

"no proprietary drivers are in use on this system"

Any ideas? Do I have to manually install the video card driver?
Where do I get one, it's ATI Radeon I think, but I am not even sure if I know how to install it under ubuntu!

---

### Post by DUXBOX on 2009-12-11
Anyone?

---

### Post by sabre2th on 2009-12-11
I like your desktop background  ;)

In my personal experiences and from what I've read on here, ATI graphics are hairy at best right now.  As long as you don't need 3d acceleration, your best bet is generally the default driver, which I assume is already being used...

If you did want to try to install the proprietary ATI driver, the best place to get it would be their website.  Link here: [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Again, though, I wouldn't recommend it right now.  I've heard nightmarish stories about Karmic and ATI.

Is everything on your system up to date?

---

### Post by joes7 on 2009-12-11
LiveCD's Repair Console.

---

### Post by DUXBOX on 2009-12-12
> **sabre2th said:**
> I like your desktop background  ;)

In my personal experiences and from what I've read on here, ATI graphics are hairy at best right now.  As long as you don't need 3d acceleration, your best bet is generally the default driver, which I assume is already being used...

If you did want to try to install the proprietary ATI driver, the best place to get it would be their website.  Link here: [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Again, though, I wouldn't recommend it right now.  I've heard nightmarish stories about Karmic and ATI.

Is everything on your system up to date?


That "nice background" is supposed to be Ubuntu's System Monitor that I miss badly. :)

Ubuntu is updated to the latest... I keep running the system update just hopping for a magic patch to fix this issue, but so far no luck!

It's funny that everything else works just fine. I watch movies, surf the internet, use open office and etc... with no issue, only some specific applications like system monitor and some games, also that wifi notification pop up message appear interlaced!

is there a way to reinstall the default video driver again?

---

### Post by DUXBOX on 2009-12-12
> **joes7 said:**
> LiveCD's Repair Console.


I have the 9.04 Ubuntu DVD but I have already upgraded the system to 9.10, so my questions are:

1- Can I use the 9.04 DVD to repair the current version?
2- How do I do a repair? Does it have a graphic interface like windows that I can select the appropriate option and repair the OS or do I have to enter some commands?

Thanks in advance

---

### Post by bigsmitty64 on 2009-12-12
1) You can download the live cd for 9.10 here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

 2) If I remember correctly, it is a graphical interface with a repair option.

---

### Post by DUXBOX on 2009-12-12
> **bigsmitty64 said:**
> 1) You can download the live cd for 9.10 here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

 2) If I remember correctly, it is a graphical interface with a repair option.


Great! It is going to take a while to download this thing but I will give it a shot and hopefully it will fix the issue. I don't want to go back to Windows anymore! :)


Thanks again for your help,

---

### Post by efflandt on 2009-12-12
I believe that has something to do with amount of video RAM (32 MB or less), but have not able to find the solution that I had seen somewhere (something to add to xorg.conf).  I had that problem one one old computer with ATI video, but I think I resolved it by using xorg-driver-fglrx.

---

