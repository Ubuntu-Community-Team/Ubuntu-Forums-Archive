---
title: "awn-extras in 11.04"
date: 2011-05-02
forum: General Help
---

### Post by swiftsam on 2011-05-02
I am a big fan of avant window navigator, but I'm having trouble getting it set up all the way in natty.

avant-window-navigator is in the natty repos, but there are a couple of shortcomings in the applets.
 - the digital clock applet is not included
 - the weather applet has an annoying bug (constantly announcing that there may be connectivity issues) that was fixed a long time ago

That's fine, I'll just I just install from the PPA I thought.  The problem is that the applets package (awn-extras) is not in [their natty repo]("https://launchpad.net/~awn-testing/+archive/ppa?field.series_filter=natty").

Does anyone know how to get awn with the most recent applets in natty?

---

### Post by swiftsam on 2011-05-02
I just solved part of my problem.  There is a package called awn-applets-all which is not installed by default.  It includes the digital clock and it looks like everything else I was used to.

I guess now they just need to update awn-applet-weather and I'll be all set.

---

### Post by cbowman57 on 2011-05-03
[Link to awn weather network error solutions]("http://reformedmusings.wordpress.com/2011/03/19/awn-network-error-in-weather/")

---

### Post by lockalyo on 2011-06-09
I already tried installing the extras via that guide on [http://www.webupd8.org/](http://www.webupd8.org/) - the network error article points to it. However, the packages described there are missing when I try to install them. In the software center, if I browse through the packages from that PPA, I see no packages for the extra applets. If I install all packages from there, I end up with no applets at all.

---

### Post by unc0nn3ct3d on 2012-04-19
looks like it has something to do with weather.com switching their backend.. need to replace xoap with xml.. Found the solution here:
[http://blog.netflowdevelopments.com/2012/04/19/weather-app-for-awn-not-working-network-error/](http://blog.netflowdevelopments.com/2012/04/19/weather-app-for-awn-not-working-network-error/)

---

