---
title: "Gyachi for ubuntu 10.10"
date: 2010-10-10
forum: General Help
---

### Post by golusweet on 2010-10-10
Hey all,

I can't install gyachi for ubuntu 10.10

tried PPAs, but there isn't package for i386.

anyone having working .deb?

---

### Post by asif_ebrahim on 2010-10-11
I installed from the following link on my laptop on 10.10 Netbook edition and it worked perfectly.

[https://launchpad.net/~loell/+archive/ppa/+build/1806226](https://launchpad.net/~loell/+archive/ppa/+build/1806226)

However when i install it on my destop with the 10.10 Desktop edition i get the following error :

Dependency is not satisfiable: libgtkhtml2-0 (>= 2.11.1) 

Does anyone have any ideas ?

Thanks.

---

### Post by gigelb on 2010-10-11
Same problem here

with Ubuntu 10.10 
Dependency is not satisfiable: libgtkhtml2-0 (>= 2.11.1)

---

### Post by golusweet on 2010-10-11
yeah. same problem.

---

### Post by gigelb on 2010-10-11
Found a solution that works for me on Ubuntu 10.10

type in terminal

sudo add-apt-repository ppa:adilson/experimental
sudo apt-get update
sudo apt-get install gyachi

Hope it works for you.

---

### Post by asif_ebrahim on 2010-10-11
Thanks alot. this worked a treat! :guitar:


> **gigelb said:**
> Found a solution that works for me on Ubuntu 10.10

type in terminal

sudo add-apt-repository ppa:adilson/experimental
sudo apt-get update
sudo apt-get install gyachi

Hope it works for you.

---

### Post by golusweet on 2010-10-11
> **asif_ebrahim said:**
> Thanks alot. this worked a treat! :guitar:


Yeah, it works. :P

---

### Post by morduk on 2010-10-13
it;s work indeed...but i have a question...have you managed to make the web cam work??i mean i can open it and have image but when i send an invitation,my friend accepts it and receives not available..anyoane any idea??

---

### Post by gigelb on 2010-10-13
> **morduk said:**
> it;s work indeed...but i have a question...have you managed to make the web cam work??i mean i can open it and have image but when i send an invitation,my friend accepts it and receives not available..anyoane any idea??

Did you click yes on Gyache popup when your friend has accepted your invitation?

---

### Post by sandman6471 on 2010-10-16
[B]Hey, Thanks for the post. It worked great for me as well.

As far as when you send a webcam invitation you have to go under permissions in your webcam window and uncheck "automatically deny anonymous users. It seems you have to do this each time you start your webcam. After doing so you will get the allow this user to view your webcam box.

Hope this helps. Just glad I had a solution to post. Linux is the greatest.

Later all, Take Care[/B]

---

### Post by negora on 2010-10-21
**gigelb:** Thanks a lot for the repository. It was JUST what I was looking for ages!

About GyanchI, although it's an "ugly" program, I've to admit that I've not been able to find any another IM on Linux which is able to make voice and video chats possible employing the Yahoo! Messenger protocol. Am I right or wrong?

---

### Post by lesterinside on 2010-11-17
Thanks for this. Installed fine.

---

### Post by Kevin_lifeshand on 2011-01-31
I need help. The download worked but when i go into a chat room. and try to enable voice. it said "Cannot run gyvoice due to the following missing files:

tsd32.dll
      tssoft.acm

Not in the following directories:
      /
      /usr/lib/win32/
      /usr/local/lib/win32/
      /usr/lib/codecs/
Please help!

---

### Post by Czvp on 2011-02-04
> **gigelb said:**
> Found a solution that works for me on Ubuntu 10.10

type in terminal

sudo add-apt-repository ppa:adilson/experimental
sudo apt-get update
sudo apt-get install gyachi

Hope it works for you.
thanks a million. it worked!

---

### Post by bryan boomer on 2011-02-20
Trying to install Gyachi on a hp mini 1000 using the ppa used the sudo command to get apt-get update I getting could not get lock /var/lib/apt/list - open (11: resources temporary unavailable) then again unable to lock directory /var/lib/apt/list

---

### Post by jerenept on 2011-02-20
> **bryan boomer said:**
> Trying to install Gyachi on a hp mini 1000 using the ppa used the sudo command to get apt-get update I getting could not get lock /var/lib/apt/list - open (11: resources temporary unavailable) then again unable to lock directory /var/lib/apt/list

Try again in a couple minutes, or wait for Synaptic, apt-get, or the Software Centre to finish.

---

### Post by duplicate150 on 2011-03-19
hello everyone.

I am new to using ubuntu at home and still use vista at office. I have functional knowledge of working my way around things in both operating system as an average user and i'm in no way an expert.

Now here's my problem. I use LAN both at home and office and at both places it is provided by my organisation. Over the past few days it appears, that ports for yahoo messenger have been blocked. So now i cannot use yahoo messenger at office or from home too. Yahoo mail and other browser based services work fine. So i can log into yahoo web messenger or through meebo.com but i cannot use webcam or voice or pic sharing.

So i installed gyachE Improved v1.2.10 for my home pc running ubuntu 10.10. Installation is fine and gyachi fires up without any problem. But it disconnects almost immediately and heres what i get on the gyachi window:
"[Saturday 19 March 2011 12:31:59]    CONNECTED: type /help for help

[Saturday 19 March 2011 12:32:15]      ** Could not login: Connection timed out. [ Could not login: Connection timed out. ] **
[Saturday 19 March 2011 12:32:15]    Disconnected from Yahoo!    See Ya!  Online for  0 : 00 : 19"

What do i do in this case? I have tried using different ports like 8001, 8002, 23, 80 etc but the result is same everytime. Is there no way gyachi can connect?

I have tried and i did not find any solution to this issue anywhere though similar log is repeated in some other threads. Incidentally i have wine installed on my pc and it is working fine.

Any suggestion and help is welcome.


Thanks all

---

### Post by myscam on 2011-03-23
> **gigelb said:**
> Found a solution that works for me on Ubuntu 10.10

type in terminal

sudo add-apt-repository ppa:adilson/experimental
sudo apt-get update
sudo apt-get install gyachi

Hope it works for you.

This worked just fine for me.  Thanks a lot.  I love Ubuntu.:)

---

### Post by pancoz on 2011-03-28
hey,
i could not start voice chat and webcams in gyache?
why?
it says like this when i open the voice chat option.
some one please help me out.
 
Cannot run gyvoice due to the following missing files:

      tsd32.dll
      tssoft.acm

Not in the following directories:
      /
      /usr/lib/win32/
      /usr/lib/win32/
      /usr/local/lib/win32/
      /usr/lib/codecs/

---

### Post by closetpokey on 2011-05-02
This is exactly what I needed thank you

---

### Post by cybersingh on 2011-06-28
[http://anipossible3.blogspot.com/2009/01/gyache-on-ubunt.html](http://anipossible3.blogspot.com/2009/01/gyache-on-ubunt.html)


hope this link solve ur problems. :guitar:
Contains step by step Guide to installation of gyachi worked well for me.

---

### Post by anshulfy on 2011-10-30
Hey thanks, it works for me.

---

### Post by stalkingwolf on 2011-12-13
i have also used this method in 11.04 and several variants of 10.10 with great success.

---

