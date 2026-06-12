---
title: "networkin option"
date: 2011-08-19
forum: General Help
---

### Post by Rakeshvijayan on 2011-08-19
from this link it show networking option on administration networking ,now an using ubuntu 10.4 " [http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html) "
how can I got that networking window

---

### Post by drpjkurian on 2011-08-19
Hi Rakesh 
I Cannot understand your Question....

---

### Post by grahammechanical on 2011-08-19
When I was using a dial-up modem I used pppconfig to make the connection to the ISP. In that link look for this

> Configuring a Dial-Up Connection using pppconfig

pppconfig may already be installed on your system.

Or you could install Gnome PPP. It will do the same thing but with a graphical User Interface. The directions are in that link. Look for:

> Configuring a Dial-Up Connection using gnome-ppp

Gnome PPP can also be downloaded through the Ubuntu Software Centre.

I have not seen that networking Window that you want to use in Ubuntu for a couple of years. This is why I used pppconfig until I got broadband and could use Network Manager.

Regards.

P.S. That link is dated 14th December 2006. There have been a lot of changes since then. This is why you cannot see the menu entry that you are looking for.

---

### Post by Rakeshvijayan on 2011-08-20
ok Thants my mistake what should I do that I need to connect internet with a dial up modem

---

### Post by drpjkurian on 2011-08-21
Hi 
I once tried by using Wvdial from ubuntu software centre..

---

### Post by frank cox on 2011-09-08
> **Rakeshvijayan said:**
> ok Thants my mistake what should I do that I need to connect internet with a dial up modem

Hi Rakeshvijayan:

First thing you have to do is see if the modem is recognized.The easiest was to do that is with Gnome-PPP which is included but not installed . here is where it is :
/usr/share/local-repository/binary/gnome-ppp_0.3.23-1ubuntu3_amd64.deb
The 32 bit version is there as well. 

After you install it run the setup and see if it finds your modem. If it does great , it probably won't and my advice is to buy another modem it will.  The cheap {10.00 to 12.00} USB winmodems on ebay will show up automatically and seem to connect as well as any, Or you can use any serial {hardware} modem and they start around 30.00 . and are the best as they do not use any system resources. If it is a laptop you will want to go with the cheap USB winmodem or a USRobotics USB serial modem for around 40.00 .
For some reason the cheap ones will only let you set them for 46k but when you check they are running faster them that and seem pretty quick as dialup goes.

Next hit control - alt -t and type in { sudo adduser yourusername dips } without the ( )'s  and hit enter and the same command for dialout . {sudo adduser yourusername dialout} Replace yourusername with your actual username of course. 
This will give your username permissions it has to have by joining these groups. You can do it from the graphical interface but this is easy and quick. 

Then type { sudo chmod +s /usr/sbin/pppd } and hit enter. At this point you should be able to connect. It may be that the first time you try it will tell you it has a permission problem with pap-secrets or chap-secrets or both 
Usually you can usually fix this by logging in one time as root to allow it to write to those files.

To do that type ( gksudo Gnome-PPP ) without the ( ) 's of course and let it connect then hit  disconnect on Gnome-PPP and try again to connect  from Gnome-PPP .  If you still have trouble you may need to setup paps and /or chaps manually . 

The instructions to do that are here :
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

The first link below  is a recent thread I made when I was having trouble . It was back in 1999 when I first got into Linux that I set up dialup with a Dell modem and Dell Linux drivers and also serial modems, old USRobotics Sportsters flashed to 56k. I almost gave up on Linux altogether but others here like bartender helped me and I discovered Puppy Linux which is very dialup friendly, Ubuntu is not. It is not that bad when you have all the info.

[http://ubuntuforums.org/showthread.php?t=1839620&highlight=gnome-ppp](http://ubuntuforums.org/showthread.php?t=1839620&highlight=gnome-ppp)

This is a thread I found that had the missing ingredient
 ( sudo chmod +s /usr/sbin/pppd )

[http://ubuntuforums.org/archive/index.php/t-1035950.html](http://ubuntuforums.org/archive/index.php/t-1035950.html)
I had gotten it to work by typing  ( gksudo gnome-ppp ) but I did not want to be logged in as root although I don't think it matters. Almost all Puppy Linux users are always logged in as root and I have never heard of anyone getting a virus or being attacked.  There is some more info there I did not need but it is good to have.
Good Luck, Hope this helped!

---

