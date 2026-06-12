---
title: "I'm done with Ubuntu...Suggestions?!?!"
date: 2009-07-13
forum: General Help
---

### Post by AdamShumpisxXx on 2009-07-13
I'm moving on. I have Windows XP Professional x64 SP2 on one 40GB partition and now I'm looking for a new version of Linux on the other 40GB partition. My needs are as follows:

1) Has to be able to support the ATI Catalyst 9.3 drivers for my Sapphire x1950xt card. This is the main reason why I'm skipping out on Ubuntu 9.04 Jaunty.

2) Has to have KDE either as the default or as an option at OS install. I don't know what version is best so that's where I need the help, haha.

3) Not really 100% mandatory but I'd really like it to have awesome support like you guys give here at Ubuntu Forums. I'll be new to it (more than likely) so I may need some help.

Well, if you guys can do anything for me that would be AWESOME. I tried searching the internet for weeks now and I can't find a definitive solution on this ATI Catalyst 9.3 thing. OK, thanks in advance!

---

### Post by theozzlives on 2009-07-13
KDE is default in Kubuntu, and an option in Ubuntu.

---

### Post by rivenathos on 2009-07-13
You may wish to consider Mandriva, openSUSE, Fedora, or possibly Sabayon.  They are all different enough from Debian and Ubuntu.  I know Mandriva and openSUSE have some really great implementations of KDE.

---

### Post by lukeiamyourfather on 2009-07-13
Ubuntu 8.04 LTS since it uses an older Xserver. No need to switch to a completely different distribution. Cheers!

---

### Post by AdamShumpisxXx on 2009-07-13
> **theozzlives said:**
> KDE is default in Kubuntu, and an option in Ubuntu.

Any Jaunty version of Ubuntu isn't compatible with my Sapphire x1950xt card. The version of Xorg used apparently won't work with anything Catalyst 9.3 or below and my card isn't supported with Catalyst 9.4...Anyone else?

---

### Post by AdamShumpisxXx on 2009-07-13
> **rivenathos said:**
> You may wish to consider Mandriva, openSUSE, Fedora, or possibly Sabayon.  They are all different enough from Debian and Ubuntu.  I know Mandriva and openSUSE have some really great implementations of KDE.

Can you verify any of those being compatible with my situation because through my own searches I can not. That's why I'm asking here. Thanks.

---

### Post by hibliss on 2009-07-13
I vote OpenSuse. It gives you the option of KDE or Gnome on install, and I would be surprised if it did not support your video card, as it is the Open source development wing of SLED.

---

### Post by AdamShumpisxXx on 2009-07-13
> **lukeiamyourfather said:**
> Ubuntu 8.04 LTS since it uses an older Xserver. No need to switch to a completely different distribution. Cheers!

This exact option is the one I've been keeping in my back pocket as I know it will work but I'm looking for something new. I might be forced to use it though...Unless someone has an alternative that fits my problems?

---

### Post by AdamShumpisxXx on 2009-07-13
> **hibliss said:**
> I vote OpenSuse. It gives you the option of KDE or Gnome on install, and I would be surprised if it did not support your video card, as it is the Open source development wing of SLED.

OK, cool. I'll give it a look. It not only has to be compatible but it has to be able to use the proprietary ATI Catalyst 9.3 driver. If I wasn't worried about that then I'd just use Kubuntu 9.04 Jaunty. Thanks!

---

### Post by twright on 2009-07-13
I don't think any modern distros support the old ATI driver any more and if they do now they will not for long.

Have you tried just using the open source drivers? On my laptop they work really well with compiz running fast etc., you might notice problems with gaming but that is what dual boots are for.

Otherwise you could just try downgrading x on whichever distro you choose to use.

---

### Post by AdamShumpisxXx on 2009-07-13
> **twright said:**
> I don't think any modern distros support the old ATI driver any more and if they do now they will not for long.

Have you tried just using the open source drivers? On my laptop they work really well with compiz running fast etc., you might notice problems with gaming but that is what dual boots are for.

