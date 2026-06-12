---
title: "Laptop questions regarding dialup Internet access and config"
date: 2012-05-29
forum: General Help
---

### Post by charleswb on 2012-05-29
I'm accustomed to using Ubuntu 11.04 on a Dell Precision desktop at my office, and another at my home.

I just installed it on a coworker's personal laptop at her request. She wants to try it.

Since I have no prior experience with laptops, I am a bit confused about her dialup Internet access.

She has Wifi access at the office, which she got working. The driver had already installed automatically, and she figured out where to enter the office Wifi password. So that part when smoothly.

However, at her home she has **dialup Internet access.** So far, neither she or I have figured out: **Where to enter configuration info for dialup Internet access?** Please provide advice for this. Thanks!

P.S. - that's one more new Ubuntu user! Even though I'm a Windows IT guy for my job, I am an Ubuntu missionary (spreading the word and getting people to try it). Maybe someday we can change all our office computers to Ubuntu. That's my fantasy. Meanwhile, I'm trying to learn as much about Ubuntu as I can. I've been using Ubuntu for 2 years on my computers, but only recently starting learning terminal and commandline.

---

### Post by mike555 on 2012-05-29
You might need to install ppp-gnome , not sure, it's been a while since I used dialup.
   and of course she needs a linux compatible dialup modem and a linux compatible dialup service .
   here in USA I recommend "Basic ISP"

---

### Post by marshag63 on 2012-05-29
charleswb, I can offer a couple of suggestions.  If your friend's laptop is older, all she would need is a pcmcia modem card (she may even have one laying around).  If her laptop is newer she would have to find a modem that is not a "winmodem."  What works for sure for dial-up and ubuntu is an old fashion serial modem, but I don't know if she could hook that up to her laptop if it is newer.

Programs to use for dialup can either be command line or graphical - I would suggest gnome-ppp.  

Here's a link I found that might help:  [https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

Hope this helps.

mdg

---

### Post by charleswb on 2012-06-03
Her laptop is a 3 or 4 years old Dell. Forgot model name and don't have her laptop handy at this time.

I'll check back with her to see how she's doing with it.

---

