---
title: "Sporadical very high I/O waiting load (possibly due to resume-from-sleep)?"
date: 2011-02-04
forum: General Help
---

### Post by *uu on 2011-02-04
[B]EDIT (March 08 2011):
By now I could confirm that the issue would occur, as well, after a few days of the machine running constantly, without resume. See also link to bug report in post #3.
/EDIT[/B]

Hi everybody,

for the last couple of days my box sometimes and sporadically ran into very high load. When at this state, I would first see the IOWait graph of the System Monitor Applet run very high, between 25 and 100% of my 4 CPUs, and shortly after also my mouse cursor would start lagging big time. Also, the harddisk usually would start to rattle like crazy. All in all, the system would eventually become almost unresponsive, every keystroke would take almost minutes to show effect.

Even if I managed closing all browsers, mailers, calendars, anything, leaving running only a mere logged-in GDM session, the system would not recover but continue to go into that unusable state. [FONT="Courier New"]top[/FONT] would not show anything unusual concerning CPU usage in the processes list, but the 'X.0%wa' value (I/O waiting, normally at or close to 0,0%) would go and remain at close to 100%, and the load average would rise constantly (in this state, I saw load averages of more than 10 and even up to 20; load is normally below 1.00 on this box).

I could not reproducibly find what would cause the issue, sometimes I was just watching a flash video in a browser, another time I would listen to music in Rhythmbox.

After some research I came across the [FONT="Courier New"]top -i[/FONT] parameter (idle processes), and there, most of the time, only '[FONT="Courier New"]top[/FONT]' and '[FONT="Courier New"]kswapd0[/FONT]' would appear. So, to my understanding, [FONT="Courier New"]kswapd0[/FONT] does have some trouble doing its swapping work.

Long story short, the only working solution I found out of this without hitting the reset button or waiting half an hour until all keystrokes and actions for a reboot are processed, was to swapoff everything via '[FONT="Courier New"]sudo swapoff -a[/FONT]'. The first time around that I had to use this trick, [FONT="Courier New"]swapoff[/FONT] shoveled all the swapped-out data back to ram, and when finished after a few minutes everything was fine again. Immediately afterwards, I could re-[FONT="Courier New"]swapon[/FONT]. 

At one time, though, after swap-off, the IOWait graph was still quite high, but my system was almost usable normally, only still a bit laggy. But when I tried to swap-on, the swap would be used and filled immediately, and my system would go straight back to being more and more unresponsive. So I settled with swap-off and ran without swap for the time being.

On my research I read somewhere (can't remember where) that it might be related to resuming after Suspend-to-RAM. I usually don't switch off my box at night, but suspend-to-RAM instead, so this might be the case here.

Also, in a recent occurrence of this issue, I noticed that my swap total was displayed as 3 GB in [FONT="Courier New"]top[/FONT], even though my swap partition has only 1 GB. So I stumbled upon [FONT="Courier New"]/dev/ramzswap0[/FONT] of a size of 2 GB being swapped on, and it's rule of 50% of the system's memory in [FONT="Courier New"]/usr/share/initramfs-tools/conf.d/compcache[/FONT], which I suspected to be the cause. But disabling that and running with only the 'traditional' swap didn't seem to solve it: nevertheless, the issue occured again!

Well, anyway, I suspect this might be a new bug surrounding kswapd0, especially as it only started a few days ago, possibly after one of the recent kernel upgrades (linux-generic 2.6.32.28.31 to 2.6.32.28.32, or 2.6.32.27.29 to 2.6.32.28.31; before that, the system was running for month's without this behavior), or maybe even [something like this old bug]("https://bugs.launchpad.net/ubuntu/+bug/484045") regressing. But before submitting it as a bug, I'd like to know if anyone knows such behavior and possibly has any ideas what might be the cause or where else a cause might be found. And I'd like to know what info I'd have to submit with a bug report, and how to get the info...

I'm on Ubuntu 10.04, running on a box with AMD X4; 4GB RAM; 1GB swap (currently swapped off); uname output: 'Linux machine 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 23:42:43 UTC 2011 x86_64 GNU/Linux'. If you need further info, please let me know.

Any assistance is greatly appreciated. :-)

uu

---

### Post by macaffi666 on 2011-03-08
bump !

same problem here, kubuntu 10.04, It is definitely not a suspend issue since I use my desktop PC as a server, and I never suspend it or switch it off.

I don't have rmazswap and I stongly suspect a kswapd bug. The PC run for 70 days without a flaw and then the high I/O activity suddendly appeared.

---

### Post by *uu on 2011-03-08
Hello macaffi666,

another affected user opened a bug report on this over at launchpad:

[https://bugs.launchpad.net/ubuntu/+bug/721896](https://bugs.launchpad.net/ubuntu/+bug/721896)

The report opener also runs a server without resume, and by now I could confirm that it also would happen on my machine when I'm not resuming.

Please go there and click the "affects me too" button at the top. The more people affected, the sooner we can hope for improvement.
(Though, the issue hasn't hit me for the last couple of days after the recent kernel updates -- knock on wood, again...)

---

