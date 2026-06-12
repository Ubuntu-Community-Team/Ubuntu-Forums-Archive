---
title: "should i get ubuntu 64 bit..?"
date: 2010-08-14
forum: General Help
---

### Post by rahilm on 2010-08-14
i got a new laptop dell inspiron 15r .. it is 64 bit.
so.. should i install 64 bit version of ubuntu on it,???
it has got ATI gpu...so are there driverrs available.
i googled for ubuntu 64 bit vs 32 bit.. but it showed results of 2007 so there might be some updates.

---

### Post by slooksterpsv on 2010-08-14
I use Ubuntu 64-bit, and it works great! There are a few programs that if I install from elsewhere (non-debs) I may have to get libs for but usually someone's posted a how-to on that.

I say use 64-bit, especially if you have 4GB of RAM or more. The 32-bit era is gone it's all about 64-bit now, my personal opinion.

---

### Post by rahilm on 2010-08-14
> **slooksterpsv said:**
> I use Ubuntu 64-bit, and it works great! There are a few programs that if I install from elsewhere (non-debs) I may have to get libs for but usually someone's posted a how-to on that.

I say use 64-bit, especially if you have 4GB of RAM or more. The 32-bit era is gone it's all about 64-bit now, my personal opinion.
could you specify which programs.. i hope vlc isn't one of them.. now that the korn ppa has closed..

i installed 64 bit..  drivers work, flash works. i sincerely hope ppa's work too..

---

### Post by slooksterpsv on 2010-08-14
> **rahilm said:**
> could you specify which programs.. i hope vlc isn't one of them.. now that the korn ppa has closed..

i installed 64 bit..  drivers work, flash works. i sincerely hope ppa's work too..

Yes most ppas should work if not all. The programs were like Unreal Tournament 2004, had to get a couple of 32-bit libs for it to work; there was a game, Alien Arena, I had to get 32-bit libs for, it's easy and we're here to help get the programs you need running if you run into a 32-bit compatibility issue. Most programs have a 64-bit variant or resolve the dependencies on their own.

---

### Post by Puzzled Guy on 2010-08-14
Just because you have a 64-bit capable computer doesn't mean you should install Ubuntu 64-bit. It could cause problems

---

### Post by rahilm on 2010-08-14
ok.. i take my words back,,. flash doesn't work so well..  i can't press the buttons on some youtube videos

---

### Post by rahilm on 2010-08-14
> **Puzzled Guy said:**
> Just because you have a 64-bit capable computer doesn't mean you should install Ubuntu 64-bit. It could cause problems
it kinda does mean that...
what problems??

---

