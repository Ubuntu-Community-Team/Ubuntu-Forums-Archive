---
title: "Repetitive Try/Install Screen, Installed 2 times"
date: 2011-06-11
forum: General Help
---

### Post by Starloric on 2011-06-11
Greetings all! 
I am a COMPLETE noob to the world and functionality of Linux/Ubuntu. I've been pondering the switch from 7 to Ubuntu for a while and made my decision today :p 
However, there are a few... Kinks in the process. 
I burned a disk with Ubuntu on it, put it in and used the "try" function. I spent a couple hours on it and liked it. I decided to hit the install button on the desktop, it all went smoothly. It froze during the "logging off" process, so I cold booted it. Upon restart, I was prompted again to try/install Ubuntu. (Again, I've already installed it, or so I think...)
Well, what the heck. I install it again, it freezes and I let it be. I come back to find it, once again, on the try/install screen. I'm currently on the "try" function again.
How do I cure my lack of an installed copy of Ubuntu? D: Please help!

---

### Post by wildmanne39 on 2011-06-11
> **Starloric said:**
> Greetings all! 
I am a COMPLETE noob to the world and functionality of Linux/Ubuntu. I've been pondering the switch from 7 to Ubuntu for a while and made my decision today :p 
However, there are a few... Kinks in the process. 
I burned a disk with Ubuntu on it, put it in and used the "try" function. I spent a couple hours on it and liked it. I decided to hit the install button on the desktop, it all went smoothly. It froze during the "logging off" process, so I cold booted it. Upon restart, I was prompted again to try/install Ubuntu. (Again, I've already installed it, or so I think...)
Well, what the heck. I install it again, it freezes and I let it be. I come back to find it, once again, on the try/install screen. I'm currently on the "try" function again.
How do I cure my lack of an installed copy of Ubuntu? D: Please help!Hi, first when you reboot or just shut down after install you need to remove the cd or it will boot to it again. Now how did you install it the second time? completely over the top of the other one by reformatting the partitions or along side? Boot up with the livecd choose try mode and run this script and post the information from this script so we can see what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read. It is possible if you remove the cd and reboot it will boot up, but it would be better to make sure you have not taken up a lot of extra space by creating more partitions then you need if it installed it twice.

---

### Post by Starloric on 2011-06-11
Oh wow, I'm facepalming pretty hard. My issue was having the disk in a second time. That should have been dead obvious!  ](*,)

---

### Post by wildmanne39 on 2011-06-11
> **Starloric said:**
> Oh wow, I'm facepalming pretty hard. My issue was having the disk in a second time. That should have been dead obvious!  ](*,)
Hi, you should still at least look at your partitions with gparted and make sure it did not install twice side by side. Would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **Starloric said:**
> Oh wow, I'm facepalming pretty hard. My issue was having the disk in a second time. That should have been dead obvious!  ](*,)

Here are couple of handy guides as well if you are new:

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

