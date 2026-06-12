---
title: "Big problem, running out of solutions."
date: 2011-01-07
forum: General Help
---

### Post by mrsteeve on 2011-01-07
Before I begin, here are some computer specs:

Toshiba Satellite C655
2 GB Ram
250 GB HDD
Intel Celeron 900 Joules / 2.2 GHz
64 bit


So, a little backstory. For christmas I got a new laptop with Windows 7, and while Win7 is a good operating system, I wanted to try Ubuntu and see which one I liked better. I installed the 32 bit version, because I understand people run 32 bit Ubuntu on 64 bit machines with out problems. For the first few days, everything was going amazing and I was pretty much using only Ubuntu (I had a dual boot with WIn7). One day, I opened my lid to find that the log in screen wouldn't appear, so I restarted.

I wish I could remember what error I got, but everytime grub tried to load Ubuntu, it wouldn't load, it just gave me some error (it may have been a kernel panic, not sure). So I went into windows, burned a windows repair disc, and fixed the MBR to be the windows boot loader instead of grub, then deleted the Ubuntu partition. Shortly after, I tried the 64 bit Ubuntu installation, and it wouldn't even boot up after the first boot (unfortunately, can't remember the error I got then either). So I repeated the MBR fix for Windows, and just stuck with Windows for a while. However, a new problem arose. Every now and then (and in time, more frequently) everything would freeze, for 1 to 2 seconds. It couldn't have been my RAM or anything, the computer was blazing fast when I got it. The windows boot also took much much longer than usual, until it just wouldn't boot at all. I had my father (who's much more knowledgeable at computers) to do something, and he loaded into an earlier recovery partition ran a program called CCleaner, which supposedly fixed it. However, the problem was still there, and it got worse. I tried CHKDSK, it didn't do anything. The random freeze ups kept happing more frequently and became more and more bothersome. Eventually my computer just wouldn't boot up, it would just be a blank screen after the 'Toshiba' logo.

I eventually called Toshiba and they said that I apparently deleted the original recovery partition, and needed a Windows install disc, which I don't have so I have to buy one. Until then, I decided to just do a complete install of Ubuntu (64 bit), since I figured if I just did a complete fresh install removing everything, it would fix it. Well, turns out it had the same freeze up problem. I then tried a clean install of 32 bit Ubuntu. No luck, still periodical freeze ups, sometimes if the freeze ups are longer the screen will go grey. Before all this mess Ubuntu ran perfectly. I'm fearing that it may be my hard drive that's the problem, but I'm not  entirely sure.

So, is there anything I can do to restore my laptop to full health with out buying a new hard drive? Unless the hard drive isn't the problem, but I don't see what else is. Thanks.

EDIT:

I tried memtest. Here are the results:

[IMG]http://i.imgur.com/ZAv4Sl.jpg[/IMG]

It says 'Pass complete, no errors'. What do you guys think?

---

### Post by binoplaza on 2011-01-07
Did you check your manufacturer's website for BIOS updates?

---

### Post by binoplaza on 2011-01-07
Did you check your manufacturer's website for BIOS updates?

---

### Post by tgm4883 on 2011-01-07
> **mrsteeve said:**
> Before I begin, here are some computer specs:

Toshiba Satellite C655
2 GB Ram
250 GB HDD
Intel Celeron 900 Joules / 2.2 GHz
64 bit


So, a little backstory. For christmas I got a new laptop with Windows 7, and while Win7 is a good operating system, I wanted to try Ubuntu and see which one I liked better. I installed the 32 bit version, because I understand people run 32 bit Ubuntu on 64 bit machines with out problems. For the first few days, everything was going amazing and I was pretty much using only Ubuntu (I had a dual boot with WIn7). One day, I opened my lid to find that the log in screen wouldn't appear, so I restarted.

