---
title: "Is K3B still available?"
date: 2004-10-24
forum: General Help
---

### Post by chapterthree on 2004-10-24
Hello All,
I'm looking at the ubuntulinux.org site, and it says "Run 'sudo apt-get install k3b'"
Ok:
```
kev [~]$ sudo apt-get install k3b
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package k3b
```

Any ideas?

---

### Post by JProgrammer on 2004-10-25
[QUOTE=chapterthree]Hello All,
I'm looking at the ubuntulinux.org site, and it says "Run 'sudo apt-get install k3b'"
Ok:
```
kev [~]$ sudo apt-get install k3b
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package k3b
```

Any ideas?[/QUOTE]
 If my memory serves me correctly I think it is in the universe repositry do you have that enabled?

---

### Post by chapterthree on 2004-10-25
eek, I'm sort of a "sudo n00b" :)
How do I enable that?

(Sorry, I came from fedora so debian and apt-get are a bit new to me)

Thanks

---

### Post by chapterthree on 2004-10-25
Hmm, actually I found out how to enable the universe.

Now I noticed that when I do the apt-get install k3b, it wants to install kde:
```
The following NEW packages will be installed:
  k3b k3blibs kdebase-bin kdelibs-bin kdelibs-data kdelibs4 libarts1 libartsc0
  libflac++2c102 libnetpbm10 libpcre3 menu menu-xdg netpbm
```

Is it possible to install k3b without installing kde?  I would like to stick with gnome for now if possible.

Thanks

---

### Post by JProgrammer on 2004-10-25
Ahh the bain of any Gnome user at the moment if you couldn't tell form the name 'K3B' it's a KDE app so no you can't have 'K3B' without KDE. There are many Gnome cd burning applications in the pipelines the most interesting of which is [coaster](www.coaster-burn.org) but unfortunately this is still a long way off since they aren't using cdrrecord like everyone else they are actually writing cd burning from the ground up they don't have anything overly useful yet :(

---

### Post by jayclark on 2004-10-25
I use kb3 without KDE. Apt-get finds the dependecys it needs for K3B, It dosen't install kde. After it installs, open the root terminal and type k3b. When k3b starts it might ask you to install cdrao or something to similar to that. Just open synaptic and type the name of the file it wants. After that you have a good cd burning app. Remember always open k3b from the terminal as root. If not you won't be able to login since it changes the .ICEAuthority file. Don't sudo k3b either. Use the root terminal.

Jay

---

### Post by Baloo on 2004-10-25
[QUOTE=JProgrammer]There are many Gnome cd burning applications in the pipelines the most interesting of which is [coaster](www.coaster-burn.org) but unfortunately this is still a long way off since they aren't using cdrrecord like everyone else they are actually writing cd burning from the ground up they don't have anything overly useful yet :([/QUOTE]

I disagree. Coaster is butt-ugly and really needs an UI redesign. 

There's nothing even remotely as good as K3b for gnome at the moment. Although its a blatent rip-off UI wise of a famous windows based app its the best way of doing cd burning application interfaces at the moment. 

Surely somebody could write a nice little mono front-end to cdrecord and make us all happy, infact, that would be a nice little job for my next mono project :)

---

### Post by JProgrammer on 2004-10-25
I would be up to helping out on that mono project. I think it's something gnome has been lacking for the longest time.

---

