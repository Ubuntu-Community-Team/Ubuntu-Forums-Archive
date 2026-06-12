---
title: "Ubuntu and Apple Touch 4th Gen"
date: 2010-09-11
forum: General Help
---

### Post by GammaPoint on 2010-09-11
I need to replace my almost 6 year iPod Nano since it can only run for about 45 minutes now on a full battery. I was thinking of replacing it with an iPod Touch 4th generation. Will this work/be recognized with Ubuntu? Anyone have experience with the 4th generation directly or perhaps what has been your experience with the 3rd generation Touch? Thanks!

---

### Post by Pelo1968 on 2010-09-18
Got the new ipod touch 4th gen earlier this week (pre-sale) and it only mounts as a camera in ubuntu , I cannot access it using rythmbox or gtkpod. and itune 10 does not work on wine.  I rebuilt my old xp box which I now access using vnc to run itune 10 and load media it the ipod touch (samba share for the folders on my ubuntu box) , bit of a hassle but the ipod touch 4th gen is so worth it.

I'm just a user not a pro, I expect someone will find ways to deal with those issues once the ipod touch 4th is officialy out in stores

---

### Post by GammaPoint on 2010-09-18
> **Pelo1968 said:**
> Got the new ipod touch 4th gen earlier this week (pre-sale) and it only mounts as a camera in ubuntu , I cannot access it using rythmbox or gtkpod. and itune 10 does not work on wine.  I rebuilt my old xp box which I now access using vnc to run itune 10 and load media it the ipod touch (samba share for the folders on my ubuntu box) , bit of a hassle but the ipod touch 4th gen is so worth it.

I'm just a user not a pro, I expect someone will find ways to deal with those issues once the ipod touch 4th is officialy out in stores

Thanks for your response Pelo. I'm really hoping I can get it to work in Ubuntu but I do have a Windows CD if I need to try to dual boot or something. I'll update this thread if I find a better solution.

---

### Post by Pelo1968 on 2010-09-20
there is hope yet, I don'T much like having to boot up an extra computer just to sync my ipod and I'm still searching for ways to do it on linux/ubuntu. I found this : 

[http://www.libimobiledevice.org/](http://www.libimobiledevice.org/)

didn'T work for me but that might just be a bug , I'll wait a bit still. From the website and the video they seem to have all the basis covered

---

### Post by GammaPoint on 2010-09-21
Thanks for posting that Pelo. I'll give some of these things a shot when I get mine from Amazon in a couple of weeks. Hopefully a solution will be found before then though!

---

### Post by 3rdalbum on 2010-09-21
Does it have to be an ipod? There are some really good Linux compatible players out there like the Sony Walkmans.

---

### Post by Pelo1968 on 2010-09-21
let me put it this way,  it doesn'T have to be an ipod , but it has to be an ipod touch 4th gen ...

---

### Post by macem29 on 2010-09-21
> **Pelo1968 said:**
> let me put it this way,  it doesn'T have to be an ipod , but it has to be an ipod touch 4th gen ...

I get it...:)

my 3G mounts in disk mode, no root, but I can see the folders containing the content, still haven't
found an app or combination of apps under linux that let me manage the device and organize content
anywhere near what I can do with itunes though...still looking, but for now I need an XP box around

---

### Post by GammaPoint on 2010-10-02
I found a solution that I really like. I downloaded VirtualBox and that allows me to install Windows XP on that virtual machine. From there I can easily install iTunes and sync my iPod normally. 

VirtualBox is such an awesome program, and I really like this solution.

---

### Post by Fluffgar on 2010-10-02
I don't know how to get iTunes to work but I'm going to see if an older version might do the trick. 

Google search "old itunes download": 
[http://www.google.co.uk/#hl=en&expIds=17259,17291,24999,26781,26885&xhr=t&q=old+itunes+download&cp=2&pf=p&sclient=psy&aq=f&aqi=g5&aql=&oq=olitunes+download&gs_rfai=&pbx=1&fp=a882380c91775e70](http://www.google.co.uk/#hl=en&expIds=17259,17291,24999,26781,26885&xhr=t&q=old+itunes+download&cp=2&pf=p&sclient=psy&aq=f&aqi=g5&aql=&oq=olitunes+download&gs_rfai=&pbx=1&fp=a882380c91775e70)

UPDATE 

Realised by looking around that iTunes on Wine probably won't even see the iPod Touch 4G either. 

Also uninstalling iTunes in Wine is a complete pain. Had to open the Terminal and type: 

```
locate itunes
```to find everything to delete after attempted uninstalls.

---

### Post by RadioEd on 2010-10-03
For what it's worth I can echo the issue reported above.  I just bought an iPod Touch 4th gen and found the same problem.  Ubuntu sees the iPod as a camera and will sync with F-Spot very nicely, until I screwed it up by trying to get it to sync with Rhythmbox.  Now it does neither.  I essentially have a PDA. :(

---

### Post by tru2lyf on 2010-10-22
> **GammaPoint said:**
> I found a solution that I really like. I downloaded VirtualBox and that allows me to install Windows XP on that virtual machine. From there I can easily install iTunes and sync my iPod normally. 

VirtualBox is such an awesome program, and I really like this solution.
will virtual box allow you to see everything that has been downloaded w/ ubuntu???

---

### Post by tru2lyf on 2010-10-27
the BEST solution to this problem is using virtualbox...after you get all the settings right it works great!!!:KS

---

### Post by Legeril on 2010-10-27
why don't you just not buy an ipod touch? Save your money and buy an eazy-breezey mp3 player

---

### Post by Pelo1968 on 2010-10-28
you can setup shared folders from ubuntu to the virtual machine

---

### Post by Ralph L on 2010-10-28
Although it was in the past when I was running hardy, I got my ipod nano to work quite well using the kubuntu player Amarok.  I installed amarok using Synaptic.  My main problem was installing the help file.  I installed the KDE Help Center and somethings, but not everything worked.  However, the help file was good enough that I got my ipod to work.  By the way I used aac format on the ipod, which took some additional Synaptic installations.

Ralph

---