Otherwise you could just try downgrading x on whichever distro you choose to use.

Now this is what I am talking about. Let's just say I would like to use Kubuntu 9.04 Jaunty. How would you elect that I downgrade X to before 1.6 when it stopped supporting 9.3 and downward? Any answers would be AWESOME! If not Kubuntu...any other distribution that you are fluent with on the subject of downgrading X would be fine. Thank you very much!

---

### Post by AdamShumpisxXx on 2009-07-13
Bump...

---

### Post by t4thfavor on 2009-07-13
Its really sad that ATI stopped putting out competent drivers, maybe instead of changing OS's think about changing hw vendors.

I have some old nvidia cards that work great. 


You have to ask yourself why the X server stopped supporting that card. I bet it isn't because the hardware changed since the last driver, but that the ATI driver has changed to the point of it being one or the other.

Oh yeah,
+1 on the open source driver, and then new hardware.

---

### Post by AdamShumpisxXx on 2009-07-13
> **t4thfavor said:**
> Its really sad that ATI stopped putting out competent drivers, maybe instead of changing OS's think about changing hw vendors.

I have some old nvidia cards that work great. 


You have to ask yourself why the X server stopped supporting that card. I bet it isn't because the hardware changed since the last driver, but that the ATI driver has changed to the point of it being one or the other.

Oh yeah,
+1 on the open source driver, and then new hardware.

I'm not about the change my hardware to suite an OS. My AMD / ATI combo is amazing. I dislike nVidia / Intel greatly. I can play any game on my Windows partition new or old on the highest settings (I'm currently playing Prototype now).

Any helpful suggestions appreciated.

---

### Post by Arup on 2009-07-13
Try Fedora 11 which is more friendlier with older cards.

---

### Post by AdamShumpisxXx on 2009-07-13
> **Arup said:**
> Try Fedora 11 which is more friendlier with older cards.

Thank you very much. I actually just took this test:

[http://www.zegeniestudios.net/ldc/](http://www.zegeniestudios.net/ldc/)

...And it led me right to Fedora and OpenSUSE. What, in your opinion, is better? I am on the fence with either one at the moment. Thanks!

---

### Post by t4thfavor on 2009-07-13
> **AdamShumpisxXx said:**
> I'm not about the change my hardware to suite an OS. My AMD / ATI combo is amazing. I dislike nVidia / Intel greatly. I can play any game on my Windows partition new or old on the highest settings (I'm currently playing Prototype now).

Any helpful suggestions appreciated.

You won't be saying that when they discontinue support for your card under Windows, which will happen. I used to be AMD/ATI all the way. The company as a whole has taken a down turn as of late, and I am afraid that an intel/Nvidia combo will beat the pants off its AMD/ATI counterpart for around the same price (especially in Linux).


I gave up on my 9600XT (6 years old?) while I still have Nvidia 56xx series cards humming away afer 6-7 years.


As always this is just my opinion.

---

### Post by Arup on 2009-07-13
> **AdamShumpisxXx said:**
> Thank you very much. I actually just took this test:

