---
title: "which ubuntu"
date: 2011-01-05
forum: General Help
---

### Post by Durden10 on 2011-01-05
Dear Community

I recently decided to install ubuntu on an old PC to increase its speed and usability. Prior to this I had windows XP running on it. I installed the newest version of ubuntu, which makes the whole thing running unbearable slow. Under windows xp it was running ok, my question therefore is: which version would you guys recommend that needs less ressources, but still has comparable functionality to the new version?

Thanks a lot!
Durden

---

### Post by NeXTWay on 2011-01-05
If this computer's *very* old, I suggest Lubuntu, which is very fast thanks to the LXDE desktop manager ([http://lubuntu.net/](http://lubuntu.net/)).
Also, it's updated to the 10.10 version (same of Ubuntu stable branch).

---

### Post by claracc on 2011-01-05
It would be good to know the characteristics of the computer to recommend one or other linux distro.

I have an old pIII laptop, 512 Mb RAM and 20 Gb HD, I have tried ubuntu and xubuntu from 8.10 ubuntu release to 9.10, and none of them works well (very slow), but I have tried puppy linux and the speed was very good, and the graphics integrated card ( 64 Mb Ram) and ethernet card inmediatly recognized and working.

You can try this os with the live CD [http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)

---

### Post by sanderd17 on 2011-01-05
If you are a cloud guy, you can try peppermint: [http://peppermintos.com/about-peppermint/](http://peppermintos.com/about-peppermint/)

It is based on Ubuntu (I think the creator of Peppermint an Lubuntu are the same), uses LXDE but it has a lot less of the heavy stuff like openoffice (or libreoffice), printer drivers or other things that can slow your computer down.

As said, peppermint is only good if you want to live in the cloud: there are apps pre-installed for gMail, google docs, youtube ...

Peppermint and Lubuntu work on the same computers, but Peppermint is always a little bit faster.

---

### Post by mastablasta on 2011-01-05
> **Durden10 said:**
> Dear Community
 
I recently decided to install ubuntu on an old PC to increase its speed and usability. Prior to this I had windows XP running on it. I installed the newest version of ubuntu, which makes the whole thing running unbearable slow. Under windows xp it was running ok, my question therefore is: which version would you guys recommend that needs less ressources, but still has comparable functionality to the new version?
 
Thanks a lot!
Durden
 
 
what exactly works slow? what is slow? if computer ran XP ok then Ubuntu should be very fast as it need smuch less resources than winXP. 
 
what are your system specs?
 
it is possible that you forgot to enable proprietary graphics drivers or that your graphics card is not well supported by ubuntu. if graphics card is not supported by Linux then you are out of luck. even if you try Puppy linux and similar suggested distributions.
 
another thing is that certain process consumes too much RAM. it is possible to disable it if it's not a crucial process. sometimes things happen and users experience slowdown with certain configurations.

---

### Post by sanderd17 on 2011-01-05
> **mastablasta said:**
> what exactly works slow? what is slow? if computer ran XP ok then Ubuntu should be very fast as it need smuch less resources than winXP. 
 
what are your system specs?
 
it is possible that you forgot to enable proprietary graphics drivers or that your graphics card is not well supported by ubuntu. if graphics card is not supported by Linux then you are out of luck. even if you try Puppy linux and similar suggested distributions.
 
another thing is that certain process consumes too much RAM. it is possible to disable it if it's not a crucial process. sometimes things happen and users experience slowdown with certain configurations.

I had an old P3 which came witm millenium. I think it had about 198 MB RAM. Win XP worked on it, but Ubuntu and Xubuntu didn't work, even not when killing processes, it was just Gnome and XFCE that took too much RAM. Lubuntu worked well(although I don't think it's advisable to open OpenOffice in Lubuntu in such a low spec computer).

---

### Post by lithopsian on 2011-01-05
Sounds like some people here haven't tried Ubuntu on very old hardware.  Machines that will run Win XP adequately can seem very sluggish in Linux.  It isn't really an issue of resources, more the nature of X server.  Windows has native windowing and responses are still pretty good even when the machine is really slow.  When Linux is a bit shot of horse-power, X server is slow and everything on the desktop *seems* slow even though applications will actually run quite well.

I run Chrunchbang (lightweight Ubuntu 9.04) on a Pentium II 400 with 384MB RAM and everything is just fine but new windows, maximising, file system dialogs, etc can all drag.  Strangely, something really big like Firefox runs just fine once it is finally open :)  Of course Win XP would be useless on this machine.

