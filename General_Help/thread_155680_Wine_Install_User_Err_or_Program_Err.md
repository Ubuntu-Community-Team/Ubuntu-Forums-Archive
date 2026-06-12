---
title: "Wine Install: User Err or Program Err?"
date: 2006-04-05
forum: General Help
---

### Post by BeerSlinger on 2006-04-05
Ok, I tried to install wine and I followed the instructions on Wine HQ and I tried to make sure that things would go smooth......well they didn't and now i'm stuck so I was wondering if someone would help.....

The first thing I did was install the new source for the update in the Synaptic Packages Manager and added to the repository the custom address:

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

Then I searched for the wine package and I found seven entries, they were:

[not installed] lg-issue52
[not installed] lg-issue80
[not installed] libwine
[not installed] libwine-dev
[installed] tellico
[not installed] wine-doc
[not installed] xwine

First, I tried to install the dependencies, this is what i changed...

[installed] lg-issue52
[installed] lg-issue80
[not installed] libwine
[not installed] libwine-dev
[installed] tellico
[installed] wine-doc
[installed] xwine

Well, then I tried installing the libraries and that's where everything went haywire....When doing so I got this error:

**[SIZE="3"]Could Not Mark all Packages for installation or Upgrade[/SIZE]**

The following packages have unresolable dependencies. Make sure that all required repositories are added and enabled in hte preferences.

libwine:


     Depends: wine  but it is not installable

Could someone tell me how to track down a resolution, because I really would like to use this software.......Part of my problem is that I don't know how to track down dependency errors because i'm still pretty new with linux......

---

### Post by BeerSlinger on 2006-04-05
Just a couple of updates for anyone trying to help, since I wrote this I went back to the Synaptic Package Manager and set my computer back to the way it was when I first tried it........also since that time I have found the How To on Wine:

[http://www.ubuntuforums.org/showthread.php?t=149585](http://www.ubuntuforums.org/showthread.php?t=149585)

and it didn't work, I don't think it was because of the instructions but because the source for server is having issues at this point........I tried over a dozen ways to download the *.deb file that is at the beginning of the tutorial and every time it failed....

in fact, I tired other versions and none of them worked either........Its my guess is that its just having issues right now with traffic or otherwise.....

---

### Post by BeerSlinger on 2006-04-06
I was hoping that I would have this solved by working the problem for a day but I just can't seem to do it.....Though on the otherhand, I tried eliminating the newbie errors so that the problem can be solved.......Sometimes I admit that i'm a little intimidated by linux because of the dependencies that have to be tracked and conflicts that have to be traced.......but hopefully, I will get over that with a little experience........

So, this is what I have tracked down:

The same two parts of Wine will not install and they are

libwine
libwine-dev

I have tried to track them down from every way I could think of.......but to no avail.....First I thougt maybe all of the dependent resources weren't installed so I started tracking them down, one by one........from the list that Debian gives, they are:

gdk-imlib1
libart2 (>= 1.2.13-5)
libaudiofile0 (>= 0.2.3-4)
libc6 (>= 2.3.2.ds1-4) [not ia64]
libc6.1 (>= 2.3.2.ds1-4) [ia64]
libdb3 (>= 3.2.9-20) [i386]
libesd0 (>= 0.2.29-1)
libglib1.2 (>= 1.2.0)
libgnome32 (>= 1.2.13-5)
libgnomesupport0 (>= 1.2.13-5)
libgnomeui32 (>= 1.4.2-3)
libgtk1.2 (>= 1.2.10-4)
libice6
libsm6
libx11-6
libxext6
libxi6
libxml2 (>= 2.6.11) [i386]
libxml2 (>= 2.6.16) [not i386] 
zlib1g (>= 1:1.2.1)
debconf (>= 1.2.0)
libwine (= 0.0.20050310-1.2)
xbase-clients (>= 4.0)
binfmt-support
msttcorefonts
wine-doc
wine-utils (Not Found)
Perl
binfmt-support

I will admit that not all were enabled, but I enabled them and then tried to get the most current version of amd64 wine off of debian and tried to install.....

xwine_1.0-1_amd64.deb

The install seemed to take, but it didn't get me very far......Although Ubuntu came up with an install for an upgrade for XWine......I don't see to where a program directory was installed.......and confirming this, I tried to install the tools for wine and it confirmed that it wasn't installed......

So i'm basically where I started, I can't install the libwine or libwine-dev because I can't find the conflict......Any Ideas?

:-k

---

### Post by dcstar on 2006-04-06
[QUOTE=BeerSlinger]
.......
So i'm basically where I started, I can't install the libwine or libwine-dev because I can't find the conflict......Any Ideas?

:-k[/QUOTE]
libwine: [I]Microsoft Windows Compatibility Layer (Dummy Package)
This is a dummy package to ease upgrade from users of old libwine-* packages
to the newer wine package.  It can be safely removed at any time.[/I]

You don't need it, stop worrying about it.

As well, you repositories should really be:

deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) breezy/

