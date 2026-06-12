---
title: "Really: How to get rid of virtuoso-t and nepomuk?"
date: 2010-05-25
forum: General Help
---

### Post by Zeemvel on 2010-05-25
Whenever I boot up ubuntu, virtuoso-t, nepomukserver and 8 instances of a nepomukservices process run, and these DO really slow my system a lot, giving slow response of GUI apps etc...

I tried asking before, but nobody knew. I'd like to keep trying:

How can I get rid of these processes. What starts them up? I want to remove the command that starts them from which ever config file it is.

Thanks.

NOTE: disabling the desktop search setting in KDE settings does NOT disable these 10 executables that slow down your system. Going to KDE control center and disabling nepomuk there isn't the answer. I'd like to know the config file please :)

---

### Post by James78 on 2010-05-25
Why don't you just go to System Settings->Advanced->Desktop Search, and uncheck "Enable Nepomuk Semantic Desktop"? It works for me, and it doesn't turn on at startup.

---

### Post by Zeemvel on 2010-05-25
> **James78 said:**
> Why don't you just go to System Settings->Advanced->Desktop Search, and uncheck "Enable Nepomuk Semantic Desktop"? It works for me, and it doesn't turn on at startup.

But it really doesn't work for me. I disabled that. But when I boot up, the 10 executables mentioned above are running.

Really, does anyone know WHAT starts up these services and HOW it does that?

In MS Windows, I'd use msconfig to get rid of such offensive application. msconfig shows all possible ways applications can automatically get started at bootup in Windows.

What ways to start up applications are there in Ubuntu, and which one of those is used by nepomuk?

I just don't want to see nepomuk again. Its own setting doesn't help.

---

### Post by James78 on 2010-05-25
You can try removing "virtuoso-nepomuk" using Synaptic. From what I checked in the dependencies, there is no ill effect to be received by removing it completely, but a fair word of warning, it IS possible. Considering KDE asks to install it to get the functionality of it, (I've seen this happen while kubuntu-desktop was already installed) it should be fine.

The startup methods are run-level (use sudo [sysv-rc-conf]("apt:sysv-rc-conf") to edit the entries), ~/.config/autostart, ~/.kde/Autostart, ~/.kde/env. The .kde entries can already be edited via the Autostart tool in System Settings. There may be a few more I forgot to list.

P.S. Config files for KDE are kept in ~/.kde/share/config/

---

### Post by Zeemvel on 2010-05-25
Removing "virtuoso-nepomuk" isn't ideal:

Then it gives a message at startup that nepomuk needs virtuoso. And if I do "ps -eal | grep nep", I still see two processes "nepomukserver" running.

nepomuk has been ruining my ubuntu experience, so one can understand that I don't even want to see its name anymore, not in the processes, not in a message at startup.

---

### Post by James78 on 2010-05-25
See if nepomuk is listed in the autostart folders I listed earlier, also, check out /usr/share/autostart.

---

### Post by Zeemvel on 2010-05-25
> **James78 said:**
> See if nepomuk is listed in the autostart folders I listed earlier, also, check out /usr/share/autostart.

Aha, that's the one!!

There's a file "nepomukserver.desktop" in there.

Thanks.

---

### Post by James78 on 2010-05-25
> **Zeemvel said:**
> Aha, that's the one!!

There's a file "nepomukserver.desktop" in there.

Thanks.
No problem. :)

---

### Post by CHaoSlayeR on 2010-06-06
Ah.... finally!

Thanx a lot for this thread!. Those two "services" turned my new workstation into a lame something. For sure the wrong thing for a dev machine.

---

### Post by jcottier on 2010-09-07
I am using kde4 kmail on Ubuntu (gnome desktop) 10.04 and I have been plagued by nepomukservices and virtuoso-t gobbling up massive amounts of CPU % apparently at random. I used a system monitor panel indicator watch CPU and keep shutting it down its services upteen times a day.

I have now uninstalled virtuoso-t, but could not find any entries in /usr/share/autostart. I eventually found this:-
/usr/share/kde4/servicetypes/nepomukservice.desktop
and removed it. This has got rid of the error message complaining about nepomuk database not running and I now have a nice flat almost zero CPU % at idle. There is still one "nepomukserver" service running, but it consumes no CPU juice so far.

---

### Post by fixitdude on 2012-06-22
Who the hell thought something that takes RAM and CPU like this thing does is a good thing?

OH I KNOW!! A developer with lots of money and lots of RAM and a super expensive CPU!! Yes, everyone has that! Good thinking!

I am so tired of this.

I also wonder if someone from microscroft has infiltrated Ubuntu and started putting junk in so that it makes Ubuntu look bad. You can't install this for your mom anymore, it's just too much crap that gets confusing. And trying to support people you have installed this for is getting to be a nightmare for upgrading, and it's now always telling them to upgrade or else, so they do and BOOM, YOU ARE SCREWED!!

THEY BLAME YOU!!!

STOP DOING THIS TO US!!!

Put this little jem into ~/.kde/Autostart/killbadstuff.sh

```

#! /bin/sh

# kill KDE CRAP !!!

killall virtuoso-t
killall nepomukserver
killall nepomukservices


```

Don't forget to:

chmod 755 ~/.kde/Autostart/killbadstuff.sh


WHAT ARE YOU PEOPLE THINKING ?

And who named that? WTF ?

---

### Post by nothingspecial on 2012-06-22
[IMG]http://img696.imageshack.us/img696/7058/necrov.png[/IMG]

---

