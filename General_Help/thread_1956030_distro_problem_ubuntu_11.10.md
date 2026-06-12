---
title: "distro problem ubuntu 11.10"
date: 2012-04-10
forum: General Help
---

### Post by rajan2003 on 2012-04-10
hey guys,


i installed the linux mint mate.......what-to-say.......addon for my ubuntu 11.10 . after that i couldnt open my software centre. and now thats fixed but now when i try to add a ppa i get this 


> Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 99, in <module>
    sp = SoftwareProperties(options=options)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 96, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 580, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.7/dist-packages/aptsources/distro.py", line 91, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template

i dunno why this is happenning and i cant wait till 12.04 releases . i think theres somthing wrong with the distro .

any help would be appreciated thanks!

---

### Post by Mark Phelps on 2012-04-10
First off, Linux Mint is NOT Ubuntu.  If you're having serious problems with Mint, you need to be posting those in the Mint forums.  You will have a better chance of getting solutions from there.

Second, what makes you think that 12.04 is going to solve the problem you're having?

Lots of folks have installed 11.10 and NOT encountered the problem you mention.

So, before you jump on the 12.04 bandwagon, you would better to check with the Mint forum folks and see if you can diagnose the problem you're having with 11.10.

---

### Post by rajan2003 on 2012-04-11
I REMOVED EVERYTHING RELATED TO LINUX MINT.


MY PROBLEM IS WHY THE HELL DO I GET THIS MESSAGE EVRYTIME I TRY TO ADD A PPA?:mad::mad:


traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 99, in <module>
    sp = SoftwareProperties(options=options)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 96, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 580, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.7/dist-packages/aptsources/distro.py", line 91, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template



DID I SAY INSTALLING 12.04 WONT SOLVE MY PROBLEM?

---

### Post by bab1 on 2012-04-11
[SIZE="2"][COLOR="Red"]Error: could not find a distribution template[/COLOR][/SIZE]

The PPA is not for that disto or version of that distro.

---

### Post by forrestcupp on 2012-04-11
> **rajan2003 said:**
> I REMOVED EVERYTHING RELATED TO LINUX MINT.


MY PROBLEM IS WHY THE HELL DO I GET THIS MESSAGE EVRYTIME I TRY TO ADD A PPA?:mad::mad:

...

DID I SAY INSTALLING 12.04 WONT SOLVE MY PROBLEM?

Don't get so mad. You never told us in the first post that you removed everything related to Mint. Does that include Mate, which doesn't get much support in Ubuntu?

Anyway, it might help if you could tell us which PPA you're trying to install (with a link to it), and what steps you took to install the PPA.

---

### Post by Myrddin Emrys on 2012-04-11
There's a Mint package called mint-meta-mate that some people have suggested installing on Ubuntu to get the MATE desktop, e.g.:

