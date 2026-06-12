---
title: "flash on ubuntu 10.10"
date: 2011-03-03
forum: General Help
---

### Post by rawk1087 on 2011-03-03
I just updated my computer with ubuntu 10.10 from ubuntu 10.04 now my flash videos are not working i can hear them but the actual video is not coming up... i check my plug ins and everything is enabled i dont know what i should do

---

### Post by HannuMR on 2011-03-03
Open Terminal and copy/paste:

[FONT=Arial][SIZE=2]sudo apt-get install ubuntu-restricted-extras[/SIZE][/FONT]

---

### Post by rawk1087 on 2011-03-03
> **HannuMR said:**
> Open Terminal and copy/paste:

[FONT=Arial][SIZE=2]sudo apt-get install ubuntu-restricted-extras[/SIZE][/FONT]

this did not help anything

---

### Post by nomko on 2011-03-03
Maybe the solution can be found here:
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) (32-bit)
[http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html) (64-bit)

---

### Post by rawk1087 on 2011-03-04
so i watch videos from every other place just not on youtube i went to check my updates and what not and i have everything up to date im think i need to disable the acceleration in settings on the actual youtube but its not highlighted

---

### Post by grahammechanical on 2011-03-04
Are you running 64bit or 32bit Ubuntu? Last year Adobe released a new version of its flash player (10 - I think) that many sites are using. It also released a 32bit Linux version of this new Flash release but it took a while to release the 64bit version for Linux. If you are using 64bit Ubuntu as I am using and the web site requires the latest flash version then you will need the 64bit Linux Flash. It is in the Ubuntu Software Centre. 

Regards.

---

### Post by bobcollard on 2011-03-04
Open Terminal and copy/paste the following;
```
sudo apt-get install nspluginwrapper
```

---

### Post by rawk1087 on 2011-03-04
> **grahammechanical said:**
> Are you running 64bit or 32bit Ubuntu? Last year Adobe released a new version of its flash player (10 - I think) that many sites are using. It also released a 32bit Linux version of this new Flash release but it took a while to release the 64bit version for Linux. If you are using 64bit Ubuntu as I am using and the web site requires the latest flash version then you will need the 64bit Linux Flash. It is in the Ubuntu Software Centre. 

Regards.
  im running a 32 bit ubuntu 10.10

---

### Post by rawk1087 on 2011-03-04
> **bobcollard said:**
> Open Terminal and copy/paste the following;
```
sudo apt-get install nspluginwrapper
```
 
 i put that in my terminal and it unpacked the contents and stopped and waited for me to give sudo command ... im fairly new to liux and ubuntu i guessed i should have mentioned that earlier but im pretty sure i did everything correctly as prompted...

---

### Post by sesipdo on 2011-03-04
go to ubuntu software center and type in search for adobe flash and or just flash :P (:

and are u using Firefox ?

---

### Post by rawk1087 on 2011-03-05
> **sesipdo said:**
> go to ubuntu software center and type in search for adobe flash and or just flash :P (:

and are u using Firefox ?

yes i am using firefox and i tried re downloading adobe flash player 10 and installing the plug in they have and none of the options have worked :(

---

### Post by Frogs Hair on 2011-03-05
The easiest method of installing flash is from software center as sesipdo wrote . If the wrapper is needed it will be installed with flash if you install from the software center. If want to use the 64 bit version then you have install from the adobe site and keep it updated yourself .

---

### Post by Frogs Hair on 2011-03-05
Here is a method for installing via the adobe website. [http://blog.sudobits.com/2010/10/11/how-to-install-adobe-flash-player-in-ubuntu-10-10/](http://blog.sudobits.com/2010/10/11/how-to-install-adobe-flash-player-in-ubuntu-10-10/)

---

### Post by oldos2er on 2011-03-05
Click the FlashAid link in my sig. It will install the correct architecture flash plugin whether you use 32- or 64-bit Ubuntu.

---

### Post by rawk1087 on 2011-03-05
> **Frogs Hair said:**
> The easiest method of installing flash is from software center as sesipdo wrote . If the wrapper is needed it will be installed with flash if you install from the software center. If want to use the 64 bit version then you have install from the adobe site and keep it updated yourself .

yes i downloaded from the adobe website and the ubuntu software center none of that worked :( and for the link in your signature the command ran and i closed the terminal after the processes were completed and still the youtube video box does not show... howeever i didnt try the 64 bit version because im running 32 bit does that matter?

---

### Post by Newuser9 on 2011-03-06
I'm having a similar issue. Youtube was working for a bit and then stopped, I installed the adobe flash through the software centre... I'm running a 64 bit Ubuntu 10.10

---

### Post by rawk1087 on 2011-03-07
> **Newuser9 said:**
> I'm having a similar issue. Youtube was working for a bit and then stopped, I installed the adobe flash through the software centre... I'm running a 64 bit Ubuntu 10.10

thats so sad... no one can help it seems and maybe its a youtube problem

---

### Post by rawk1087 on 2011-03-09
> **Newuser9 said:**
> I'm having a similar issue. Youtube was working for a bit and then stopped, I installed the adobe flash through the software centre... I'm running a 64 bit Ubuntu 10.10

solved the problem the settings menu has a acceleration hardware check uncheck it and it should work!

---

