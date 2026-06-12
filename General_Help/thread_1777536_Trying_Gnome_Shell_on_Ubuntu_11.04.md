---
title: "Trying Gnome Shell on Ubuntu 11.04"
date: 2011-06-07
forum: General Help
---

### Post by Nonno Bassotto on 2011-06-07
I am positive this has been asked countless times, but I do not want to rely on older threads, as things seem to move rather quickly, and new PPAs appear overnight.

What is currently the preferred way to try Gnome Shell on Ubuntu Natty? By preferred I mean that it should integrate as seamlessly as possible on Ubuntu and it should allow an easy way to get back to Unity.

---

### Post by hhh on 2011-06-07
The preferred way is not to install it until 11.10, it will break your installation...
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/690045](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/690045)
[http://askubuntu.com/questions/37600/gnome-3-ppa-was-unstable-until-april-28th-so-is-it-ok-now/37804#37804](http://askubuntu.com/questions/37600/gnome-3-ppa-was-unstable-until-april-28th-so-is-it-ok-now/37804#37804)

Here's the unofficial way...
[http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3](http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3)

---

### Post by linuxinstalledfromhdd on 2011-06-07
> **Nonno Bassotto said:**
> I am positive this has been asked countless times, but I do not want to rely on older threads, as things seem to move rather quickly, and new PPAs appear overnight.

What is currently the preferred way to try Gnome Shell on Ubuntu Natty? By preferred I mean that it should integrate as seamlessly as possible on Ubuntu and it should allow an easy way to get back to Unity.

I'm just going to confirm what the other user just posted to your article here.. 

Yes, it's not ready for prime time yet.  If you are a Gnome 3 developer, then ok.  Other than that, it would be best to wait until they get all the bugs out of it.  If you try to install it on 11.04 and you can't get it to work, you would need to to do a PPA purge from recovery mode command line. If you haven't done that before, I wouldn't install Gnome Shell 3 PPA yet.  If you are a developer you would need to create a minimal installation of Ubuntu and install it from the command line, so that way it would hopefully work.  You can simply do a search for how to do that on google or here as well.  :D

---

### Post by hhh on 2011-06-07
Here's the Ubuntu Forums thread on it. As you can see from the first post, the original poster gave up on it as it broke his own system...
[http://ubuntuforums.org/showthread.php?t=1742343](http://ubuntuforums.org/showthread.php?t=1742343)

---

### Post by dwhite on 2011-06-08
> **Nonno Bassotto said:**
> 

What is currently the preferred way to try Gnome Shell on Ubuntu Natty? By preferred I mean that it should integrate as seamlessly as possible on Ubuntu and it should allow an easy way to get back to Unity.

Gnome 3 not specifically mentioned here but probably what you are looking to do (that is switch between unity and gnome 3) 

If by chance you meant switching between unity and gnome 2 then i'll just mention that you can do that at the login screen...

---

### Post by nothingspecial on 2011-06-08
At the moment you cannot switch between them afaik.

I'm using it on top of xubuntu (no conflicts) and it works well.

---

### Post by Nonno Bassotto on 2011-06-08
> **linuxinstalledfromhdd said:**
> I'm just going to confirm what the other user just posted to your article here.. 

Yes, it's not ready for prime time yet.  If you are a Gnome 3 developer, then ok.  Other than that, it would be best to wait until they get all the bugs out of it.  If you try to install it on 11.04 and you can't get it to work, you would need to to do a PPA purge from recovery mode command line. If you haven't done that before, I wouldn't install Gnome Shell 3 PPA yet.  If you are a developer you would need to create a minimal installation of Ubuntu and install it from the command line, so that way it would hopefully work.  You can simply do a search for how to do that on google or here as well.  :D

Thank you all. Yes, I am aware that installing Gnome Shell will break my system, and that is why I asked for an easy way to go back rather than the option to switch at login. Doing a PPA purge from command line is not a problem.

I will have a look at the links and hope for good. Thank you all for the advice.

---

### Post by bmbaker on 2011-06-08
gnome 3 will not break your system!
you can still use unity and gnome classic!

you need 2 ppa's 
[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)
[https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)
do an update and install gnome-shell
then log into gnome-shell and do a dist-upgrade
everything wks just fine :-)

---

### Post by ojdon on 2011-06-08
I wrote a tutorial on how to install gnome-shell. It's aimed at tablet devices but anyone can use it really:

[http://www.ollie-reardon.co.uk/create-a-linux-tablet-distribution/]("http://www.ollie-reardon.co.uk/create-a-linux-tablet-distribution/")

---

### Post by Nonno Bassotto on 2011-06-08
> **bmbaker said:**
> gnome 3 will not break your system!
you can still use unity and gnome classic!

you need 2 ppa's 
[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)
[https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)
do an update and install gnome-shell
then log into gnome-shell and do a dist-upgrade
everything wks just fine :-)

Do you mean that one can have both and choose at login?

---

### Post by pikamoku on 2011-06-08
> **bmbaker said:**
> gnome 3 will not break your system!

yep! gnome3+gnome-shell is my default session from 4 weeks. No one issue unless experimental extensions related.


edit myself:
on ricotz repository warns you that need also gnome3-team ppa

---

