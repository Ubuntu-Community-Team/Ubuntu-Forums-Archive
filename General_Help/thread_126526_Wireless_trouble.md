---
title: "Wireless trouble"
date: 2006-02-06
forum: General Help
---

### Post by daditlefsen on 2006-02-06
Hi.

Ubuntu did not find my wireless card, can it be this card? I dont know what type of card it is, or what kind of drivers I need. Can anyone help me?

Screenshot: [http://www.home.no/ditlefsen/arkiv/ubuntu/skjermdump.gif](http://www.home.no/ditlefsen/arkiv/ubuntu/skjermdump.gif)

Thanks:)

---

### Post by Robgould on 2006-02-06
ok....go to the network menu under system.  Try to configure aht0....your wireless connection.  If you do not have a driver you will have to use your windows driver with ndissrapper or something like that.  If you search this forum for automoatix, you will find a program that installs lots of software.  One of the options helps you with your wireless card.  Hope this helps

---

### Post by daditlefsen on 2006-02-07
I cant use any windows drivers because i dont know what type of network card that is in it, and i have not got any internet connection on that pc either.. Im sitting on my laptop currently but i also want ubuntu on my stationary pc.

I tryed to install automatix on the stationary pc but nothing happened.. I know that i have not done anything wrong, because i installed it on my laptop..

Can someone help me find out what type of network card i got??:-k

---

### Post by Robgould on 2006-02-07
To find out what card you have, boot the system im windows.  Go to device manager and look in there.  Or you could look in the user manula for your computer if you have one.  You can get to device manager by right-clicking my computer and choosing "manage".  You will see a listing for device manager in the left pane.

---

### Post by daditlefsen on 2006-02-09
Ok, i found out that my network card is **AriPlus G D-Link DWL-G510**. I downloaded the Windows drivers and ndissrapper. But how do I install ndissrapper? I read the INSTALL-file and it said, just type "install" in the terminal it said that the command was not found..

---

### Post by The Mekon on 2006-02-09
I hve a similar card which just works with breezy.  Have you checked if the card has actually been detected by typing iwconfig while in a terminal.

I get:

brian@fonze-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Edwards"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:3D:28:63:B7
          Bit Rate:36 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=31/94  Signal level=-64 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

brian@fonze-ubuntu:~$

If you dont get wireless extension you will need to set up ndiswrapper as described in the Wiki at this [link]("https://wiki.ubuntu.com/WifiDocs/Ndiswrapper?action=show&redirect=HowToSetUpNdiswrapper").

---

### Post by daditlefsen on 2006-02-11
The card is not detected. Ran in to more problems.

Its seems that there are three difrent revisions on the card. I found out (by taking the card out of the pc) that I have H/W Ver: C1 (revision C). D-Link only have divers for revision A and B. After Googling for some time I found this thread at Linuxquestions: [http://www.linuxquestions.org/questions/showthread.php?t=400874](http://www.linuxquestions.org/questions/showthread.php?t=400874)

There it said that I had to get the drivers from the page [http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm)

From the forum I also got this message:
> nd then there is another problem with them.. those driveres only seem to work when you have the exact same kernel as they say you need to have.. so if they say 2.6.8 then you better have that one and not 2.6.12 because that will give your problems and it won't work.. so if you have revision C get the drivers to match your distro and kernel and install those.. (to be found at [http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm))

once you installed those it should be easy enough.. my rev.C card has been working for about a month now.. i have some drop/errors but it's still good..

seems like they updated their RT61 driver.. maybe it works even better now.. anyways you'll need the RT61 drivers

So I need to know the exact file i sould download from the page..

Could someone please help me out? Im not really sure what file I have to download.. I got the newest Ubuntu 5.10:)

---

### Post by daditlefsen on 2006-02-14
I have connected the pc whit a other network card so i was able to run the Automatix. But I did not se any more results.. 

Can anyone please help me out whit the AriPlus G D-Link DWL-G510 Revision C card?

---