I wish I could remember what error I got, but everytime grub tried to load Ubuntu, it wouldn't load, it just gave me some error (it may have been a kernel panic, not sure). So I went into windows, burned a windows repair disc, and fixed the MBR to be the windows boot loader instead of grub, then deleted the Ubuntu partition. Shortly after, I tried the 64 bit Ubuntu installation, and it wouldn't even boot up after the first boot (unfortunately, can't remember the error I got then either). So I repeated the MBR fix for Windows, and just stuck with Windows for a while. However, a new problem arose. Every now and then (and in time, more frequently) everything would freeze, for 1 to 2 seconds. It couldn't have been my RAM or anything, the computer was blazing fast when I got it. The windows boot also took much much longer than usual, until it just wouldn't boot at all. I had my father (who's much more knowledgeable at computers) to do something, and he loaded into an earlier recovery partition ran a program called CCleaner, which supposedly fixed it. However, the problem was still there, and it got worse. I tried CHKDSK, it didn't do anything. The random freeze ups kept happing more frequently and became more and more bothersome. Eventually my computer just wouldn't boot up, it would just be a blank screen after the 'Toshiba' logo.

I eventually called Toshiba and they said that I apparently deleted the original recovery partition, and needed a Windows install disc, which I don't have so I have to buy one. Until then, I decided to just do a complete install of Ubuntu (64 bit), since I figured if I just did a complete fresh install removing everything, it would fix it. Well, turns out it had the same freeze up problem. I then tried a clean install of 32 bit Ubuntu. No luck, still periodical freeze ups, sometimes if the freeze ups are longer the screen will go grey. Before all this mess Ubuntu ran perfectly. I'm fearing that it may be my hard drive that's the problem, but I'm not  entirely sure.

So, is there anything I can do to restore my laptop to full health with out buying a new hard drive? Unless the hard drive isn't the problem, but I don't see what else is. Thanks.

I cal

Run a memtest from the Ubuntu CD. If it's a new machine and you have bad hardware you should be under warranty.

---

### Post by MrDetermination on 2011-01-07
You can download an ISO from MS for the type of Windows license you have (the sticker on the laptop).

Your problem is likely hardware related as you're having stability issues in Windows and Ubuntu.  Run memtest to rule out memory; run that with the laptop sitting on a flat clean table.  If that runs stable overnight then it isn't your memory and isn't likely your power supply or processor.  That leaves heat and hard drive.

Are you running on your lap or on a clean flat hard surface?  Does the machine get hot when running?  Does it run stable for a while when you first start using it for a day?

My advice is remove all partitions on the drive and do a completely fresh install of something, anything, so you know you have a "clean" OS and can rule that out.  Try to run in a cool room on a flat surface and check to see if it still gets hot.

