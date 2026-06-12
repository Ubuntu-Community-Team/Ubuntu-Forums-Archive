---
title: "Lubuntu live cd won't start into the gui"
date: 2011-06-24
forum: General Help
---

### Post by mojo risin on 2011-06-24
Hi, I bought a magazine because it said it had lubuntu on its disk. <i popped it into a computer(laptop) to try it, but lubuntu for some reason only goes into the first shell. It will switch o the othr shells, but the desktop one stays blank(or rather black) 
Xubuntu and the other buntus on the cd however work allright in their live mode, and fedora from another live cd that was on the magazine also works fine(in fact I am using it right now)
Anybody got an idea why lubuntu isnt working but the other ones are? could it be a manufacturing fault or are there underlying issues? 

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

well I see that it works with my normal computer so it probably isnt a cd error, but rather it seems to be a gnome load issue? But why wouldnt it load when the other buntus have no problem loading it?

---

### Post by jerrrys on 2011-06-24
are you saying that all three came on one cd?  the official releases takes a cd each.  

[http://lubuntu.net/blog/lubuntu-1104-released](http://lubuntu.net/blog/lubuntu-1104-released)

[http://www.xubuntu.org/get](http://www.xubuntu.org/get)

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by jlapier on 2011-06-30
It was probably a DVD that came with a magazine that combined a few different variants. 

In any case, I just wanted to point out that I had the same problem with Lubuntu 11.04, downloading the ISO and burning it myself. When I booted up, it just went to a console session. I shut it down and then looked around for a solution, then decided I'd best first check the CD for errors and then try booting again and check the X logs to see if I could find any interesting error messages. After checking the CD, I booted it again and on the second try it just went straight into the GUI. 

So I guess I would suggest trying it a few times (and if you consistently cannot get a GUI, maybe check the X11 logs).

---