---

### Post by BeerSlinger on 2006-04-06
[QUOTE=dcstar]libwine: [I]Microsoft Windows Compatibility Layer (Dummy Package)
This is a dummy package to ease upgrade from users of old libwine-* packages
to the newer wine package.  It can be safely removed at any time.[/I]

You don't need it, stop worrying about it.

As well, you repositories should really be:

deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) breezy/[/QUOTE]

Ok, then let's step back for a minite.......point taken.........from my research I have added the deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) binary/, deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) source/ and deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) breezy/ (that's new to me by the way) and I don't see anything listed in the Add Application menu for wine even though those repositories have been added.......

So my next logical thought was to go to the debian.org package list and try to find the AMD64 compatable realease and download and install......So first I download:

xwine_1.0-1_amd64.deb

Then the update manager comes up with:

XWine
Graphical user interface for the wine emulator
New Version 1.0.1-1

Then I install that.......but that's where the fun ends........I automatically figured that the added repositories would install wine and I was a little confused when it didn't appear and I can't seem to find a file directory for it, I do though have an /etc/xwine directory but its almost empty.....

I just don't know how to proceed......

I have even tried: 

sudo xwine

and I get:

user@localhost:~$ sudo xwine
error: wine doesn't work, you have to install it...
user@localhost:~$

When I try:

user@localhost:~$ sudo apt-get install xwine
Reading package lists... Done
Building dependency tree... Done
xwine is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
user@localhost:~$

I just don't know where to logically go next......

---

### Post by Michael Ambrus on 2006-05-05
I think you need to install wine also:

vmware@vmware-bavm:~$ sudo apt-get install wine

/Michael

---

### Post by Smight on 2006-05-05
I was having similar problems.. I posted this link into my package manager

deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) breezy/

This broke my package manager. The package manager now just churns and churns, does nothing.. Where is the /end idiot button in my logic.. The last time I did this I had to re-install Ubuntu. I'm not real familiar with the Xserver enviro but you'd think doing what you read might fix things, but in my case, it broke things.. Any ideas?



Smighty

---

### Post by Smight on 2006-05-05
[QUOTE=Smight]I was having similar problems.. I posted this link into my package manager

deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) breezy/

This broke my package manager. The package manager now just churns and churns, does nothing.. Where is the /end idiot button in my logic.. The last time I did this I had to re-install Ubuntu. I'm not real familiar with the Xserver enviro but you'd think doing what you read might fix things, but in my case, it broke things.. Any ideas?



Smighty[/QUOTE]

Wow.. I'm coming along quite nicely.. I've unjacked my package manager. It appears that when you insert an improperly worded location into the repositories section it jacks with your " add applications " component. Going directly into the package manager and removing it fixes that. However.. This does not take me farther away from the problem. I have installed wine from the root console ( have I? ) and still it appears that wine has not been installed. Is there some justice I am missing? Hopefully I can get a dork award once I figure this stuff out.. :)

apt-get install wine <-- by all apparent observations this should do the trick however in my case, as well as the other soul in this thread this does not work.

Listening.. For clue.. Phone.. :)

Smighty

---

