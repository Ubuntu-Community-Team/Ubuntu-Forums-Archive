---
title: "ubuntu Update and computer restart fail"
date: 2011-02-22
forum: General Help
---

### Post by amin2084 on 2011-02-22
Hello,

I've a problem with my ubuntu. Im using ubuntu 10.10 installed alongside Windows XP (Dual Booting). When i install update for ubuntu, the computer need to restart to complete the update. But when i restart the computer, the computer stuck on ist screen (image attached below) and fail to boot. i've trying to restart the computer several time but still fail. anyone can help me to solve this problem other than formating the hard disk?
[ATTACH]184125[/ATTACH]
please help me.:confused:

---

### Post by sanderd17 on 2011-02-22
you don't even get to the grub screen?

I assume that you don't use WUBI, if you do, say it. WUBI needs completely different solutions.

Te first thing you can try s to reinstall GRUB. Burn a live CD (or USB) and check out this thread: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) point 13.

If you get errors in some step, or don't succeed, don't continue but ask help.

If you don't have a backup, you can use the live CD to create one. Do this before you proceed.

---

### Post by amin2084 on 2011-02-22
hi sanderd,
yes i dont even get to the grub screen and im not using WUBI installing linux.
i've try with live cd of ubuntu but the same thing happen and cannot press any key as in the picture like it is hang. so cannot boot from live cd. the black screen didnt appear at all.

---

### Post by sanderd17 on 2011-02-22
Then I think it is a hardware failiure. Ubuntu isn't able to break your system like that.

---

### Post by amin2084 on 2011-02-22
oh no! its too bad to back up everything and reinstalling its once again. :( anyway thanks for your help sanderd. i will try to find the solution first before format it.

---

### Post by sanderd17 on 2011-02-22
Are you able to frormat it? if so, how do you do it?

---

### Post by amin2084 on 2011-02-22
i cannot format it with the same computer but i will format the hardisk with another computer. but im not sure whether i can reinstall it using the computer or not. any suggestion. because i've try detached the OS hd and put another hd without any OS but the same problem still happen.

---

### Post by sanderd17 on 2011-02-23
The hardware failiure is probably not your HDD, but your motherboard. You will have to take it to a local repair service.

---

### Post by amin2084 on 2011-02-23
Ok, the problem nearly solved but i still cannot figure out what is the source of the problem.
i have try to clear the CMOS by removing the MOBO battery and check the HDD error with another machine and try to open the machine with OS installed on my HD. The HD is good and nothing error and i can open the system using another machine. And then i attached it back to my machine and open it and gladly it working now. but now the problem is i cannot connect to the internet using Windows XP OS. Windows XP ask me to activate the product first before log in.
After that i try to connect internet with my ubuntu OS. and its internet connection working with ubuntu. so what this mean? :)

~A liitle happy now~ :)

---

