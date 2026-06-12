---
title: "hard 2 grasp"
date: 2011-07-19
forum: General Help
---

### Post by mixednutsduo on 2011-07-19
Although I expierimented with "Mint" awhile back, I consider myself an ole' coot beginner (67 yrs. old and on fast forward)...My question should be easy for you but 4 me, It's been a headache...I currently run Ubuntu on win 7 via wubi and I cant even get on the net w/Ubuntu....I have all the #'s ie. mac address, router address etc....but nothing!!..I'm retired and if time were money, I'd be a millionaire...I have a little above average intelligence, but, I find this all rather daunting..If you could get me through this, I mat be more inclined to stick with it...plain english and step by step instructions would be helpful...Thanx in advance[ :confused:mixednutsduo@rocketmail.com]("http://ubuntuforums.org/mixednutsduo@rocketmail.com")

---

### Post by trollolo on 2011-07-19
To get on teh "net" you need the right drivers. they were a pain for me to find, but this is how i did it:
 
1) settings>system>drivers
2) activate non-free drivers
3) copy URL of error code
4) move to computer with access
5) download the .deb (i had to download 4 of them)
6) move back to ubuntu comp, install them 1 at a time
 
and your computer should start displaying the option to choose a network

---

### Post by doas777 on 2011-07-19
welcome!

first a peice of advice: edit your post to remove your email. we appreciate the gesture, but there are spiders that scan the web for email addresses, and we wouldn't want them to find yours.

on your issue, do you have a home router, or are you connected directly to your ISPs equipment (cable/adsl modem)? are you wired or wireless?

you said you had all the numbers. does this include an ip address? what is it?
you can find out if you don't know, by opening a Terminal, and entering:
```
ifconfig -a
```you can copy and paste in the terminal by rightclicking. copy the output of the command and post it back here if you would like help interpreting it.

---

