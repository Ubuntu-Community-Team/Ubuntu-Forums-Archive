---
title: "Clean Install of Ubuntu 11"
date: 2011-12-04
forum: General Help
---

### Post by Arcx500 on 2011-12-04
I want to perform another clean install of Ubuntu. A stand alone OS.

However my last attempt made it impossibe for me to stay with Ubuntu.

When I previously performed a clean install on my computer, during the installation it was checking if I have a working network connection and it did and installed with no problems. 

When I got to the desktop, I didn't have any internet. Even after choosing eth0 just to be certain I'm connected but ended up receiving a window saying "You've been disconnected."

I tried looking up this problem but none of them matched my problem so before I try again, can I get help with this?

EDIT : Strangest thing is, if I install it within Windows (Wubi) then I have no problems at all but the limit is 30gb wich isn't enough.

---

### Post by oldtimer7777 on 2011-12-04
Try using a walk-through first this time, to help guide you through the entire process of getting everything configured just right:

[https://debianhelp.wordpress.com/201...neiric-ocelot/]("https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/")

Usually that resolves many of these kinds of issues.    After that point from trying the checklist step-by-step, just let us know what the errors look like so we can help you.


> **Arcx500 said:**
> I want to perform another clean install of Ubuntu. A stand alone OS.

However my last attempt made it impossibe for me to stay with Ubuntu.

When I previously performed a clean install on my computer, during the installation it was checking if I have a working network connection and it did and installed with no problems. 

When I got to the desktop, I didn't have any internet. Even after choosing eth0 just to be certain I'm connected but ended up receiving a window saying "You've been disconnected."

I tried looking up this problem but none of them matched my problem so before I try again, can I get help with this?

---

### Post by Arcx500 on 2011-12-04
> **oldtimer7777 said:**
> Try using a walk-through first this time, to help guide you through the entire process of getting everything configured just right:

[https://debianhelp.wordpress.com/201...neiric-ocelot/]("https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/")

Usually that resolves many of these kinds of issues.    After that point from trying the checklist step-by-step, just let us know what the errors look like so we can help you.

I'll look at it but as far as I read, I didn't see anything about checking network settings.

---

### Post by oldtimer7777 on 2011-12-04
> **Arcx500 said:**
> I'll look at it but as far as I read, I didn't see anything about checking network settings.

What I would simply do in your particular situation is use a hardwired Ethernet line to my router.  If you don't have those, you need to purchase them.  Keep it hardwired all the way through the installation process.  Once you have your system installed, and updated, and any packages upgraded...  You have gone through the above checklist very throughly and deligently, then you can set up your wifi connection.   If your Wifi isn't supported on the Ubuntu Kernal automatically, you can use Ndiswrapper and installed the window driver for your make/model laptop wifi adapter that way.   If that is case, you can always return here and ask how to install Ndiswrapper, and we can help guide you through that process if need be. 

What many users do is simply install everything over the Wifi connection instead, and they come here reporting all kinds of trouble with their systems afterwards, so it is best to use a fast hardwired Ethernet connection initially when installing and making sure you system has everything it needs to hit the ground running.  It just makes more sense that way.

---

### Post by Arcx500 on 2011-12-04
> **oldtimer7777 said:**
> What I would simply do in your particular situation is use a hardwired Ethernet line to my router.  If you don't have those, you need to purchase them.  Keep it hardwired all the way through the installation process.  Once you have your system installed, and updated, and any packages upgraded...  You have gone through the above checklist very throughly and deligently, then you can set up your wifi connection.   If your Wifi isn't supported on the Ubuntu Kernal automatically, you can use Ndiswrapper and installed the window driver for your make/model laptop wifi adapter that way.   If that is case, you can always return here and ask how to install Ndiswrapper, and we can help guide you through that process if need be. 

What many users do is simply install everything over the Wifi connection instead, and they come here reporting all kinds of trouble with their systems afterwards, so it is best to use a fast hardwired Ethernet connection initially when installing and making sure you system has everything it needs to hit the ground running.  It just makes more sense that way.

With hardwired, you're just talking about a network cable being connected to my desktop right? It's a desktop and is always wired. I still find it strange that it worked with Wubi.

---

### Post by oldtimer7777 on 2011-12-04
> **Arcx500 said:**
> With hardwired, you're just talking about a network cable being connected to my desktop right? It's a desktop and is always wired. I still find it strange that it worked with Wubi.

Don't use Wubi.  Wubi is for a very limited test drive of Ubuntu.  Always install freshly with a hardwired connection.  Wifi installation/configurations are dead last when it comes to installing Ubuntu, if you want the job done right the first time.  Hardwired Ethernet solves this problem entirely.  When you done completely with the above checklist link, then you can worry about your Wifi.  Wifi can be installed several ways, so not to worry.

---

### Post by vasa1 on 2011-12-04
> **oldtimer7777 said:**
> Try using a walk-through first this time, to help guide you through the entire process of getting everything configured just right:

[https://debianhelp.wordpress.com/201...neiric-ocelot/]("https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/")
...

Just curious ... why do you recommend that particular link? From what I've seen, the author doesn't really care that much about 11.10 and is more concerned with guiding users on how to make 11.10 work like an older system that the author prefers.

I could give specific quotes but the slant is pretty obvious. I really wouldn't recommend that link to anyone interested in using 11.10 as 11.10.

There was nothing that I could see in the OP indicating that OP wanted to install 11.10 but make it behave like some other OS. OP has (or had) a very specific issue,

---

### Post by oldtimer7777 on 2011-12-04
> **vasa1 said:**
> Just curious ... why do you recommend that particular link? From what I've seen, the author doesn't really care that much about 11.10 and is more concerned with guiding users on how to make 11.10 work like an older system that the author prefers.

I could give specific quotes but the slant is pretty obvious. I really wouldn't recommend that link to anyone interested in using 11.10 as 11.10.

There was nothing that I could see in the OP indicating that OP wanted to install 11.10 but make it behave like some other OS. OP has (or had) a very specific issue, 

I think the author of that How-to guide was being honest, that's all. Might save someone time.. I don't know.  If you have a problem with that, maybe you should take it up with them instead of posting your opinion here. This is a help group. Not a Unity fan club meeting. Get over it.

---

### Post by vasa1 on 2011-12-04
> **oldtimer7777 said:**
> I think the author of that How-to guide was being honest, that's all. Might save someone time.. I don't know.  If you have a problem with that, maybe you should take it up with them instead of posting your opinion here. This is a help group. Not a Unity fan club meeting. Get over it.

There's nothing to get over. I'll state it bluntly. That link is not helpful to the present case.

---

### Post by oldtimer7777 on 2011-12-04
> **vasa1 said:**
> There's nothing to get over. I'll state it bluntly. That link is not helpful to the present case.

Well you are mistaken. The user wants to learn how to install Ubuntu. That is what the link is meant to accomplish for someone who is new to Ubuntu.  Just because it doesn't specifically have anything positive to say about Unity is completely irrelevant to helping someone install Ubuntu on their computer for the first time. You don't have to use -only- unity to install Ubuntu. Again, just get over it and move on. This is a general help group, not a unity fan club. Who are you to say what's what anyhow? Why don't you chat it up in the cafe section Vasa, if that is what you prefer, because this is help group. Sorry.

---

### Post by vasa1 on 2011-12-05
I won't respond to your *ad hominem* comments.

I hope someone can help OP solve the network issue, which is what the problem appears to be from the first post:
> When I got to the desktop, I didn't have any internet. Even after choosing eth0 just to be certain I'm connected but ended up receiving a window saying "You've been disconnected."

---

### Post by Arcx500 on 2011-12-05
> **vasa1 said:**
> I won't respond to your *ad hominem* comments.

I hope someone can help OP solve the network issue, which is what the problem appears to be from the first post:

Thanks, I hope so too.

---

### Post by oldtimer7777 on 2011-12-05
> **Arcx500 said:**
> Thanks, I hope so too.

Well we aren't mind-readers.  If you want help with something like this you will need to post more specific information about what is happening after you install Ubuntu.   And as for Vasa, I have no idea what they are talking about here.  Unity has nothing to do with Internet Connectivity like this user is reporting in the General Help Forum.. Vasa, the issue has nothing to do with Desktop Environment, so I don't even know why you bother bringing it up in the first place, and whether or not a user is installing from Unity or Gnome, or LXDE, it has to do with something else other than the Desktop Environment. All you did Vasa, was attack the link I provided simply because you don't like what it has to say about your precious Unity, and that is well, your opinion Vasa.  Maybe you helped design Unity or something and when a web site say something negative about Unity you get upset about it and take it personally, because whatever you have to say at this point is certainly not helpful either, and this is what I see Vasa doing here. 

If you use the walk-through that I provided you with, and you reinstall your system that way, and post more information about what your connection looks like after you have a clean installation, so we can figure out your issue with Internet Connectivity, maybe we can actually fix it?? If that is what you need, then try to follow instructions. Otherwise, let me tell you, do you have a long wait because I'm not here to argue about which is the best Desktop Environment, understand that.. so Vasa you take your opinion elsewhere, and you have nothing to say to help this user at all at this point either.. Don't take it so personally.

Are you using Wifi or Ethernet to connect?  What does ipconfig say about your eth0 connection information when it works from the Live Ubuntu installation disc or USB?  Are you using a router or not? etc etc etc..  The more information, the better. Details... details.. details..

If you want help, that's how you get it. Again, Desktop Environment has zero to do with solving this issue, so don't listen to Vasa, and their personal opinions that aren't helpful to your specific issue.  If someone wants to help, by all means, help.  Take your opinion about the links to the person who wrote those pages. Not here.

---

### Post by Arcx500 on 2011-12-07
> **oldtimer7777 said:**
> Well we aren't mind-readers.  If you want help with something like this you will need to post more specific information about what is happening after you install Ubuntu.   And as for Vasa, I have no idea what they are talking about here.  Unity has nothing to do with Internet Connectivity like this user is reporting in the General Help Forum.. Vasa, the issue has nothing to do with Desktop Environment, so I don't even know why you bother bringing it up in the first place, and whether or not a user is installing from Unity or Gnome, or LXDE, it has to do with something else other than the Desktop Environment. All you did Vasa, was attack the link I provided simply because you don't like what it has to say about your precious Unity, and that is well, your opinion Vasa.  Maybe you helped design Unity or something and when a web site say something negative about Unity you get upset about it and take it personally, because whatever you have to say at this point is certainly not helpful either, and this is what I see Vasa doing here. 

If you use the walk-through that I provided you with, and you reinstall your system that way, and post more information about what your connection looks like after you have a clean installation, so we can figure out your issue with Internet Connectivity, maybe we can actually fix it?? If that is what you need, then try to follow instructions. Otherwise, let me tell you, do you have a long wait because I'm not here to argue about which is the best Desktop Environment, understand that.. so Vasa you take your opinion elsewhere, and you have nothing to say to help this user at all at this point either.. Don't take it so personally.

Are you using Wifi or Ethernet to connect?  What does ipconfig say about your eth0 connection information when it works from the Live Ubuntu installation disc or USB?  Are you using a router or not? etc etc etc..  The more information, the better. Details... details.. details..

If you want help, that's how you get it. Again, Desktop Environment has zero to do with solving this issue, so don't listen to Vasa, and their personal opinions that aren't helpful to your specific issue.  If someone wants to help, by all means, help.  Take your opinion about the links to the person who wrote those pages. Not here.
I don't believe I can make it more clear by saying "After the clean install, my wired internet was not working." I also stated as the setup checks if you have a good network connection before even starting that it was working fine. I'm directly connected to the modem. It works perfectly fine on Windows and it also works fine when using Wubi. Just as I said before, I found it strange that Wubi gave me no network problems at all but when I performed a clean install it did. As from your attitude, I don't think you can help me if you direct me to a website that guides you through a clean install when I specifically said that I have a network problem. To me, it seems that you can't take rejection when I don't find your support helpful. I think it's you who shouldn't take me personal.

---

### Post by oldtimer7777 on 2011-12-07
Take you personally? Please...  I beg your pardon...

If you want help, we need more information than "it don't work"... 

We need specifics. We need to know what IPCONFIG says about that network conection after you do a clean install.  I was about to get that part of the diagnosis before I was very rudely interrupted by this irate Vasa character telling me he doesn't like my link because it insults his precious Unity, and absolutely nothing else to add to help you with your problem either... Vasa, if that is the best you can do, we don't need it here. Give me a break here.   You want help? Follow instructions.  Learn something new.  If you want to talk about how great Unity is, take it to the cafe and let me help users that truly want help. Thank you very much...

Explaining to a new user to try a walk-through for installing Ubuntu 11.10 isn't a bad idea (it actually makes a great deal of sense, and will save you time) if they are having Internet connectivity issues after doing a clean installation.  There are many things that can easily go wrong during a fresh installation if they are new to Ubuntu, and that is why I recommended the link to you for your problem with Internet connectivity after doing a fresh installation of Ubuntu 11.10.  That link absolutely applies to you in your particular situation too.

After you follow a guide, at least we can sure that you are doing a proper installation of Ubuntu 11.10.   And get that out of the way.  You are saying to us, that this link shouldn't have to apply in your case because it works fine in Wubi and Windows on your computer..   Great, but I don't use either of those kinds of ways to get my internet connectivity to work on a fresh installation of Ubuntu, so that is what the link is for.  Nothing personal because that is just the way I do it here.  If you don't like it, or you don't like my links, guess what? Stop wasting my time. You can wait around for someone to answer your questions that will -not- require you to do any more work than you obviously feel like accomplishing today, or that you feel you have already done enough of to solve your particular issues. Understand that,  I'm not here to play these games with users who want paid support or whatever.  You want someone to be a mind-reader or whatever. By all means, hire someone to fix your issues, and this problem will be solved and you won't have to do anything about it except pay them your hard earned money and relax... In your particular situation that might be a really terrific idea, and I mean absolutely nothing personally by saying that either.  Goodluck with that issue with Internet Connectivity on a fresh installation of Ubuntu 11.10.

> **Arcx500 said:**
> I don't believe I can make it more clear by saying "After the clean install, my wired internet was not working." I also stated as the setup checks if you have a good network connection before even starting that it was working fine. I'm directly connected to the modem. It works perfectly fine on Windows and it also works fine when using Wubi. Just as I said before, I found it strange that Wubi gave me no network problems at all but when I performed a clean install it did. As from your attitude, I don't think you can help me if you direct me to a website that guides you through a clean install when I specifically said that I have a network problem. To me, it seems that you can't take rejection when I don't find your support helpful. I think it's you who shouldn't take me personal.

---

### Post by kdane4 on 2011-12-07
> **Arcx500 said:**
> I want to perform another clean install of Ubuntu. A stand alone OS.

However my last attempt made it impossibe for me to stay with Ubuntu.

When I previously performed a clean install on my computer, during the installation it was checking if I have a working network connection and it did and installed with no problems. 

When I got to the desktop, I didn't have any internet. Even after choosing eth0 just to be certain I'm connected but ended up receiving a window saying "You've been disconnected."

I tried looking up this problem but none of them matched my problem so before I try again, can I get help with this?

EDIT : Strangest thing is, if I install it within Windows (Wubi) then I have no problems at all but the limit is 30gb wich isn't enough.

Are you able  to connect to the  internet using just the LIVE CD? maybe an update went haywire when it was installed that's why it stopped working. I also advice doing another thread (or just linking this one) on the* Networking and Wireless* forum instead of *General Help*.

:)

---

### Post by DapperMe17 on 2011-12-07
Arcx500,

I find the link provided by oldtimer to be absolutely fantastic, and very helpful to a clean installation. 

If you've ran Ubuntu off of a LiveCD, and can connect automatically, then installation to the HD will provide the very same result. 

Oldtimer has asked you for more specific details, and that's what you will need to provide. 

:roll:

---

### Post by Jive Turkey on 2011-12-07
I don't think that an additional install is really what you need.  You probably just need to do a bit of tweaking to your network settings to get your internet connection up.

If you post the output of the "ifconfig" and "cat /etc/network/interfaces" commands with some explanation of which interfaces (network cards/plugs) you are using we should be able to get you going.  I recently installed the 11.10 server edition with only a wireless connection and had no problems whatsoever and the installer was able to use my wifi card to make a WPA2 connection to my neighbor's router and get the latest packages.  

If you are having trouble with using wifi it might be a driver issue and somebody has probably solved it in the recent past.  If you are having issues connecting via wired connection to your router or modem we may have to do more digging.

I won't personally be able to respond until tomorrow but many people are here to help in the meantime.

some commands that might help to get your connection up are "sudo /etc/init.d/networking restart" (restarts your networking config) and "ifdown -a" (takes down all network interfaces) followed by "ifup -a" brings them back up, (don't forget to use sudo). 

I scanned the thread after writing the first part of this post and I see you are connected directly to the modem, does your ISP require you to use any kind of password or anything like that?

---

### Post by oldtimer7777 on 2011-12-07
Take you personally? Please...  I beg your pardon...

If you want help, we need more information than "it don't work"... 

We need specifics. We need to know what IPCONFIG says about that network connection after you do a clean install.  I was about to get to that part of the diagnosis before I was very rudely interrupted by this irate Vasa character telling me he doesn't like my link because it insults his precious Unity, and they having absolutely nothing else to add to help you with your problem either... Vasa, if that is the best you can do, we don't need it. Give me a break.   You want real help? Follow instructions.  Learn something new.  If you want to talk about how great Unity is, take it to the cafe forum and let me help users that truly want my help. Thank you very much...

Explaining to a new user to try a walk-through explaining the proper installation Ubuntu 11.10 isn't a bad idea (it actually makes a great deal of sense, and will save time) esp. if they are having Internet connectivity issues after doing a clean installation.  There are many things that can easily go wrong during a fresh installation if they are new to Ubuntu, and that is why I recommended the link to you for your problem with Internet connectivity after doing a fresh installation of Ubuntu 11.10.  That link absolutely applies to you in your particular situation.

After you follow a guide, at least we can be sure that you are doing a proper installation of Ubuntu 11.10 and also so we can get that out of the way.  You are saying to us, that this link shouldn't have to apply in your case because it works just fine in Wubi and Windows on your computer..   Great for Wubi and Windows, but I don't use either of those kinds of ways to get my internet connectivity to work on a fresh installation of Ubuntu, so that is what the link is for.  Nothing personal because that is just the way I do it here.  If you don't like it, or you don't like my links, guess what? Stop wasting my time. You can wait around for someone to answer your questions that will -not- require you to do any more work than you obviously feel like accomplishing today, or that you feel you have already done enough of to solve your particular issues. Understand that,  I'm not here to play these passive-aggressive games with users who expect paid support or whatever or if they feel that they want someone to be a mind-reader regarding their problems or whatever. By all means, hire someone to fix your issues, and this problem will be solved quickly and you won't have to do anything about it except pay them your hard earned money and relax... In your particular situation that might be a really terrific idea, and I mean absolutely nothing personally by saying that either.  Goodluck with that issue with Internet Connectivity on a fresh installation of Ubuntu 11.10.

---

