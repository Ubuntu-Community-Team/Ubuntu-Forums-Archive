---
title: "Remastersys Live CD installation problem"
date: 2011-09-15
forum: General Help
---

### Post by sptutusukanta on 2011-09-15
I want to take backup of my whole system using **Remastersys** along with my users' data.
It creates full live ISO of my system.
It works nicely when I try to boot as liveCD.
But as I tried to **install the backup distibution it hangs up**!.. What to do now?

Is there ***any better software or other options to create live CD*** of my system which can be used to*** install on another system***???

Thanks in advance..

---

### Post by texla on 2011-09-27
I have the same or similar problem with Remastersys in Natty.  Never had a problem with other versions of Ubuntu but there is no way I can find to install the backup of a Natty install.  Other versions worked great so I've gone back to 10.10 Maverick on my new computer because that is all I could install.  Good luck - google searches have shown nothing helpful so far...

---

### Post by bodhi.zazen on 2011-09-27
IMO you really do not need an image of the entire system, just back up the files you need.

this would be anything in your $HOME directory + any system files you manually edit.

All the other system files are an apt-get away.

You can very easily generate a list of all installed packages, and then restore those packages :

[http://www.ubuntu-unleashed.com/2008/04/howto-restore-all-installed-packages-in.html](http://www.ubuntu-unleashed.com/2008/04/howto-restore-all-installed-packages-in.html)

---

### Post by elliotn on 2011-09-28
I have The same problem with remastersys, I made a backup but when I want to install it didn't work, livecd boots well but no install.sux

---

### Post by deserthowler on 2011-09-28
I use the install option in the remastersys start menu instead of using the install icon on the live version desktop.  Worked fine for me with 11.04.  Copied from one machine to another.  No proprietary drivers installed.

Earl

---

### Post by elliotn on 2011-09-28
> **deserthowler said:**
> I use the install option in the remastersys start menu instead of using the install icon on the live version desktop.  Worked fine for me with 11.04.  Copied from one machine to another.  No proprietary drivers installed.

Earl

the thing is the install option on the start menu doesn't install it just freeze there

---

### Post by texla on 2011-09-28
> **deserthowler said:**
> I use the install option in the remastersys start menu instead of using the install icon on the live version desktop.
Earl
I tried that as well.  Mine lets the install start but it goes quickly to a message that says the username and password I entered are invalid - but it never asks for a username and password during this part of the install!  Then  it says ubi-partman error exit code #10 - no idea - I like the remastersys version of installs because netgear wn111 ndlswrapper ubuntuit keeps all of my settings, programs and email accounts. 

I am able to install a distro copy however.  This has all of my programs installed.  Now I will try the home copy and the packages list (in case I need it) suggested by bodhi.zazen and see if that does the job...

---

### Post by texla on 2011-10-01
> **bodhi.zazen said:**
> IMO you really do not need an image of the entire system, just back up the files you need.

this would be anything in your $HOME directory + any system files you manually edit.

All the other system files are an apt-get away.

You can very easily generate a list of all installed packages, and then restore those packages :

[http://www.ubuntu-unleashed.com/2008/04/howto-restore-all-installed-packages-in.html](http://www.ubuntu-unleashed.com/2008/04/howto-restore-all-installed-packages-in.html)
Thanks for this Bodhi!  Took a while for everything to install - and a few restarts after copying my Home Folder.  note: Unity went to always hide so that was fun to get back (hold down the Super or Windows key for a few seconds and then find your compiz settings in the search bar) but now all is good - Oh yeah, tried this with transferring my Natty install to a new computer with the Oncelot 11.10 beta 2 install and it worked great so far!  Nice tip.

---

### Post by bodhi.zazen on 2011-10-01
> **texla said:**
> Thanks for this Bodhi!  Took a while for everything to install - and a few restarts after copying my Home Folder.  note: Unity went to always hide so that was fun to get back (hold down the Super or Windows key for a few seconds and then find your compiz settings in the search bar) but now all is good - Oh yeah, tried this with transferring my Natty install to a new computer with the Oncelot 11.10 beta 2 install and it worked great so far!  Nice tip.

You are most welcome, smaller backup then an image of the entire system ;)

---

