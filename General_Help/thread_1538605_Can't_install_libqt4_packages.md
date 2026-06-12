---
title: "Can't install libqt4 packages"
date: 2010-07-25
forum: General Help
---

### Post by bobtfish on 2010-07-25
Hi, I noticed this trying to install the virtualbox qt gui, but it doesn't really seem to be anything to do with that.
I think maybe I have a PPA that has different versions of a lot of qt packages, but I'm a bit confused:
In Synaptic, I try to install virtualbox-ose-qt, and get an error

"Depends: libqt4-opengl but it is not going to be installed"

Ok, so I search for that package, it is there, but I get:

  Depends: libqtcore4 (=4:4.6.2-0ubuntu5) but 4:4.6.2-0ubuntu6~ppa9 is to be installed
  Depends: libqtgui4 (=4:4.6.2-0ubuntu5) but 4:4.6.2-0ubuntu6~ppa9 is to be installed

And pretty much the same every time I try to follow this down the pile.
Now I think this is saying it wants the version ending 5, but the only version available is the one ending 6~ppa9. But under "Latest Version" is the version number ending 5 anyway, so I don't know where this other one is coming from.

I sorted everything in Synaptic by Origin and went through everything that wasn't directly from Ubuntu, but didn't see anything at all about libqt4, so as far as I can tell there shouldn't be any conflict with a PPA anyway??

So please, does anyone have any suggestions? Do I need a PPA for the most recent versions? Or is it possible to force installation of the versions available? Would that cause problems? Thanks.

Chris

---

### Post by mc4man on 2010-07-25
> I think maybe I have a PPA 
Look and see if the ppa is still enabled, if it isn't, then you could try enabling and see if it can provide the librairies you need installed ( or go to the ppa's package page and look

Some libraries have  a dep(s) of => (equal or greater), some of just =.
So in this case libqt4-opengl has an = dep., you'll need your ppa to provide  a libqt4-opengl for you.


> Depends: libqtcore4 (=4:4.6.2-0ubuntu5) but 4:4.6.2-0ubuntu6~ppa9 is to be installed
Depends: libqtgui4 (=4:4.6.2-0ubuntu5) but 4:4.6.2-0ubuntu6~ppa9 is to be installed


Most times you can read that like this
Depends: libqtcore4 (=4:4.6.2-0ubuntu5) but 4:4.6.2-0ubuntu6~ppa9 is [COLOR="Blue"]already[/COLOR] installed
Depends: libqtgui4 ([COLOR="Blue"]=[/COLOR]4:4.6.2-0ubuntu5) but 4:4.6.2-0ubuntu6~ppa9 is [COLOR="Blue"]already[/COLOR] installed

(If neither are installed then your ppa is enabled  - disable it and try again


If your ppa can't provide all the qt4 libs that are required or requiring an = version then you'll need to either force the install (probably a poor idea), or downgrade your qt4 libs to the ubuntu versions or forget installing virtualbox-ose-qt, or find a ppa that provides all the packages.


If you disable the ppa and downgrade you may lose whatever it is that caused you to add the ppa in the first place, only you know why you added the ppa

---

### Post by bobtfish on 2010-07-27
Thanks for your input, but I think I may have been unclear. I said I thought it might be a PPA problem simply because of the version numbers. I do not have any PPAs set up specifically for this, I was just wondering if one I already had set up for something else may have been interfering. Google suggests some people have had similar problems with Skype, and I have got Skype, but it's installed through a repository with a skype.com url, not a Launchpad PPA.

The particular packages I mention are NOT installed, any version. However, searching in Synaptic just for "libqt4" does have some packages that are installed with the "4:4.6.2-0ubuntu6~ppa9" version number, although I can't quite figure out where they came from.

What does worry me somewhat is that if I select any of the packages that ARE installed, then go to Properties->Dependencies, I get a list of dependencies, and then a line:
Replaces: libqt4-core (<4.4.0~beta1-1)

So does this mean trying to install the packages I want is conflicting with the ones that are already there?

Actually, I note that viewing "Dependent Packages" lists a whole bunch of stuff I don't know about, and also Skype. I will try temporarily disabling the Skype repository and report back, but I guess that won't help as there will be clashes with the things already installed.

Chris

---

### Post by bobtfish on 2010-07-27
Ok, so disabling the Skype repository was of no help. I have however noticed that the packages with the 6~ppa9 version number are listed in Synaptic as being installed locally (i.e. sort by Origin, they are under Local). So I have no idea how or why that would be the case, this is a relatively recent installation of 10.04, and I don't recall doing anything like that.

I think my best bet is to force a downgrade of these packages to the main repository versions. I will Google, but any advice on how to go about this?
Thanks.

Chris

---

### Post by bobtfish on 2010-07-27
I know I keep replying to my own thread, but I wanted to just share my fix in case it helps someone else.
I tried to use Force Version in Synaptic, but then several programs (Hedgewars, VLC, ...) complained they wanted to be removed, so I used dpkg on the command line:
sudo dpkg -P --force-all libqt4-dbus libqt4-network libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-xml libqtcore4 libqtgui4
to remove everything without worrying about breaking dependencies, then to reinstall the standard repository version:
sudo apt-get install libqt4-dbus libqt4-network libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-xml libqtcore4 libqtgui4

After this I could install the stuff I wanted just fine, and I checked the programs that complained and they worked, although I haven't tested them thoroughly.
Thanks for your input mc4man, and anyone else who at least read it but couldn't help.

Chris.

---

### Post by romankarlfranz on 2010-12-29
:popcorn:may God reward you for that good deed and send to hell all those who take part in the windows conspiracy

---

### Post by itsAqeel on 2012-02-19
Hello ..
   Im a newbee to Ubuntu n I was also having the same installation problem when I was installing fatrat today... bt I fixed it out when I followed ur suggestions...

 Thanks a lot, u guyz rockk... :D

---

### Post by Iowan on 2012-02-19
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.Closed.

---