### Post by benmoran on 2010-08-14
OK, the flash fix is really simple. 
[http://www.ubuntumini.com/2010/07/64-bit-flash-fix.html](http://www.ubuntumini.com/2010/07/64-bit-flash-fix.html)

Besides the shitty flash plugin, there is no reason whatsoever to use 32-bit IMO. It's 2010.

---

### Post by rahilm on 2010-08-14
> **benmoran said:**
> OK, the flash fix is really simple. 
[http://www.ubuntumini.com/2010/07/64-bit-flash-fix.html](http://www.ubuntumini.com/2010/07/64-bit-flash-fix.html)

Besides the shitty flash plugin, there is no reason whatsoever to use 32-bit IMO. It's 2010.
   are you sure this will work on my computer???
{Dell inspiron 15r ,, i3-350m .. ati 1gb]

the last time i did something to fix it (2 hrs ago) .. i ended up re-installing the system..!!

---

### Post by wojox on 2010-08-14
Screw the wrapper. Install the actual [64 bit driver]("http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/").

---

### Post by rahilm on 2010-08-14
i m so gonna test this only on my Live-CD..!!

---

### Post by rahilm on 2010-08-14
> **wojox said:**
> Screw the wrapper. Install the actual [64 bit driver]("http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/").
the first step is really confusing... which link to i click,,??

---

### Post by wojox on 2010-08-14
> **rahilm said:**
> the first step is really confusing... which link to i click,,??

The third here. The one that doesn't have a line through it.

---

### Post by CoolJohnB on 2010-08-14
Why does the Ubuntu Desktop Download page say the 64-bit version is NOT recommended for daily use?

---

### Post by wojox on 2010-08-14
> **CoolJohnB said:**
> Why does the Ubuntu Desktop Download page say the 64-bit version is NOT recommended for daily use?

I think just to make it easier on new people. Say you have a printer with only 32 bit drivers, you'll have to install 32 bit libraries for it.

---

### Post by philinux on 2010-08-14
> **wojox said:**
> Screw the wrapper. Install the actual [64 bit driver]("http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/").

Adobe have removed support for this as there is a security bug. It's been fixed in the latest 32 bit flash though.

[http://labs.adobe.com/technologies/flashplayer10/faq.html](http://labs.adobe.com/technologies/flashplayer10/faq.html)


[http://www.adobe.com/support/security/advisories/apsa10-01.html](http://www.adobe.com/support/security/advisories/apsa10-01.html)

---

### Post by rahilm on 2010-08-14
> **philinux said:**
> Adobe have removed support for this as there is a  security bug. It's been fixed in the latest 32 bit flash though.

yay!!

benmoran's solution worked though.....

gnome-do ppa is not working..

DOUBT:
If i install virtualbox...  will the guest session still be 64bit??

---

### Post by TyLLy_4 on 2010-08-14
DO NOT USE 64 BIT ON A DESKTOP INSTALL!!!!!! 

Ubuntu itself its OK, however the performance difference is not that great and there are lots of applications that are 32 only. 

I was running 64but on my DV lappy for 6 months until I couldn't take it any longer. 

64 Bit will fight you every step of the way for absolutely everything.

I would only recommended 64 bit for servers 

(my server right now its running 10.04 64Bit)

---

### Post by rahilm on 2010-08-14
> **TyLLy_4 said:**
> DO NOT USE 64 BIT ON A DESKTOP INSTALL!!!!!! 

Ubuntu itself its OK, however the performance difference is not that great and there are lots of applications that are 32 only. 

I was running 64but on my DV lappy for 6 months until I couldn't take it any longer. 

64 Bit will fight you every step of the way for absolutely everything.

I would only recommended 64 bit for servers 

(my server right now its running 10.04 64Bit)

could u b more specific....
which applications??

can we use --force-architecture on such??

---

### Post by TyLLy_4 on 2010-08-14
> **rahilm said:**
> could u b more specific....
which applications??

can we use --force-architecture on such??

I didn't mean to defame Ubuntu. i Just wouldn't recommend the 64bit version for desktop use. 

I had lots of problems with:

1) Flash
2) Compiz (i think relating to graphic card)
3) Forcing Debs (Most of the time it broke something) 
4) Almost no games run acceptably on 64
5) Random applications that i Would need that run perfectly on 32 Ex:
GTK Radiant, Setup Makers, My PHP IDE, Map Compiler.

---

### Post by worksofcraft on 2010-08-14
There have been a few teething problems with 64 bit Linux, but benchmark tests such as [http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1) show an impressive improvement in performance for many situations. In the long run it is the way forward IMO.

---

