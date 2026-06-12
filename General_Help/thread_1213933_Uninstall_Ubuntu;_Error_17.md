---
title: "Uninstall Ubuntu; Error 17"
date: 2009-07-15
forum: General Help
---

### Post by jonathan.david.lim on 2009-07-15
All right, here's the deal. I don't want Ubuntu anymore. I used my system's recovery discs to try and reinstall Windows, but now every time I try to turn the damn thing on, I get Error 17'd. I don't want Ubuntu in a partition, I don't want to dual boot, I just want it off my hard drive. Why can't I format this stupid thing? Ubunut is a virus, as far as I'm concerned.

---

### Post by prem1er on 2009-07-15
1. Put the windows cd in when the computer is on.
2. Power off the computer
3. Power on the computer
4. At the bios screen select to boot from the CD
5. You will boot off the windows cd and avoid the grub error.
6. Install windows.

Enjoy Vista!

---

### Post by prem1er on 2009-07-15
didn't mean to post.

---

### Post by windy81 on 2009-07-15
i'm having the same problem matey... [http://ubuntuforums.org/showthread.php?t=1213911](http://ubuntuforums.org/showthread.php?t=1213911)

its the grub boot loader that will not, go away.

even after formatting the damn thing remains.

you are in a more difficult position thatn me though since you loaded it on you internal hard drive..

i hope a solution is found.

---

### Post by prem1er on 2009-07-15
This isn't an "Ubuntu wide problem", it is a mistake YOU have made in trying to remove Ubuntu.  It means that grub is trying to load a partition that no longer exists.

---

### Post by xd397 on 2009-07-15
I had a similar problem once. I believe you need to open a terminal and tell it to fdiskmbr basically. I have not done this for a while so I may be wrong

---

### Post by windy81 on 2009-07-15
well ubuntu has given me nothing but problem, i want to remove it completely, i am no programmer, and i do not understand the internals of Ubuntu.

i have formatted my external hard drive and thats about all i know how to do.

i have also run fixmbr in recovery mode in my windows xp, and the problem persists.

so you saying that i have made a mistake is probably a mistake many people will make and as such it should be addressed.

if u want to flame for the sake of it, carry on.

---

### Post by Slim Odds on 2009-07-15
> **windy81 said:**
> so you saying that i have made a mistake is probably a mistake many people will make and as such it should be addressed.

if u want to flame for the sake of it, carry on.

The only way to "address the problem" is to understand the problem. This was explained to you. If you want to continue to believe that this is an "Ubuntu problem", you may. But it's not.

Computers are very complicated. Since most people buy them with the OS already installed, they sometimes forget this.

You simply need to boot from the Windows CD and let it have whatever control of your computer that you want it to have. It's really not that hard and Ubuntu has nothing to do with it.

If this is beyond your skill level, you may need to get someone to help you.

---

### Post by hyperdude111 on 2009-07-15
To restore the windows bootloader.

[http://www.neowin.net/forum/lofiversion/index.php/t292614.html](http://www.neowin.net/forum/lofiversion/index.php/t292614.html)

---

### Post by windy81 on 2009-07-15
> **Slim Odds said:**
> The only way to "address the problem" is to understand the problem. This was explained to you. If you want to continue to believe that this is an "Ubuntu problem", you may. But it's not.

Computers are very complicated. Since most people buy them with the OS already installed, they sometimes forget this.

You simply need to boot from the Windows CD and let it have whatever control of your computer that you want it to have. It's really not that hard and Ubuntu has nothing to do with it.

If this is beyond your skill level, you may need to get someone to help you.

ok so 

i did install grub on the external hard drive. Thats it's last knows location.

i have restored mbr  by entering recovery mode and running fixmbr in xp

i have formatted the external hard drive.



so why is grub still coming up ? where is it ? i don't understand this what so ever. it was. like i said, on the external hard drive so why, after formatting is it still there ?

---

### Post by windy81 on 2009-07-15
**fdisk /mbr is **for windows98 not xp.... the same command in xp is fixmbr which i have already done.

---

### Post by windy81 on 2009-07-15
> **Slim Odds said:**
> 
This was explained to you. If you want to continue to believe that this is an "Ubuntu problem", you may. But it's not.



i have to disagree, if ubuntu cannot be un-installed properly and easily, by the likes of people like me who are not in a status-quo situation with the workings of the ubuntu, then it is a buntu wide problem.

Ubuntu as far as i can tell is meant to appeal to the wider public, so it should be sorted out.

---

### Post by zhurai-tsuki on 2009-07-15
> **windy81 said:**
> i have to disagree, if ubuntu cannot be un-installed properly and easily, by the likes of people like me who are not in a status-quo situation with the workings of the ubuntu, then it is a buntu wide problem.

Ubuntu as far as i can tell is meant to appeal to the wider public, so it should be sorted out.

just put in Windows CD
boot into Windows CD (unless your BIOS fails enough to not boot it)
install Windows, formatting over all the other partitions
Windows installed, Ubuntu gone

"status-quo situation" <-- how did you install ubuntu over those partitions (that 98/ME/2000/XP/Vista/7/DOS/whatever was in control of) if you didn't get that you can just write over it all with another CD (in this case, Windows install CD)

---

### Post by prem1er on 2009-07-15
Close this thread. He has been given multiple answers that would solve his problem.  Trolling.

---

### Post by windy81 on 2009-07-15
> **prem1er said:**
> Close this thread. He has been given multiple answers that would solve his problem.  Trolling.

no i have not been given any answers, i am not trolling. 

none of the answers have helped me. 

all i can do is re install windows xp, and see if that works.

as for you you should get off your pedestal. Christ almighty get over yourself.

---

### Post by windy81 on 2009-07-15
> **zhurai-tsuki said:**
> just put in Windows CD
boot into Windows CD (unless your BIOS fails enough to not boot it)
install Windows, formatting over all the other partitions
Windows installed, Ubuntu gone

"status-quo situation" <-- how did you install ubuntu over those partitions (that 98/ME/2000/XP/Vista/7/DOS/whatever was in control of) if you didn't get that you can just write over it all with another CD (in this case, Windows install CD)

i did a clean install of Ubuntu and grub on the external hard drive (dev/sdb) 
That's all i did.

---

### Post by Slim Odds on 2009-07-15
Can you boot from the Windows CD?

If so, then you be OK from there.

Otherwise, take your computer to the shop.

---

### Post by Slyder0244 on 2011-01-14
Was there ever a solution for removing grub from an external drive? I just put an old laptop drive into an external enclosure, and it had both XP and Ubuntu on it. I formatted the drive, but I keep getting a grub error when I boot up now. I know I can just set it up to not boot from external drives, but I'd rather remove the root of the problem which is grub.

---

