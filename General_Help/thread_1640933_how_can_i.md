---
title: "how can i"
date: 2010-12-08
forum: General Help
---

### Post by freefixkorma on 2010-12-08
hey guys i need some help ,i am running ubuntu 10.10 dktop edition need some help in this issue i have a wireless network how can i block some web sites like facebook and tweeter or other sites my daughter i using this page more than as usual i wanna block this page and other pages ,i wanna block any connections to this site or other site that could bridge to this page ,what is best to do please anyone post please . i have a wireless linksys wireless routerand  i there any way i can perform this issue i will appreciate any guidance and how to block certain pages of social network i will appreciate that thanks in advance

freefix

---

### Post by iponeverything on 2010-12-08
A quick and dirty way would be to add the following lines to /etc/hosts

127.0.0.1       [www.facebook.com](www.facebook.com)
127.0.0.1       [www.twitter.com](www.twitter.com)

---

### Post by freefixkorma on 2010-12-08
how i do this in a command line thanks

freefix

---

### Post by endotherm on 2010-12-08
```
sudo nano /etc/hosts
```
<add your 127 lines>
Ctrl + X, when prompted save the doc.

that should do it. it shouldnt be necessary to restart the networking service but if it doesn't work at first try:
```

sudo /etc/init.d/networking restart

```

---

### Post by freefixkorma on 2010-12-08
i am sorry thanks for the reply can you detail little bit more cause i am dummy on this thanks

---

### Post by tgm4883 on 2010-12-08
> **freefixkorma said:**
> i am sorry thanks for the reply can you detail little bit more cause i am dummy on this thanks

I don't think endotherm could go into much more detail than that without sshing into your machine and doing it for you.

---

### Post by freefixkorma on 2010-12-08
thanks for your time 

freefix

---

### Post by freefixkorma on 2010-12-08
thanks guys i managed to do it ,is this going to block those 2 sites that i block and anyone who wants to log in from the phone too or any laptop in the house,sorry i am new with ubuntu thanks for the replies 

freefix

---

### Post by endotherm on 2010-12-08
ok, lets slow down then.
1) open a terminal on the box you wish to edit.

2) enter this command:
```
sudo nano /etc/hosts
```
this will open up the hosts file in a editor called 'nano'. nano is simpler that many of the other editors.

3) in the file, add the 2 lines IPOnEverything suggested.

4) press Ctrl + X to exit the editor. nano will ask you if you would like to save (look toward the bottom of the screen for nano's messages). say yes. it will then ask you if you would like to save it to /etc/hosts. just hit enter to except the default.

so now you have edited your hosts file. all shoudl be done. test to make sure that you cannot get to either of the sites mentioned. 

hope that helps.

---

### Post by tgm4883 on 2010-12-08
> **freefixkorma said:**
> thanks guys i managed to do it ,is this going to block those 2 sites that i block and anyone who wants to log in from the phone too or any laptop in the house,sorry i am new with ubuntu thanks for the replies 

freefix

Well that will work for that one machine. You could do it at the router, but obviously that only works for your network, and there will still be ways around it. 

For what you are trying to do, I would probably just switch to OpenDNS and block the sites there. Again though, if anyone really wants to get around it they still can.

---

### Post by freefixkorma on 2010-12-08
hi guys i did block facebook but twitter still open and i did a line for twitter how can i do for the wireless if it is possible please that will be much better i did not think on that before that will be great  how do i do that if you dont mind

thanks

---

### Post by msandoy on 2010-12-08
In order to manage what you want, you have to enable site blocking in your Linksys router. It should be well explained in the manual, and can usually also be limited to certain times of the day.

---

### Post by freefixkorma on 2010-12-08
thanks i will do that thanks guys

freefix

---

