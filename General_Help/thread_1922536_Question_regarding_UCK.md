---
title: "Question regarding UCK"
date: 2012-02-09
forum: General Help
---

### Post by sunewbie on 2012-02-09
Hi,

I am an end user and have limited broadband. I want to ask a basic question. 

I have installed Xubuntu 11.10 and then added lot of apps like xubuntu restricted extras, non-free codecs, Libre Office, some KDE apps like Krita, Okular, K3b etc. and changed panel position

Now, I wish to have a backup with all the deb files of installed software and make a customized xubuntu with all apps installed by default.

The question is, if I select manual mode and then select apps from repos, which I have already installed, does UCK / remastersys re-download it from net? 

Does it need any programming knowledge. I do not want to add my custom themes, or change plymounth themes and artwork like login screen, etc. simply add more apps, so that I can have a full backup LIVE DVD (not data files and folders)

Thanks.

---

### Post by Bucky Ball on 2012-02-09
You may want to look here:

[http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html)

Or perhaps consider Clonezilla which is also apparently excellent:

[http://clonezilla.org/](http://clonezilla.org/)

Know what you're saying and have thought about doing the same myself so interested to see how things pan out. Good luck. ;)

PS: I love Xfce DE (the one Xubuntu uses, obviously) and wouldn't want it any other way! :)

PPS: With Clonezilla at least (and I imagine Remastersys also) it is a bare-metal backup; e.g. it backs up what is on your machine, NOT downloading stuff from the net. Hope you get what I mean.

---

### Post by sunewbie on 2012-02-09
> **Bucky Ball said:**
> You may want to look here:

[http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html)

Or perhaps consider Clonezilla which is also apparently excellent:

[http://clonezilla.org/](http://clonezilla.org/)

Know what you're saying and have thought about doing the same myself so interested to see how things pan out. Good luck. ;)

PS: I love Xfce DE (the one Xubuntu uses, obviously) and wouldn't want it any other way! :)

PPS: With Clonezilla at least (and I imagine Remastersys also) it is a bare-metal backup; e.g. it backs up what is on your machine, NOT downloading stuff from the net. Hope you get what I mean.

Hi,

Thanks.

As I understand from your advice, with remastersys or clonezilla, I can make a remaster ISO (LIVE DVD) containing all the apps without net connection. This backups help when you want your friend to test Linux and it has all non-codecs and restricted extras installed.

Just incase of my stupidity (when curiosity wins over common sense like not trying in virtualbox before doing some weird things), I can format and reinstall my remastered Xubuntu without much downloading of apps.

This is one of the reason why I have Bodhi Linux. I was about to install XFCE meta package on it (i did it in virtualbox), but then thought to install Xubuntu.

I love XFCE. it is a DE and not TE like new UNITY and Gnome 3 with Gnome shell (cinnamon is a life saver).

'D' in DE means Desktop and not 'tablet / touch screen' optimized environment. I have 20'' LCD monitor which is 2 feet away. Now image that you keep stretching your hand. Touch Experience will become 'Ouch Experience' :) ;) :D 

I like traditions desktop with icons on my desktop. XFCE and LXDE are the most stable ones these days. UNITY is improving. Lets hope it is implemented well in 12.04.

I think a DE is ideal when it does not draw users attention to itself, but allows one to work without itself getting noticed.

just a personal opinion.

Still I would like to know that UCK does not need internet to make a remaster.

Thanks

---

### Post by Bucky Ball on 2012-02-09
> **sunewbie said:**
> Hi,

Thanks.

As I understand from your advice, with remastersys or clonezilla, I can make a remaster ISO (LIVE DVD) containing all the apps without net connection. This backups help when you want your friend to test Linux and it has all non-codecs and restricted extras installed.

That is how I understand it. You would not have to be connected to the net, it will back up your machine's configuration as is (bare-metal back-up).

> **sunewbie said:**
> Just incase of my stupidity (when curiosity wins over common sense like not trying in virtualbox before doing some weird things), I can format and reinstall my remastered Xubuntu without much downloading of apps.

Without ANY downloading of apps. You will be installing a 'clone' of your system, exactly as it was. Think of it as a 'restore' situation. 

> 
This is one of the reason why I have Bodhi Linux. I was about to install XFCE meta package on it (i did it in virtualbox), but then thought to install Xubuntu.You can install Xfce4 from a package manager (Synaptics, Software Centre) and that is the desktop environment. You don't need to install any meta-package or the complete Xubuntu or xubuntu-desktop (that drags in all Xubutu apps which may/may not be desirable).

> 
I think a DE is ideal when it does not draw users attention to itself, but allows one to work without itself getting noticed.Why I love Xfce. I have keyboard shortcuts for everything; it's plain, simple, functional, reliable, doesn't get in the way. I don't need bells, whistles and disco lights. I just need stability so I can get things done. ;)

---

### Post by sunewbie on 2012-02-09
Hi,
> **Bucky Ball said:**
> 
That is how I understand it. You would not have to be connected to the net, it will back up your machine's configuration as is (bare-metal back-up).

Without ANY downloading of apps. You will be installing a 'clone' of your system, exactly as it was. Think of it as a 'restore' situation. 

Thanks for confirmation.

> **Bucky Ball said:**
> 

You can install Xfce4 from a package manager (Synaptics, Software Centre) and that is the desktop environment. You don't need to install any meta-package or the complete Xubuntu or xubuntu-desktop (that drags in all Xubutu apps which may/may not be desirable).

True, thanks for reminder.
2 apps for each application like terminal, image viewer, DVD burning, is sometimes an annoyance.

> 
Why I love Xfce. I have keyboard shortcuts for everything; it's plain, simple, functional, reliable, doesn't get in the way. I don't need bells, whistles and disco lights. I just need stability so I can get things done. ;)

totally agree +1 :)

---