[http://www.noobslab.com/2011/11/install-linux-mint-mate-desktop-on.html](http://www.noobslab.com/2011/11/install-linux-mint-mate-desktop-on.html)
[http://www.addictivetips.com/ubuntu-linux-tips/install-linux-mint-mate-desktop-in-ubuntu-11-10/](http://www.addictivetips.com/ubuntu-linux-tips/install-linux-mint-mate-desktop-in-ubuntu-11-10/)

This is actually a really bad idea, as it tends to cause just the sort  of problems the original poster reports. A much better approach is to  use the MATE developers' own repository, which gives a clean  installation and is very easy to set up with 11.10 or 12.04. See:

[http://mate-desktop.org/](http://mate-desktop.org/)
[http://wiki.mate-desktop.org/download#ubuntu](http://wiki.mate-desktop.org/download#ubuntu)

Here's a detailed walkthrough:

[http://www.howtogeek.com/110052/how-to-install-the-mate-desktop-go-back-to-gnome-2-on-ubuntu/](http://www.howtogeek.com/110052/how-to-install-the-mate-desktop-go-back-to-gnome-2-on-ubuntu/)

---

### Post by rajan2003 on 2012-04-12
sory guys ididnt mean to get mad . i was mad about my terminal message i keep getting.

> Don't get so mad. You never told us in the first post that you removed everything related to Mint. Does that include Mate, which doesn't get much support in Ubuntu?

yes
__________________________________________________________________________________-------------


> Anyway, it might help if you could tell us which PPA you're trying to install (with a link to it), and what steps you took to install the PPA.


sudo add-apt-repository ppa:webupd8team/themes
ityped it.then password . then i pressed ENTER . and then the error
i didnt understand about the link. if you meant the site that i got the ppa,its this
[http://www.webupd8.org/2011/10/4-beautiful-gnome-32-compatible-gtk.html](http://www.webupd8.org/2011/10/4-beautiful-gnome-32-compatible-gtk.html)

_______________________________________________________________________________________--

> There's a Mint package called mint-meta-mate that some people have suggested installing on Ubuntu to get the MATE desktop, e.g.:

[http://www.noobslab.com/2011/11/inst...esktop-on.html](http://www.noobslab.com/2011/11/inst...esktop-on.html)
[http://www.addictivetips.com/ubuntu-...-ubuntu-11-10/](http://www.addictivetips.com/ubuntu-...-ubuntu-11-10/)

This is actually a really bad idea, as it tends to cause just the sort of problems the original poster reports. A much better approach is to use the MATE developers' own repository, which gives a clean installation and is very easy to set up with 11.10 or 12.04. See:

[http://mate-desktop.org/](http://mate-desktop.org/)
[http://wiki.mate-desktop.org/download#ubuntu](http://wiki.mate-desktop.org/download#ubuntu)

Here's a detailed walkthrough:

[http://www.howtogeek.com/110052/how-...e-2-on-ubuntu/](http://www.howtogeek.com/110052/how-...e-2-on-ubuntu/)




im not gonna install MATE again .

---

### Post by rajan2003 on 2012-04-12
i just edited my ,um,this thing:
gksu gedit /etc/*release,
and changed it from its MATE setting to this:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=Oneric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

but that doesnt seem to work either

---

### Post by forrestcupp on 2012-04-12
> **rajan2003 said:**
> i just edited my ,um,this thing:
gksu gedit /etc/*release,
and changed it from its MATE setting to this:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=Oneric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

but that doesnt seem to work either

That seems to be the right fix from what I've seen elsewhere. I wonder if the problem is that you misspelled **Oneiric**. If it still doesn't work try it again without capitalizing it. I saw someone else who made a spelling mistake like that, and when they fixed it, it worked.

---

### Post by lolpenguin on 2012-04-12
> **Mark Phelps said:**
> First off, Linux Mint is NOT Ubuntu.  If you're having serious problems with Mint, you need to be posting those in the Mint forums.  You will have a better chance of getting solutions from there.

Second, what makes you think that 12.04 is going to solve the problem you're having?

Lots of folks have installed 11.10 and NOT encountered the problem you mention.

So, before you jump on the 12.04 bandwagon, you would better to check with the Mint forum folks and see if you can diagnose the problem you're having with 11.10.

...
Mint is actually an edited Ubuntu. Take a look in sources.list in a Mint install:
```
deb http://packges.linuxmint.com/ lisa main upstream import
[B]deb http://archive.ubuntu.com/ oneiric main restricted universe multiverse
deb http://archive.ubuntu.com/ oneiric-updates main restricted universe multiverse[/B]
```
and so on.

---

### Post by rajan2003 on 2012-04-12
> That seems to be the right fix from what I've seen elsewhere. I wonder if the problem is that you misspelled Oneiric. If it still doesn't work try it again without capitalizing it. I saw someone else who made a spelling mistake like that, and when they fixed it, it worked.


**HOLY COW!!!!! IT WORKED!!!!**:KS:KS:KS:KS:guitar::guitar::guitar::guitar:

THANKS DUDE I REALLY APPRECIATE IT .I'VE been waiting for this reply forever . BTW **decapitalization along with correcting the name worked for me**



PS:There's no better way to capture my enthusiasm than with CAPS, trust me. It's very cool.

**problem solving reply by forrestcupp**

---

### Post by forrestcupp on 2012-04-14
Hey, I'm glad it worked out for you.

---

