---
title: "Dell C400"
date: 2010-04-12
forum: General Help
---

### Post by OZFive on 2010-04-12
I just recently came into possession of a Dell C400 and I decided to set it up for the kids to use as a netbook type computer.

I Installed Xbuntu 9.10 on it today.  As this machine does not come with a CD/DVD drive and I do not want to invest money in something I got for free.  So I installed it in another computer which went well enough.  Then transfered the HD to the new machine.  

Now before you say.. there is the problem, it is not.  I had done this already with a previous copy of Xubuntu Hardy that did this well.  But after I went to 9.10 through Update Manager, a flickering screen came up.  The desktop was visible but shifted and flickering.

So I thought something must have gone wrong with the install.  So I DL'ed a copy fo Xubuntu 9.10, installed it, transferred the HD, and I got the same issue.

Any ideas at all.  I am not holding my breath.

---

### Post by Jose Catre-Vandis on 2010-04-12
I reckon Ubuntu has got too clever for itself, and is being more discerning about the hardware switch.

When you get to grub, edit your default boot entry to remove quiet and splash, this should allow you to have a command line prompt. (?)

Back up your existing /etc/X11/xorg.conf and then try reconfiguring your xorg:
```
sudo dpkg-reconfigure xserver-xorg
```

Alternately

Have you got a USB port on the C400 and a spare USB stick? If so , i suggest you create a USB install and go from there.

or you could splash out on an external CD Rom drive for £13:
[http://www.ukclearancecentre.co.uk/192-dell-c400-external-cd-rom-drive.html](http://www.ukclearancecentre.co.uk/192-dell-c400-external-cd-rom-drive.html)

---

### Post by terrrorr on 2010-04-12
Hi,

I assume that you have some sort of display driver problem. It sounds that your Dell is pretty old and you cannot install or boot from USB stick (as you may know, there is a tool called USB Start Up Creator in System->Administration which could be used to create bootable USB stick) so this option is not possible.

What I would do:

1. Install SSH server so I could use terminal remotely
2. Follow these instructions:
[https://help.ubuntu.com/community/Video]("https://help.ubuntu.com/community/Video")

I hope this will solve your problem

---

### Post by krazyjvc on 2010-04-14
Hi OZFive,
I'm also in possession of a Dell C400 since intrepid and have always upgraded (not a new install), the only really stone in the shoe this netbook has is it cant boot from usb. But since i have WinXP in it, the 1st time i installed Ubuntu in it was with this awesome tool.
[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

All you have to do is run it and choose which flavor you want to install. Select the C:\ drive and restart. it will copy the CD files to the harddisk and then you can install (X)ubuntu as if you were installing from a real CD.

give it a try and then post here the results :)
Good luck mate.

---

### Post by OZFive on 2010-04-15
Ok I got a media cable and a DVD bay so that I might install direct form disc.  Still having the same issue here :(  Not fun I must say.  I tried the reconfigure the xorg and it made no difference.

Let me try to explain it a bit more....

The screen is flickering right from the moment that the Xubuntu Splash comes up and the fancy little fireworks start cycling.  

The screen is also offset to the right, approx by about 30 pixels.

---

### Post by Jose Catre-Vandis on 2010-04-16
Does it flicker with the Dell boot screen or when in bios, or with original OS?

---

### Post by bandoba on 2010-04-17
Hello,

I am yet another user of Ubuntu or XUbuntu 9.10 on DELL C400. I am having exact same issue. The flickering screen shows up only after GDM starts. Also I can use Ctrl+Alt+<n> to go to virtual consoles and the text mode works fine. But as soon I switch back to graphical flickering starts and continues. 

I am in process of trying Puppy and KNOPPIX so that I can use this machine. Right now it is just unusable even if I have working XUbuntu on it.

Would appreciate any help or suggestions to get this fixed.

Thanks!

---

### Post by bandoba on 2010-04-17
I just posted a fix that worked for me. Its no magic, I just did dist-upgrade and I believe that installed correct xserver for me.

I was not able to locate this thread but found another one and hence posted my steps there. Here is the link:
[http://ubuntuforums.org/showpost.php?p=9134172&postcount=9](http://ubuntuforums.org/showpost.php?p=9134172&postcount=9)

Hope it helps. Your original first post gave me confidence that I am not alone in facing this issue and decided to follow it up. So thanks!

BTW, Puppy 4.3.1 (frugal install) works great too.

---

### Post by krazyjvc on 2010-04-19
[https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/542208](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/542208)

---

