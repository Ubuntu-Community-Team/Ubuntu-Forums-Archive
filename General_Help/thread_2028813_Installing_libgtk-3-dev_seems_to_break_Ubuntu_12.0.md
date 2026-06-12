---
title: "Installing libgtk-3-dev seems to break Ubuntu 12.04 interface"
date: 2012-07-18
forum: General Help
---

### Post by Dave Buchan on 2012-07-18
Hi,

I have a 64 bit HP NC6400 laptop. I develop applications using GTK+.

Up to now, I've been using libgtk2.0-dev on Ubuntu 10.04, however I decided to get up-to-date so I installed 12.04 (complete fresh install). It looks good, but I ran into trouble as follows:

After fresh install of 12.04, I did the following (and nothing else):

sudo apt-get update
sudo apt-get install aptitude
sudo aptitude install libgtk-3-dev

When libgtk-3-dev was preparing to install, I answered "Y" to both questions. Then I restarted.

I type in my credentials at the graphical login screen, it accepts them, but then the screen goes black for a split second, and then returns to the login screen. If I try to move the mouse, it sticks and skips.

I can type cntl-alt-f1 to go to TTY session and login just fine.

I've tried doing:

sudo aptitude remove libgtk-3-dev

but that didn't help.

I've attached the contents of .xsession-errors before I installed libgtk-3-dev, and then after I installed it and the trouble began. Don't know what I'm looking at.

I couldn't attach the installation dialog (it's too big) so I've put it on my web site here:

[http://www.pdbuchan.com/libgtk-install.txt](http://www.pdbuchan.com/libgtk-install.txt)

Advice?

Dave

---

### Post by mc4man on 2012-07-22
You made a couple of mistakes here - 
first you posted in wrong sub-forum for your issue.

The real mistake is you accepted what aptitude wanted to do which basically removed anything to log in to.

Next time it's is worth reading thru what is to be removed..., personally on a fresh install I'd update/upgrade first, then install add. packages & I wouldn't use aptitude for normal update/upgrade tasks

---

### Post by Dave Buchan on 2012-07-23
Why not use aptitude? I thought it was like apt-get but kept better records of dependencies, so less likely to corrupt if you did an uninstall. Is that not right? I should use apt-get install instead?

I did see a lot of stuff being removed, so I was suspicious, for sure, but I thought the install would stop dead if I said "no" to either of the "Accept?" queries.

Can you expand a bit on what you said?

---

### Post by Toz on 2012-07-23
Moved to general help.

---

### Post by mc4man on 2012-07-24
I'd use apt-get because it would have upgraded your libgtk3* packages rather than what aptitude **First** suggested doing. 
That doesn't mean you had to accept aptitudes  1st. 'solution', you could have resolved it yourself or tried more aptitude solutions
(or used apt-get.

Ex.on a live 12.04 session right now, duped what you did. Aptitude handles the request 'wrong' as seen below - clipped, but exactly what you saw
>  $ sudo aptitude install libgtk-3-dev
clipped
The following packages will be upgraded:
  gir1.2-gtk-3.0 gir1.2-pango-1.0 libcairo-gobject2 libcairo2 libglib2.0-0 libglib2.0-bin libgtk-3-0 
  libgtk-3-common libpango1.0-0 
[COLOR="Red"]9[/COLOR] packages upgraded, 70 newly installed, 0 to remove and 343 not upgraded.
Need to get 31.9 MB of archives. After unpacking 101 MB will be used.
The following packages have unmet dependencies:
 libgtk-3-bin : Depends: libgtk-3-common (= 3.4.1-0ubuntu1) but 3.4.2-0ubuntu0.4 is to be installed.
 libgail-3-0 : Depends: libgtk-3-0 (= 3.4.1-0ubuntu1) but 3.4.2-0ubuntu0.4 is to be installed.
The following actions will resolve these dependencies:

       Remove the following packages:      
clipped
15)      gnome-session  
31)      light-themes
32)      metacity 
33)      nautilus
66)      unity 
67)      unity-2d 
68)      unity-2d-shell
 
answered n

2nd aptitude solution - 
> The following actions will resolve these dependencies:

     Upgrade the following packages:                                                     
1)     libgail-3-0 [3.4.1-0ubuntu1 (now, precise) -> 3.4.2-0ubuntu0.4 (precise-updates)] 
2)     libgtk-3-bin [3.4.1-0ubuntu1 (now, precise) -> 3.4.2-0ubuntu0.4 (precise-updates)]
Accept this solution? [Y/n/q/?]

That would have likely not removed anything...

On the other hand apt-get does it correct the 1st. time - 
>  sudo apt-get install libgtk-3-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
clipped
The following packages will be upgraded:
  gir1.2-gtk-3.0 gir1.2-pango-1.0 libcairo-gobject2 libcairo2 [COLOR="Blue"]libgail-3-0[/COLOR] libglib2.0-0 libglib2.0-bin
  libgtk-3-0 [COLOR="Blue"]libgtk-3-bin[/COLOR] libgtk-3-common libpango1.0-0
[COLOR="Blue"]11[/COLOR] upgraded, 70 newly installed, 0 to remove and 341 not upgraded.



In any event one is ultimately responsible for typing y

---

### Post by Dave Buchan on 2012-07-26
Sorry I took so long to get back.

Anyway, I wanted to test this properly so I did a fresh OS install and then did

apt-get update
apt-get install aptitude
aptitude install libgtk-3-dev

But now, having learned that I can reject aptitude's initial offer of solution, I said "no" and let it offer a solution which involved upgrading those apps in need of upgrading, but with NO removals.

Worked like a charm!

Thanks for taking the time to provide the great answer!

As you said, it might be wise to do an initial upgrade before installing anything anyway.

Thanks again!

Dave

---

