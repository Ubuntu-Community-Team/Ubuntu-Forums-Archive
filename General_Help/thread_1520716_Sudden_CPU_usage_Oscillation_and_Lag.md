---
title: "Sudden CPU usage Oscillation and Lag"
date: 2010-06-29
forum: General Help
---

### Post by stressmonkey on 2010-06-29
My CPU usage suddenly started oscillating between 5% and 80% causing the computer to lag very badly. This problem came on suddenly--I was using the computer the night before and then the next day I was hit with the lag.

Computer info:

IBM Lenovo ThinkpadR61 with Ubuntu 10.04 Lucid Lynx
Intel Duo Core 2GHz Processor T7300
2.5GB RAM (2GB Kingston DDR2 + 512MB DDR2 not sure what brand)
Intel Graphics Media Accelerator X3100
Intel 802.11abg wireless

everything was working perfectly until the CPU usage started to spike. It's very strange, spiking every few seconds.

Here is a picture of the System Monitor

[http://picasaweb.google.com/lh/photo/WhrjEXVlDFdWhU0rg0hDUg?feat=directlink]("http://picasaweb.google.com/lh/photo/WhrjEXVlDFdWhU0rg0hDUg?feat=directlink")


[IMG]http://picasaweb.google.com/lh/photo/WhrjEXVlDFdWhU0rg0hDUg?feat=directlink[/IMG]



Any ideas of what the problem could be? Please let me know if you need more information, I will supply as promptly as possible!

Thanks!

---

### Post by mikewhatever on 2010-06-30
Which process was using the CPU?
Install htop, and next time it happens, run it and post the output.

---

### Post by stressmonkey on 2010-06-30
I'm not sure what process was causing the lag--and that is the main problem I suppose...

Even with a reboot, the problem persists.  I also tried running a live version of Ubuntu 10.04 to see if it was a system update or program that was causing the lag, but even under Ubuntu live the CPU spiking continued.  

Could it be a driver update that caused the problem? The only way a driver could have been updated was if the Update Manager installed it. I have not manually installed or tampered with any drivers.


I will install htop tonight and post the output.

---

### Post by stressmonkey on 2010-07-02
OK I installed htop and ran it, I sorted processes by memory and by CPU usage. I did not see any program hogging resources. 


[http://picasaweb.google.com/malikb33/SystemMonitor#]("http://picasaweb.google.com/malikb33/SystemMonitor#")


you can see from the CPU usage between the two htop photos, how it is fluctuating, from high to low. it is such a strange problem.

---

### Post by stressmonkey on 2010-07-02
I just finished doing a clean install of Ubuntu 10.04, and updating the BIOS. Below is a link to the bios upgrade...

[http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-68178]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-68178")


Previously I did not have the other CPU running so I enabled it from the BIOS menu. Here are pictures from System Monitor and htop

[http://picasaweb.google.com/lh/photo/H21jRccJ42oST5-NUibhug?feat=directlink]("http://picasaweb.google.com/lh/photo/H21jRccJ42oST5-NUibhug?feat=directlink")

[http://picasaweb.google.com/lh/photo/HrOu3iBanXuEM7B1YQkbrg?feat=directlink]("http://picasaweb.google.com/lh/photo/HrOu3iBanXuEM7B1YQkbrg?feat=directlink")

Has anyone ever seen something like this before? Is it a hardware issue?

---

### Post by stressmonkey on 2010-07-03
just to update on the thread....

still have not found a solution to the problem. has anyone ever came across something like this before? is it a hardware problem?

---

### Post by mikewhatever on 2010-07-05
The problem is odd indeed. How come the dual cpu wasn't enabled in the bios from the start?

---

### Post by stressmonkey on 2010-07-05
I just had it disabled because I didn't really need all the processing power, and I thought it would save battery life. But because the lag is so much, I enabled it to be able to take the screenshots and do a clean install of Ubuntu and update it.

---

### Post by happyhamster on 2010-07-05
Perhaps this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/537396](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/537396)

---

### Post by stressmonkey on 2010-07-05
[FONT=Arial][SIZE=2]that's very strange. I removed the battery to take out one of the RAM sticks (I have a 2gb stick, installed about 4 months ago, and a 512mb that is original to the comp), and when I booted up the computer it seemed like the problem was resolved.  But I am still getting spikes in the CPU usge....from 15% to 25 to 30% on one processor and 5% to 20% on the other.

Because this thread died off for a while, I posted to a different thread that is having much more activity.  Please refer to 
[SIZE=3]
[/SIZE][/SIZE][/FONT][FONT=Arial][SIZE=3][http://ubuntuforums.org/showthread.php?t=1524521](http://ubuntuforums.org/showthread.php?t=1524521)[/SIZE][/FONT]

---

### Post by mikewhatever on 2010-07-05
Died of a while? You only posted it five days ago.

---

### Post by stressmonkey on 2010-07-05
[FONT=Arial][SIZE=2]Sorry this was my first time posting to the forum and I have now been informed on proper posting etiquette. [/SIZE][/FONT][FONT=Arial][SIZE=2]

I guess this post can be marked as SOLVED,  because everything is back to normal with my computer.  
  
I think what happened was that one of the updates triggered something in  my computer to use a ton of CPU usage. What was strange about it was  that there was no process listed in 'htop' or system monitor that was  eating so much processor power.  When I took my battery out of the  laptop to remove the 512mb memory stick, the problem went away. 
  
I reinstalled the 512mb stick and now everything is running smooth, so  it was not the RAM that was causing the issue.
  
Reading the debugging report  [/SIZE][/FONT][FONT=Arial][SIZE=2]
  
  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/537396](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/537396)
  
at post #33, a user was experiencing similar problems with a sudden CPU  spiking and 100% usage, and he took his battery out for 1 minute, and  that fixed the problem.  So if you have this problem, I guess the best  bet is to do likewise.
  
Thanks a lot for the help everyone. This was my first time using the  forum and I appreciate it very much! 
  
  
[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT]

---

