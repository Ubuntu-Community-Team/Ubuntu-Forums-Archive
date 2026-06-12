---
title: "Ubuntu 9.10 not connecting to the internet"
date: 2010-03-10
forum: General Help
---

### Post by maxim219 on 2010-03-10
Hi everyone,
I had this Internet connection problem for like 2 days, no Firefox, no Updates, no Softwares, it by all means freaked me out!
Here is my step by step solution:

PS1. this solution is for those of you who are connected to their WIFI or Ethernet cable and can't get Internet. 

Oh yes, for those using other computers to look for a solution (cause basically there's no internet to use on ubuntu :wink: ), here is a quick fix for Firefox, so you can follow the steps and try them out on your OS directly:

1- copy and past or simply type **about:config** in the firefox bar address.
2- press the "I'll be careful, I promise" button
3- in the filter bar, type **ipv6**
4- the browser will show a phrase "network.dns.disableipv6", double click the phrase to show **true** instead of **false** in **Value** section.
5- browse your Internet to find your way out !!! 

Ok so for those who wanna able the Internet for the rest of Ubuntu applications, here is what I did:

1- **Applications>Ubuntu Software Center>Edit>Software Sources**
2- **Check** all the boxes in the **Ubuntu Software** window
3- Go to **download from** menu choices and click [B]Other...
[/B]4- Click **Select Best Server** and let it ping
5- After it's done, click **Choose Server** and then close the **software sources** window
6- In **Ubuntu Software Center**, you'll notice it is downloading the latest updates for you
7- After it's done downloading, go to **System>Administration>Update Manager>install updates**
8- Follow the proceeder, I encountered three messages:
    8.1- click **forward**
    8.2- click **replace**
    8.3- check all the boxes and then **forward**
9- Restart your computer
10- Hallelujah you have your Internet back :grin: !! 

PS2. You can now go back and activate ipv6 on your firefox, some poeple don't care or prefer to disable it to get faster internet, but in my opinion, Internet is evolving and ipv4 will be replaced sooner or later.

Let me know if it works for you too !
Cheers

---

### Post by Bobusa01 on 2010-03-26
It worked as far as downloading goes. but still does not connect to Internet. It connects if I post Ip address in the browser. For example if I use 74.125.65.99 it pulls up the Google page, But If I try [www.google.com]("http://www.google.com") it does not work
Thanks
Bob

---

### Post by Kidogo on 2010-04-12
**Solved: I changed the DSL modem.**
I have solved a similar problem. I run Ubuntu 9.10 through a bootable USB memory. My Sony Vaio VGN-SZ3XP was connected through a DSL modem (running ADSL2+), ZHONE 6212. I could not reach internet at all. 

Strangely enough a few days earlier I had been able to connect to internet with the same setup (exkluding the ZHONE modem), when visiting my son and connected to his LAN.

I tried all suggestions in this and other forums to get into internet, but I did not succeed.

Finally I suspected the modem to be the culprit. I changed to an older modem (not ADSL2+ but ADSL2 without a+). That modem, a Westell B90, worked just fine, and I can now reach internet!

So fellows, why not try another modem if you have problems reaching the internet?

---

