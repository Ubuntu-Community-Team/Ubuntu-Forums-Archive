---
title: "Wireless Troubles"
date: 2010-08-07
forum: General Help
---

### Post by Kenneh-BeaR on 2010-08-07
Hello. I'm very new to Linux here. My friend introduced me to Linux a while back but I wasn't interested at the time. But fate lead me crawling to Linux when my stupid Vista based laptop caught an unrepairable issue. (Still don't know what the cause was or how to fix it to this day) The other day I brought my computer to my friend and in great desperation, asked him to install Linux onto my pathetically, crippled laptop. So here I am with Ubuntu and all I got to say is... I LOVE IT! It's so fast, clean and new! (Thank you Linus Torvalds and the many hard working programmers for providing this for us)

Now that introduction, story and thanks are out of the way. I would like to present my problem.

After installing Linux I quickly came to the realization that my computer is not picking up my NetGear Router's wifi signal. This is troublesome for me because I have to run a 25ft lan line through my house just to use the internet. I've checked all that I know to check and still haven't found the issue. When I tried to connect at my friends house, the computer recognized his wifi and many surrounding wifi's in the area, however mine did not work. His router is a NetGear as well but a different model, older I think. But he told me that the Broadcom STA driver only recognizes G and N networks (not sure what that means) but I do know that my router is a G (as indicated on the bottom)

Could it be that my laptop is a Dell Inspiron 1545? I read in the Broadcom Driver's "Read Me" it stated that it functioned for; Dell 1390, Dell 1395, Dell 1490, Dell 1500, Dell 1501, Dell 1505, Dell 1510 and Dell 1520. The "Read Me" also stated "Cards not listed here may also work" (I assume "cards" means "WLAN Cards")

So why am I not getting wifi from my router?
What can I do to gain wifi?
Are there any other Ubuntu drivers available that may work?

Please Help and Thanks in advanced.

---

### Post by bergfly on 2010-08-07
Kenneh-BeaR

Just to be clear, you say that your laptop, with the present install of Ubuntu on it, did connect and work at a friends house with wireless? If that is the case, then the issue here is specific to your home, not your laptop. If that is not the case, we have a whole other road to go down. 

thanks

---

### Post by debasish_bhattacharjee on 2010-08-11
Hello Everyone,

I am very much new in using Linux. Particularly i have installed Ubuntu 10.04 in my dell 1545 laptop side by side with windows 7. Now i am having problem with wireless setup.

basically i am using a wireless router to get connected with internet and i dont have to do anything while i am using windows 7, but while i pretend to use ubuntu i couldnt get connected with internet and without that i cant mange my required plugins and other related stuffs, what can i do?? please help.

---

### Post by MrStill on 2010-08-11
> **debasish_bhattacharjee said:**
> Hello Everyone,

I am very much new in using Linux. Particularly i have installed Ubuntu 10.04 in my dell 1545 laptop side by side with windows 7. Now i am having problem with wireless setup.

basically i am using a wireless router to get connected with internet and i dont have to do anything while i am using windows 7, but while i pretend to use ubuntu i couldnt get connected with internet and without that i cant mange my required plugins and other related stuffs, what can i do?? please help.

For starters, it will be easier for you if you can go somewhere that you can connect your laptop to a network using Ethernet connection. Wired connections almost always work out of the box, in my experience. 

If you open up a terminal, and post output from lspci, iwconfig, and ifconfig, this would offer some useful information.

---