Here is a good place to start if you still think it might be the hard drive:
[http://www.myharddrivedied.com/about_recovery_services.html](http://www.myharddrivedied.com/about_recovery_services.html)

---

### Post by electroken on 2011-01-07
I am not a real expert but it could be your ram no matter how new it is. In shipping laptops the bouncing they get could have loosened one of your ram sticks. I guess my first try would be to open up the trap door over the ram and reseat each of the ram sticks. You have nothing to lose doing it but take cautions for static especially this time of year. If you can get into the bios of the laptop then you can at least find out if the system is seeing the hard drive correctly etc.
If you have already tried a full install of ubuntu and have overwritten windows by doing so, then you have little to lose by trying it again. I think I would try to use a 64 bit version of ubuntu. I am also told at this point in time, that it is wiser to install using 10.04 and not 10.10 until there is more evaluation of the new os.
I am of the opinion that your issues with the computer are hardware and perhaps nothing at all was wrong with either installation. Sorry not much more help than that.

---

### Post by electroken on 2011-01-07
I am not a real expert but it could be your ram no matter how new it is. In shipping laptops the bouncing they get could have loosened one of your ram sticks. I guess my first try would be to open up the trap door over the ram and reseat each of the ram sticks. You have nothing to lose doing it but take cautions for static especially this time of year. If you can get into the bios of the laptop then you can at least find out if the system is seeing the hard drive correctly etc.
If you have already tried a full install of ubuntu and have overwritten windows by doing so, then you have little to lose by trying it again. I think I would try to use a 64 bit version of ubuntu. I am also told at this point in time, that it is wiser to install using 10.04 and not 10.10 until there is more evaluation of the new os.
I am of the opinion that your issues with the computer are hardware and perhaps nothing at all was wrong with either installation. Sorry not much more help than that.

---

### Post by electroken on 2011-01-07
I am not a real expert but it could be your ram no matter how new it is. In shipping laptops the bouncing they get could have loosened one of your ram sticks. I guess my first try would be to open up the trap door over the ram and reseat each of the ram sticks. You have nothing to lose doing it but take cautions for static especially this time of year. If you can get into the bios of the laptop then you can at least find out if the system is seeing the hard drive correctly etc.
If you have already tried a full install of ubuntu and have overwritten windows by doing so, then you have little to lose by trying it again. I think I would try to use a 64 bit version of ubuntu. I am also told at this point in time, that it is wiser to install using 10.04 and not 10.10 until there is more evaluation of the new os.
I am of the opinion that your issues with the computer are hardware and perhaps nothing at all was wrong with either installation. Sorry not much more help than that.

---

### Post by mrsteeve on 2011-01-07
Also, when I was installing Ubuntu after all the bad stuff happened, I hit the more details button that showed what the terminal was doing during the installation, I browsed up and it said that the hard drive had a bad sector on it.

---

### Post by mrsteeve on 2011-01-07
> You can download an ISO from MS for the type of Windows license you have (the sticker on the laptop).

Your problem is likely hardware related as you're having stability issues in Windows and Ubuntu. Run memtest (free bootable iso) to rule out memory; run that with the laptop sitting on a flat clean table. If that runs stable overnight then it isn't your memory and isn't likely your power supply or processor. That leaves heat and hard drive.

Are you running on your lap or on a clean flat hard surface? Does the machine get hot when running? Does it run stable for a while when you first start using it for a day?

My advice is remove all partitions on the drive and do a completely fresh install of something, anything, so you know you have a "clean" OS and can rule that out. Try to run in a cool room on a flat surface and check to see if it still gets hot.

The problems start right once it boots up. I believe it gets hot after a while, but the freeze ups happen almost immediately. Also, when I did the full install of Ubuntu at the end, it deleted all the remaining partitions and created a brand new one. Then on the first boot, the problems were there.

---

### Post by mrsteeve on 2011-01-07
Sorry for the multiple posts, computer screwing up.

---

### Post by mrsteeve on 2011-01-07
deleted because it's another multi-post

---

### Post by tgm4883 on 2011-01-07
I think it's the forums, I've been having some trouble with them today too

---

### Post by electroken on 2011-01-07
I am not a real expert but it could be your ram no matter how new it is. In shipping laptops the bouncing they get could have loosened one of your ram sticks. I guess my first try would be to open up the trap door over the ram and reseat each of the ram sticks. You have nothing to lose doing it but take cautions for static especially this time of year. If you can get into the bios of the laptop then you can at least find out if the system is seeing the hard drive correctly etc.
If you have already tried a full install of ubuntu and have overwritten windows by doing so, then you have little to lose by trying it again. I think I would try to use a 64 bit version of ubuntu. I am also told at this point in time, that it is wiser to install using 10.04 and not 10.10 until there is more evaluation of the new os.
I am of the opinion that your issues with the computer are hardware and perhaps nothing at all was wrong with either installation. Sorry not much more help than that.

---

### Post by zealibib slaughter on 2011-01-07
If your hard drive is failing (yes even new ones go bad) then this may be the problem.  Load a ubuntu live cd and boot from it.  Then go to system-administration-disk utility and view the SMART values for your hard drive.  This should tell you if there is something going wrong with the drive.  I've had this problem many times with some of my older hardware and it almost always turns out to be a bad drive.

---

### Post by mrsteeve on 2011-01-07
Edited my first post with the memtest results picture. What do you guys think?

---

### Post by mrsteeve on 2011-01-07
Edited my first post with the memtest results picture. What do you guys think?

---

### Post by binoplaza on 2011-01-07
> **mrsteeve said:**
> Edited my first post with the memtest results picture. What do you guys think?

Picture is not so clear, not sure if it's completed yet?
If there are no error's you have nothing to worry about concerning your ram.

---

