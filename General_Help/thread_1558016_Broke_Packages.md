---
title: "Broke Packages"
date: 2010-08-21
forum: General Help
---

### Post by laos.lindberg on 2010-08-21
I was trying to upgrade midori and i was told there were broken packages. 

Any help?

```
manning@manning-laptop:~$ sudo apt-get install midori
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  midori: PreDepends: dpkg (>= 1.15.7.2) but 1.15.5.6ubuntu4.1 is to be installed
E: Broken packages

```

---

### Post by laos.lindberg on 2010-08-22
bump bump

anybody?

---

### Post by Pollox on 2010-08-22
Thought:
1) start Synaptic (under System >> Administration)
2) Under edit menu, select "fix broken packages"
3) click apply
4) try installing midori again and report results

---

### Post by laos.lindberg on 2010-08-22
did that, it tells me "successfully fixed dependency problems"

i tried to install midori again, and received the same feedback as before,  kernel was recently upgraded.

---

### Post by Pollox on 2010-08-22
Okay, time for more information then.  What version of Ubuntu are you running.  What repositories do you have enabled, e.g. backports, proposed, a special one for midori?  It looks like the version of midori you are trying to install depends on a newer version of dpkg than you can install.

---

### Post by laos.lindberg on 2010-08-22
I am running Ubuntu 10.04.1 LTS. I do have the midori and webkit ppa's enabled through ubuntu tweak.  

yorba, wine, tweak, tvst-hotmail-cardapio, tracker-team-tracker, tiheum-equinox-lucid, skype, sevenmachines-flash, pidgin, opera, midori-ppa-lucid, neversfelde-ppa, midori-ppa,medibuntu, gtg-development-ppa, google-chrome, gloobus-dec-gloobus-preview, elementary-ppa, elementaryart-elementarydesktop, dropbox, docky, chuchiperiman-cloudsn, chromium-daily-ppa-lucid, chromium-browser, cardapio-team-unstable, caffeine-developers-ppa, bisigi-ppa, banshee, awn-core, am-monkeyd-nautilus-elementary-ppa-lucid


I think this covers it.  I am a year into my ubuntu experience and i love it.  if there is more info you need, let me know the best way to get it.

thank you for the hand.

---

### Post by Pollox on 2010-08-22
Ok, just as I thought, the problem is due to dependencies of this newer version of midori that aren't met in the standard repos.  Specifically, if you look at the properties of midori under synaptic, you'll see the line "PreDepends: dpkg (>=1.15.7.2)".  You have a few options:

1) track down a version of dpkg for Lucid (Ubuntu 10.04) of version 1.15.7.2 or higher and install it.  You don't need to add another repository, a deb file will do.
2) In Synaptic, select midori, and under the Package menu, select Force version.  Pick the older version.  Wait for the day when the dependency is satisfied and midori will get upgraded then.
3) Remove the midori and webkit repos.

I would also advise you to be careful about enabling lots of third-party repositories.  They can cause issues like this, or even stability issues, so limit yourself only to the ones you need (when you just have to have the latest version of something, or when what you want isn't in the standard repos).

---

### Post by laos.lindberg on 2010-08-22
thanks for the heads up and the advice! I will only use third party ppa's for things i want to be on the bleeding edge of.  I don't want to have to track down little fixes all the time.

thanks

---

