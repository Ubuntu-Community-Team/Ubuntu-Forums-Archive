---
title: "Get Canon LBP2900 printer working!"
date: 2010-03-11
forum: General Help
---

### Post by herophuong on 2010-03-11
I have a tips to get this popular printer to work on my ubuntu karmic system.
After following very many tutorials ([UNIXMEN]("http://www.unixmen.com/linux-distributions/ubuntu/229-installation-canon-lbp2900-on-linux"), [Wiki Ubuntu]("https://wiki.ubuntu.com/Canon_LBP_2900_HowTo"), [Ubuntu Community]("https://help.ubuntu.com/community/CanonCaptDrv190")) on the web to set up this printer, you are so angry because it doesn't work (or works for the first time and after restarting your computer it doesn't print anymore) !!! Arghh.....
However, I find an interesting thing about it!!!
If you follow the guide on this forum (or any guides I provided above), at the end you should enter a command in the terminal:
> captstatusui -P LBP2900Then you see a windows with blank message. Nothing here, right?
We will begin from here:
> gksudo gedit /etc/ccpd.confChange the tag <Printer LBP2900> to <Printer LBPxx00> (like 2000 or 5000, etc)
Then:
> sudo /etc/init.d/ccpd stop> sudo /etc/init.d/ccpd startIf it does nothing, restart your computer.
Now we enter the first command once again. We should see the message "No specified printer". Don't worry! We will re-edit the ccpd.conf (change LBPxx00 to LBP2900).
Notice that: We don't restart the machine now! Open the terminal and enter two command below:
> sudo /etc/init.d/ccpd stop> sudo /etc/init.d/ccpd startTo make sure we are successful, enter this command again:
> captstatusui -P LBP2900
Now, our printer are "Ready to print" (Remember to turn on the printer).

---

### Post by juliobahar on 2010-03-14
I'm sorry this doesn't make sense at all. Just for the record I did really try it doesn't make any difference.

I know we all are having trouble with those lousy Canon drivers. Honestly I'm about to blow my brains out now for this CANON LBP2900 of mine keeps on losing connection saying a communication error; check your power and your USB cable. And I really don't know why.

I'd appreciate help regarding such an error.

---

### Post by herophuong on 2010-03-15
Do you make sure that your printer can work perfectly with windows?
If yes, I think you should delete all the driver by the synaptics manager. While re-installing the driver, you should connect the printer to your computer. If it can print the first time, and then do nothing after you restart your computer, it's time to do my tip.
I recommend you follow the guide in "ubuntu community" which I have linked above.

---

### Post by juliobahar on 2010-03-15
> **herophuong said:**
> Do you make sure that your printer can work perfectly with windows?
If yes, I think you should delete all the driver by the synaptics manager. While re-installing the driver, you should connect the printer to your computer. If it can print the first time, and then do nothing after you restart your computer, it's time to do my tip.
I recommend you follow the guide in "ubuntu community" which I have linked above.

I was finally able to get my printer working. After a couple of restarts, playing around with cups, ccpd, ccpdadmin, ccpd.conf... etc

But honestly I really don't know what really makes the printer indiscoverable at the first time "saying communication error" in captstatusui.

I don't know but I feel that switching on the printer before booting will make it discoverable by ubuntu, but you have to switch it off and then on or probably change the USB port in order to get it ready for printer ... I might be wrong though


Ah, BTW I used the new canon capt v2.00 just for your knowledge.

---

### Post by herophuong on 2010-03-28
I don't care about the CAPT driver version, because from 1.6 to 1.9 it always works for me.

---

### Post by juliobahar on 2010-03-28
> **herophuong said:**
> I don't care about the CAPT driver version, because from 1.6 to 1.9 it always works for me.

Very good then. I feel still the drivers need more work. An't I right?

---

### Post by herophuong on 2010-03-29
Generally, new driver will fix some errors and get some new functions for our devices. But I think with a printer: what're new functions we can get? And what're the errors we can feel? The new CAPT v2 would have supported more printers. And our LBP2900 driver is still the old.

---

### Post by Finian on 2010-04-02
Hi Everybody I am new to Ubuntu (to Linux in fact...) and of course my  LBP2900 didn't work in the first place...

...after spending hours trying and reading posts I finally found an  solution. It's derived from a post in the german ubuntu Forum  "Installing the LBP5000". It works pretty well and is very logical to  me. I found out that the most important thing is to switch the printer  (LBP 2900) off during the installation and to use the CAPT Driver  Version 2.0!

Since I was so happy to get the LBP2900 working that I posted my  solution on my Blog. You will find a link to the driver aswell.

My Blog: [www.sunscreen.blog.com]("http://www.sunscreen.blog.com")

I hope it works for You! I'd be happy for Feedback.

---

### Post by lukakipic on 2010-06-27
I don't know where I found this driver but at my Ubuntu 9.10 32-bit and now on Ubuntu 10.04 64-bit for Canon LBP-2900 work fine. Just read README file.
 

    	 	 	 	 	 	  
[http://ubuntuone.com/p/86k/](http://ubuntuone.com/p/86k/)

---

### Post by Dominic21 on 2012-05-17
Thank u dude its worked fyn.
I too had the same problem.. Printer doesn't work after the restart. Just worked once at the fresh driver install only. Finally its working by your TIP !!!
THANKS a lot !!!:popcorn:

---

