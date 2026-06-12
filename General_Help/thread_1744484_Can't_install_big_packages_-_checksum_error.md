---
title: "Can't install big packages - checksum error"
date: 2011-04-30
forum: General Help
---

### Post by michaln on 2011-04-30
Hi

I have problem witch installing larger packages. Small packages works always. Some bigger works after few tries (like vlc-data). Large packages never works (wesnoth-1.8-music 138MB). I checked many mirrors: main, every from Poland and most from Germany. It same on kubuntu 10.10 and 11.04. My ISP doesn't use proxy of any kind. What could be the reason?

---

### Post by rfry11 on 2011-04-30
Go to SpeedTest.net and run the test. What we're looking for is if it either can't complete, or is extremely low. 

It sounds like what's happening is that your internet connection is resetting or dropping out before the big ones finish, whereas the little ones finish because they're little.

---

### Post by michaln on 2011-04-30
I can complete test on speetTest. I got 30/20 Mbit to Germany (Cologne) and 30/3 Mbit to USA. This is my second ISP with same problem. I don't have a clue what could be a reason. I also couldn't git clone mesa repository for long time. Then in one day i could do it 3-4 times and then it broke for me again. I tested ram with memtest from kubuntu cd and it was ok.
 
I downloaded ubuntu 11.04 iso twice. I got two different md5 checkums and both were wrong... So it's my computer or my ISP's fault. Do you have idea how could i test my ehternet card, disk etc?

---

### Post by rfry11 on 2011-05-01
I had these same problems, and I can tell you that if you're connected with a wired connection, it should be bullet proof on your end so it is definitely an ISP issue.

If you're connecting wirelessly, it may be poor wireless drivers and we can look into that separately. In my experience though, it tends to be an ISP issue. Tell them that you're unable to download large files due to your connection throttling and dropping out, and they should treat that as urgent enough to figure out what's going on.

Downloading the 11.04 ISO via bittorrent will allow you to get the complete file error free for the time being, you can find that over here:
i386: [http://goo.gl/j2BGq](http://goo.gl/j2BGq)
amd64: [http://goo.gl/VuNsP](http://goo.gl/VuNsP)

---

### Post by bergfly on 2011-05-03
I find the best tool for testing a connection is mtr. Open a Konsole window and type

*mtr [www.google.com](www.google.com)*

at the prompt. Let it run for a good bit and see where you are in terms of errors. If you are seeing errors there could be a myriad of reasons, but at least mtr will tell you if they are local or ISP related.

---

### Post by michaln on 2011-05-04
It was on my side. Thank you rfry11 and bergfly for help.

Mtr showed that my network is ok. I talked with my isp but they couldn't find anything on their side. Funny thing about it is that I used wired ethernet connection. I bought wifi router (yay 2011) and it works. Now i have bad hardware or driver. If it's hardware fault why i don't have retrasmitions, broken connections etc? If it's driver bug it had to survive from 2.6.35 to 2.6.38... Dmesg says that i have Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0).

Is there anyone with same hardware that could confirm that it is driver/hardware fault?

---

