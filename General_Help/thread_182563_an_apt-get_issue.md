---
title: "an apt-get issue"
date: 2006-05-26
forum: General Help
---

### Post by Nice2Mitiu on 2006-05-26
hi,every time i use apt-get or synaptic, i get this:
```
W: Couldn't stat source package list http://archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://koti.mbnet.fi breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://theli.free.fr ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

```

even though i run apt-get update, i continue getting the same stupid error. but the strangest thing is, that i actually CAN install programs. the problem became annoying, when i desided to upgrade to Dapper - it wouldn't let me to it! :( 
please tell me what should i do?

---

### Post by FredSambo on 2006-05-26
are you running breezy or dapper at the moment?  or were you unable to upgrade?

you can try

```
sudo gedit /etc/apt/sources.list
```

and comment out those particular lines, or you could change the word 'breezy' with 'dapper,' if you are indeed running dapper.

good luck!

---

### Post by Ramses de Norre on 2006-05-26
What's the content of your /etc/apt/sources.list?

---

### Post by FredSambo on 2006-05-26
[QUOTE=Ramses de Norre]What's the content of your /etc/apt/sources.list?[/QUOTE]

ya, paste it here so we can check out your warez.  :p

---

### Post by FredSambo on 2006-05-26
(off topic)

Wow, Ramses, are you really in Leuven, Belgium?

Damn fine beer in your neck of the woods, cheers!

---

### Post by Nice2Mitiu on 2006-05-26
[QUOTE=Ramses de Norre]What's the content of your /etc/apt/sources.list?[/QUOTE]
```
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://wine.lowvoice.nl/apt breezy main
deb-src http://wine.lowvoice.nl/apt breezy main

deb http://deb.opera.com/opera/ etch non-free

deb http://kubuntu.org/packages/kde351 breezy main

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://koti.mbnet.fi/~ots/ubuntu/ breezy/
deb-src http://koti.mbnet.fi/~ots/ubuntu/ breezy/

deb http://theli.free.fr/packages/breezy/ ./
```

i am running breezy.

---

### Post by Ramses de Norre on 2006-05-26
And not only the beer is superb over here ;)

---

### Post by FredSambo on 2006-05-26
[QUOTE=Nice2Mitiu]```
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://wine.lowvoice.nl/apt breezy main
deb-src http://wine.lowvoice.nl/apt breezy main

deb http://deb.opera.com/opera/ etch non-free

deb http://kubuntu.org/packages/kde351 breezy main

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://koti.mbnet.fi/~ots/ubuntu/ breezy/
deb-src http://koti.mbnet.fi/~ots/ubuntu/ breezy/

deb http://theli.free.fr/packages/breezy/ ./
```

i am running breezy.[/QUOTE]

where did you get that list?

---

### Post by Nice2Mitiu on 2006-05-26
[QUOTE=FredSambo]where did you get that list?[/QUOTE]
> where did you get that list?
how should i know :/

---

### Post by Nice2Mitiu on 2006-05-26
i did it! i f*****g did it!
well, you helped me.i just had to look closely at sources.list, removed some strange https and delete a file in /var/lib/apt/lists

---

### Post by 3rdalbum on 2006-05-26
I think he means "where did you get the sites for those modifications to your sources.list?".

Try commenting out (putting a "#" before) the lines which don't have the word Ubuntu in them. (including the Kubuntu one).

Otherwise, just keep trying. The repositories have been playing up for a number of people lately, it's probably just in preparation for June.

---

### Post by FredSambo on 2006-05-26
> I think he means "where did you get the sites for those modifications to your sources.list?".

thanks for clearing that up!  

i'm glad everything worked out!

---