### Post by TyLLy_4 on 2010-08-14
> **worksofcraft said:**
> There have been a few teething problems with 64 bit Linux, but benchmark tests such as [http://www.phoronix.com/scan.php?pag...u_32_pae&num=1](http://www.phoronix.com/scan.php?pag...u_32_pae&num=1) show an impressive improvement in performance for many situations. In the long run it is the way forward IMO.

Here is some more meaningful information about the benchmarking and performance of 32 vs 64 Bit. 

[http://tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

[CENTER]
[IMG]http://tuxradar.com/files/3264_extract.png[/IMG][/CENTER]

I guess for certain things like working with video or 3D rendering it does perform a LOT better. However as i didn't really do none of those things the stability of the 32 bit was more worth it.

---

### Post by oldos2er on 2010-08-14
"DO NOT USE 64 BIT ON A DESKTOP INSTALL!!!!!!"

I have to disagree. 64-bit Ubuntu has worked very well for me the past couple of years.

---

### Post by TXpaniolo on 2010-08-14
I'm a noob and went with 64 bit.  Some small issues with Flash.  The 32 bit wrapper works fine at YouTube, sometimes some issues with YouTube embedded on other sites but if I really want to see it I just go to YouTube.  Other than that everything has been smooth.  But I don't play games.  otoh if you are a heavy gamer like my son it is doubtful you will play those under Ubuntu anyways.

---

### Post by rahilm on 2010-08-14
> **TXpaniolo said:**
> I'm a noob and went with 64 bit.  Some small issues with Flash.  The 32 bit wrapper works fine at YouTube, sometimes some issues with YouTube embedded on other sites but if I really want to see it I just go to YouTube.  Other than that everything has been smooth.  But I don't play games.  otoh if you are a heavy gamer like my son it is doubtful you will play those under Ubuntu anyways.
good point.
now that i have installed ubuntu 64bit and all softwares and drivers and all...
i really need a good reason to remove and put 32 - bit (it will take roughly 1/10 of the time as i have all the updates ready)

---

### Post by worksofcraft on 2010-08-14
> **TyLLy_4 said:**
> Here is some more meaningful information about the benchmarking and performance of 32 vs 64 Bit. 

[http://tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

I guess for certain things like working with video or 3D rendering it does perform a LOT better. However as i didn't really do none of those things the stability of the 32 bit was more worth it.

Hum yes IDK why that link of mine stopped working, but evidently it depends what you do with your computer. While you may like unzipping Archives others are interested in Apache static web page serving. The graph looks like the one attached:


[CENTER][IMG]http://www.phoronix.com/data/img/results/ubuntu_32_pae/2.png[/IMG][/CENTER]

All the progams I use on my 64 bit installation work just fine and IMO it is demand for leading edge technology that fuels progress.

---

### Post by NewDisciple on 2010-08-14
Another vote for 64 bit. As for flash follow the advice that wojax gave.  The 64 alpha version is still out there and it works.  You have nothing to lose by trying the 64 bit version.  If for some reason it is a problem for you go back to the 32 bit version.  The only real reason for not installing is not enough ram.

---

### Post by rahilm on 2010-08-15
I do some video transcoding to make videos for my mobile phone. I also intend to make some videos when i go to college from tomorrow.. will this affect my choice.
Does git (or whatever) of ffmpeg works for 64-bit... i'll normally use openshot and avidemux...

---

### Post by rahilm on 2010-08-15
> **TyLLy_4 said:**
> I didn't mean to defame Ubuntu. i Just wouldn't recommend the 64bit version for desktop use. 

I had lots of problems with:

1) Flash
2) Compiz (i think relating to graphic card)
3) Forcing Debs (Most of the time it broke something) 
4) Almost no games run acceptably on 64
5) Random applications that i Would need that run perfectly on 32 Ex:
GTK Radiant, Setup Makers, My PHP IDE, Map Compiler.

1)flash is almost working fine (i didn't test everything)
2)Comopiz works with AMD drivers
3)I am going to try that, but i haven't yet come across a 32-bit only package.
4)Never used one of them. (IDE problems have me worried.. anyone tested eclipse???)

---

### Post by slooksterpsv on 2010-08-15
> **rahilm said:**
> 1)flash is almost working fine (i didn't test everything)
2)Comopiz works with AMD drivers
3)I am going to try that, but i haven't yet come across a 32-bit only package.
4)Never used one of them. (IDE problems have me worried.. anyone tested eclipse???)

Eclipse works flawless, I install that first on Ubuntu before anything else.

---

### Post by rahilm on 2010-08-15
THIS!!


[http://www.omgubuntu.co.uk/2009/12/64bit-flash-ppa.html](http://www.omgubuntu.co.uk/2009/12/64bit-flash-ppa.html)

---

### Post by EN1ac3R on 2010-08-15
Hi,just joined here,so nice to meet you all.

I have just installed Ubuntu Ultimate edition 64bit 2.7 in my VMware 7.0 Which is running on windows 7 64bit.

It is a absolutley fantastic ubuntu..there is also a gamers version as well....
Take a look here,there are shortcuts to all the versions:

[http://ultimateedition.info/](http://ultimateedition.info/),


When the 2.8 version is out,thats when i will do a hd install (only beta now)

It beautifully made,well laid out.
Easy to work around everything and some nice programs included.
Editing programs,movie players,music etc 

I would say to anyone...install this 64bit  linux,you wont be disapointed.

Its got a virtual emulator included aswell-qemulator 0.5-so you can have your favourite other distro by your side as well ( backtrack 4 :)  ),


The only problems i had on installing in VMware 7.0 was that i put the iso in a virtual drive and everytime i entered the desktop it just kept freezing up,installing from the optical drive done the job.
Everytime i boot up i have to use the virtual keyboard to enter the login,but thats okay :)


Well give it a try...

EN1ac3R

---

