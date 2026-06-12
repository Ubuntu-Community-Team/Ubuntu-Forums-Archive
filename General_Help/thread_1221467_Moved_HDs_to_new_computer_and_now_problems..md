---
title: "Moved HDs to new computer and now problems."
date: 2009-07-23
forum: General Help
---

### Post by xeddog on 2009-07-23
Hi all,

My backup computer blew up on me a few days ago and so I went out and bought some new stuff (Intel i7-920, 6GB ram, new 1TB Hitachi SATA2 disk drive, and a Intel GeForce 9500GT video card).  I played musical computers for an entire day moving all the hardware around in three computers, but I am only having problems with my new backup machine.  

I took out the guts from what was my primary computer and put them in the case the backup was in.  (Pentium-4 motherboard, 3 Ghz cpu, 1GB memory, and two IDE disk drives).  On sda was my Jaunty that I use(d) all the time, and on sdb was a Jaunty install that I upgraded with Karmic to play with.  Both of those were working fine when I took them out.  I also added a third drive (sdc) with a windows 7 installation on it.  

The only two differences in the old and new setups are the addition of the third disk drive, and the biggee seems to be changing from a ATI 9550 AGP graphics card to an nVidia Ge5200 PCI card.

The Jaunty that was installed on sda booted and is now working fine.  It took care of all the drivers all by itself.  I have also finagled the menu.lst file and have the Windows 7 install on sdc working (need to update a couple of drivers but it works).  My problem is the Karmic install on sdb.  It ain't happy anymore and I cannot get it to boot.  Not even the recovery mode.  I don't think it can handle the new graphics card because some of the last messages that appeared on the monitor had to do with agppart or something like that.  Anyway, it looks like it was still trying to use the old ATI graphics card and puking because it wasn't there.  I would have included the messages but I cannot find them.

So my questions are:
1.  Is there a way I can remove the ATI driver from the karmic installation on sdb and install the nVidia driver by using the live cd or . . .????  I don't want to do a clean install just yet if I don't have to but I realize that it is probably going to be necessary.
2.  Where would all of those boot messages be located.  I looked through /var/log on sdb and nothing in there was dated later that 7/12/2009 which is the last time I booted that disk in the old configuration.  Of course, on sda everything is for the current boot.


TIA,

xeddog

---

### Post by synapsys on 2009-07-23
Karmic is still in alpha... having installed it, you should be fully prepared to re-install at any time.

---

### Post by xeddog on 2009-07-25
> Karmic is still in alpha... having installed it, you should be fully prepared to re-install at any time. 

Yeah, I'm well aware of Karmic's alpha status.  And I realize that I may indeed have to re-install it.  But the real reason is that there is "other" stuff on the drive that I am just not sure if I want to erase it yet.  One of those situations where I am 95% certain that there is nothing left that I have not backed up somewhere else, but this time I just can't get myself to let go of that other 5%.  :-)  I can mount the drive on my Jaunty install, go through it all, and make sure what I want is backed up.  But it will take me a while to go through it all.  I was also sorta hoping to make a learning experience out of this too.  

Which brings up a third question.  Is there a way to install karmic again WITHOUT formatting??  

xeddog

---