[http://www.zegeniestudios.net/ldc/](http://www.zegeniestudios.net/ldc/)

...And it led me right to Fedora and OpenSUSE. What, in your opinion, is better? I am on the fence with either one at the moment. Thanks!

My suggestion would be for Fedora 11, its newer and more cutting edge. Make sure to enable RPM Fusion repositories and yum presto. Its quirky to setup and frustrating at times but once done, its rock solid and quick.

---

### Post by AdamShumpisxXx on 2009-07-13
> **Arup said:**
> My suggestion would be for Fedora 11, its newer and more cutting edge. Make sure to enable RPM Fusion repositories and yum presto. Its quirky to setup and frustrating at times but once done, its rock solid and quick.

Thank you VERY much! If all votes are in I think I'll be going over to Fedora...If I need any help would it be cool to contact you through a PM?

---

### Post by Arup on 2009-07-13
> **AdamShumpisxXx said:**
> Thank you VERY much! If all votes are in I think I'll be going over to Fedora...If I need any help would it be cool to contact you through a PM?

Sure, and there are other Fedora experts here at the forum as well and many sites as well as an helpful Fedora forum. Fedora guide is one such helpful website among many others.

---

### Post by Vakman on 2009-07-13
You said that you had Ubuntu 8.04 In your back pocket. You may want to try out Linux Mint. It is based off Ubuntu and each release follows Ubuntu. So Mint 5 is based on 8.04 and is also their LTS version. Will feel new and the same but at least you know everything will work. I also find Mint to be far faster than Ubuntu in many cases. The LiveCD is really fast as is the install. I use Mint 7 as my distro. 

P.s. I liked Fedora but openSUSE I found to be trouble with my 4850s. Also on other machines I found it to be really slow in general. My vote is easily Mint though.

---

### Post by AdamShumpisxXx on 2009-07-13
> **Thisislaw said:**
> You said that you had Ubuntu 8.04 In your back pocket. You may want to try out Linux Mint. It is based off Ubuntu and each release follows Ubuntu. So Mint 5 is based on 8.04 and is also their LTS version. Will feel new and the same but at least you know everything will work. I also find Mint to be far faster than Ubuntu in many cases. The LiveCD is really fast as is the install. I use Mint 7 as my distro. 

P.s. I liked Fedora but openSUSE I found to be trouble with my 4850s. Also on other machines I found it to be really slow in general. My vote is easily Mint though.

Thanks but I tried Mint previously. If I was going back to Ubuntu 8.04 I'd go the Kubuntu route and customize it myself without employing the use of a pre-customized OS like Mint. Thank you for the suggestion though!

---

### Post by ghostborg on 2009-07-13
My suggestion would be to stay with XP and run Ubuntu in a VirtualBox, or just forget about Ubuntu. I mean if it is too difficult then why bother, just move on. I would.
Good Luck to you in whatever you decide.

---

### Post by AdamShumpisxXx on 2009-07-13
> **ghostborg said:**
> My suggestion would be to stay with XP and run Ubuntu in a VirtualBox, or just forget about Ubuntu. I mean if it is too difficult then why bother, just move on. I would.
Good Luck to you in whatever you decide.

I'm keeping my XP partition for gaming and Adobe Premiere CS3 Pro and nothing else. I like to use Linux distributions for everything else as they are safer, faster, and more efficient. Thanks!

---

### Post by Vakman on 2009-07-13
> **AdamShumpisxXx said:**
> Thanks but I tried Mint previously. If I was going back to Ubuntu 8.04 I'd go the Kubuntu route and customize it myself without employing the use of a pre-customized OS like Mint. Thank you for the suggestion though!

I see then. Well if you are choosing between Fedora or openSUSE. Fedora certainly gets my vote. Good luck.

---

### Post by AdamShumpisxXx on 2009-07-13
> **Thisislaw said:**
> I see then. Well if you are choosing between Fedora or openSUSE. Fedora certainly gets my vote. Good luck.

Thanks.

---

### Post by twright on 2009-07-14
> **AdamShumpisxXx said:**
> Now this is what I am talking about. Let's just say I would like to use Kubuntu 9.04 Jaunty. How would you elect that I downgrade X to before 1.6 when it stopped supporting 9.3 and downward? Any answers would be AWESOME! If not Kubuntu...any other distribution that you are fluent with on the subject of downgrading X would be fine. Thank you very much!
Hi,
you should be able to downgrade the xserver using the instructions in this thread:
[http://ubuntuforums.org/showthread.php?t=1171445](http://ubuntuforums.org/showthread.php?t=1171445)

It won't keep working for ever (as the xserver and the drivers become more and more out of date) but then there are always the open source drivers which are getting better all the time.

---

### Post by lukeiamyourfather on 2009-07-14
> **AdamShumpisxXx said:**
> ...but I'm looking for something new.

Yes, and that's why it doesn't work in the first place. There's usually a good few months of lag between the newest whatever and what vendors (like AMD/ATi) can support. Cheers!

---

