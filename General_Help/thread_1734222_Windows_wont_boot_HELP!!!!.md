---
title: "Windows wont boot HELP!!!!"
date: 2011-04-20
forum: General Help
---

### Post by RKEEP on 2011-04-20
HELP I had ubuntu 10.10 installed on my hard drive on a seperate partition from my main windows XP partition. But then when, for some weird reason i tryed to boot up ubuntu and it would'nt work. So i went to windows Disk Management and deleted the ubuntu partition. I then rebooted and it said could not find partition. The first thought i had was that it was the grub boot-loader had been on that partition and so i reinstalled ubuntu and went to go back to windows but when i try to boot windows it comes up in the boot loader but go's black screen for about a second and then just automatically go's back to the boot-loader.
I dont have internet on the Computer that the situation is on and I'm writing this on my laptop. When i boot ubuntu though it works fine and everything seems fine and the windows drive is still there when I mount the windows partition but I dont know if when I installed ubuntu, I might of accidentally put the boot-loader somewhere its not supposed to be. Please help. I would keep ubuntu there and install heaps of plugins and programs etc but cant as i dont have access to the internet on that computer so i cant listen to any of my music or my files and programs please help.

---

### Post by ashickur.noor on 2011-04-20
> **RKEEP said:**
> HELP I had ubuntu 10.10 installed on my hard drive on a seperate partition from my main windows XP partition. But then when, for some weird reason i tryed to boot up ubuntu and it would'nt work. So i went to windows Disk Management and deleted the ubuntu partition. I then rebooted and it said could not find partition. The first thought i had was that it was the grub boot-loader had been on that partition and so i reinstalled ubuntu and went to go back to windows but when i try to boot windows it comes up in the boot loader but go's black screen for about a second and then just automatically go's back to the boot-loader.
I dont have internet on the Computer that the situation is on and I'm writing this on my laptop. When i boot ubuntu though it works fine and everything seems fine and the windows drive is still there when I mount the windows partition but I dont know if when I installed ubuntu, I might of accidentally put the boot-loader somewhere its not supposed to be. Please help. I would keep ubuntu there and install heaps of plugins and programs etc but cant as i dont have access to the internet on that computer so i cant listen to any of my music or my files and programs please help.
Try to fix MBR from win 7 dvd. Then fix the grub. Hope it will help.

---

### Post by RKEEP on 2011-04-20
would i use the Win 7 disk because it is windows xp??? thanks so much :D

---

### Post by ndefontenay on 2011-04-20
It's worth a try. It won't destroy your partition if it fails and you can always try again with a win xp CD later on.

---

### Post by RKEEP on 2011-04-20
So what exactly do i do i dont have the windows 7 disk and knowing from the past when I insert the windows xp disk it just gets rid of the bootloader and cant boot from anywhere?? My windows xp disk is only just an iso burnt onto a disk not the original disk. can i fix the MBR from the ubuntu live CD?

---

### Post by ashickur.noor on 2011-04-20
> **RKEEP said:**
> So what exactly do i do i dont have the windows 7 disk and knowing from the past when I insert the windows xp disk it just gets rid of the bootloader and cant boot from anywhere?? My windows xp disk is only just an iso burnt onto a disk not the original disk. can i fix the MBR from the ubuntu live CD?
Try googling how to fix MBR of win XP using win xp cd. If you don't have a original disk it's seems not to be metter.

---

### Post by RKEEP on 2011-04-20
yeah ive searched that but last time i tryed that it just got rid of everything on my hard drive.I think im just gonna back all the stuff up from ubuntu then just create one big partition and split it off using wubi though :D

---

### Post by dragonfly41 on 2011-04-20
Although I've recently used command line from recovery disc to fix mbr (Vista dual boot)

bootrec /fixmbr
bootrec /fixmbr

I've read that you can use [COLOR=Navy]ms-mys[/COLOR] from LiveCD to fix mbr

> 
can i fix the MBR from the ubuntu live CD?



[http://www.linux-geek.co.nz/2011/04/17/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.linux-geek.co.nz/2011/04/17/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)


[http://ubuntuforums.org/showthread.php?t=1009707&highlight=ms-sys](http://ubuntuforums.org/showthread.php?t=1009707&highlight=ms-sys)

---

### Post by RKEEP on 2011-04-20
Thanks so much i just got the original ubuntu cd and did that and it works fine thanks soo much :D

---

### Post by Mark Phelps on 2011-04-21
> **nullifygirls said:**
> sir please suggest me solution for my problem.

According to your original post, you want help setting up dual boot -- which is NOT the topic of this thread.

Please don't hijack someone else's thread for your own problem;  instead, start your own thread.

thanks

---