It would help to know the specs of your machine.  Anything from a Celeron/P4 above about 1.5Ghz with 512MB will run lightweight versions just great, but full Ubuntu comes with a fairly heavy desktop and might be a bit frustrating for you.  More recent versions always seem to get a little bit harder on resources and 10.10 is no exception.

---

### Post by Durden10 on 2011-01-05
thanks for the infos!
I have an AMD athlon with ~500MB RAM as well as a Nvidia graphics card...

The thing is that I need an OS as user-friendly as possible; Lubuntu sound quite similar to Ubuntu, I take it that puppy linux an Peppermint are for the experienced Linux-user only?

---

### Post by Spyderkid on 2011-01-05
Lubuntu is the best for old laptops. Or Xubuntu but I strongly suggest Lubuntu

---

### Post by monkey21stc on 2011-01-05
Have you tried cutting down on the special effects from compiz and selecting minimal effects under Appearance Preference>Visual Effects?

---

### Post by sanderd17 on 2011-01-05
~500 MB is certainly enough for Lubuntu. It would even be enough for ubuntu if you kill certain processes (but you have to know which :P )

I have Lubuntu and use it if I need to work a long time on battery. Gnome with heavy compiz effects eats battery.

About Peppermint: it is also based on Ubuntu and uses the Ubuntu repo's. So it's not more difficult to start with peppermint, but there is a chance that the project is going to be abandoned. In that case, you would have to search a new solution.

Puppy is completely independant and indeed it's a lot harder to install and to manage. But I have never seen a lighter distro than puppy that offers normal desktop tools like a word processor, browser, little games ...

I have Puppy as a live CD. If something is wrong, the live CD boots so fast that you can fix it (or at least get your files of) in no time.

---

### Post by claracc on 2011-01-06
Can be tried lubuntu from live CD without installing to the HD?, I mean without altering your current os installation, as can be done with ubuntu and xubuntu live CDs?.

Thanks in advance.

---

### Post by mastablasta on 2011-01-06
> **Durden10 said:**
> thanks for the infos!
I have an AMD athlon with ~500MB RAM as well as a Nvidia graphics card...
 
The thing is that I need an OS as user-friendly as possible; Lubuntu sound quite similar to Ubuntu, I take it that puppy linux an Peppermint are for the experienced Linux-user only?
 
 
it could be poor opensoruce nvidia drivers that are making it slow.
 
as suggested try turning off special desktop effects. switch to easier desktop theme (such as clearlooks) see if that helps.
 
even Kubuntu should run on your setup (looks a lot closer to windows).
 
you could try to install XFCE (and then select it before login), no need to do full xubuntu install. it should run much faster. but 500MB should be plenty for ubuntu.
 
Puppy linux works in a different way (for example user is always root if i am not mistaking). is also quite easy, but maybe doen't have so many programmes in repositories. peppermintOS is like Lubuntu (based on LXDE) an is ment for cloud computing. for example instead of open office it will have a launcher that will connect you to google docs. 
 
> **claracc said:**
> Can be tried lubuntu from live CD without installing to the HD?, I mean without altering your current os installation, as can be done with ubuntu and xubuntu live CDs?.
 
Thanks in advance.
 
 
yes it can. so can MintLXDE (but it is a bit heavier). if you are looking for somethig really light try slitaz.

---

### Post by cascade9 on 2011-01-06
If you still have ubuntu on that machine, I'd have a play with DEs before you go installing lubuntu or anything like that. 

sudo apt-get install xfce4 

and/or 

sudo apt-get install lxde 

[http://packages.ubuntu.com/maverick/xfce4](http://packages.ubuntu.com/maverick/xfce4)
[http://packages.ubuntu.com/maverick/lxde](http://packages.ubuntu.com/maverick/lxde)

You wont have to pull that much down from the repos, you can get a look at xfce and lxde, and I wouldnt be suprised if either of them turned sluggish into decent. 

Once you've installed xfce or lxde, logout (or reboot), then choose the DE you want from GDM (login screen).

*edit- thats what I get for hitting 'post' then walking away...mastablasta posts pretty much what I was going to. 

BTW, xfce on top of ubuntu is faster than xubuntu in my experience. KDE 4.X wil probably run on that machine, but unless its a fast athlon (not an 'athlon classic', t-birds and athlon XP would be OK) and got at least a 5XXX (FX series) nvidia card, its going to run really badly.

---

### Post by Durden10 on 2011-01-10
@cascada9: thanks a lot! I just installed xfce4 and it works flawless an fast!

---

### Post by cascade9 on 2011-01-10
:) Nice, enjoy! :)

---

