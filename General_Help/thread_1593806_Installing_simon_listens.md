---
title: "Installing simon listens"
date: 2010-10-11
forum: General Help
---

### Post by Conkerchen on 2010-10-11
I am trying to install speech recognition sofware "simon listens" from [here](http://sourceforge.net/projects/speech2text/files/) but when i click on the .deb it says, that there is an unsolvable dependency to the package "libqt4-multimedia (>= 4:4.6.1)". I couldnt find this one in the repos myself, so i downloaded it manually from [here](https://launchpad.net/ubuntu/maverick/amd64/libqt4-multimedia), but when i try to install this package, it says, that the package "libqtcore4 (= 4:4.6.2-0ubuntu5)" is missing. So I also try to install that one but this time it says, that there is allready a newer version installed.

So how do I resolve this dependency? If I try to remove the newer package via apt-get, it also wants to remove a whole lot of other programs like plasma and such. Is there a way to go back to the older version? If so, would that be compatible with my distro (I'm running Kubuntu 10.10 x86_64) or does this get me into any trouble? And if so: why doesnt exist a libqt4-multimedia package in the distros because it looks like it did in Lucid.

Thanks for the help.

---

### Post by jambel on 2010-10-14
From the author's forum:

> Ubuntu 10.10 is not yet supported.

QtMultimedia was replaced by QtMobilities QtMultimediaKit but it isn't a  trivial change (requireing changes to simons buildsystem). I'll create  packages for 10.10 but that might take a while... Sorry.

Best regards, Peter [https://sourceforge.net/projects/speech2text/forums/forum/672426/topic/3889153/index/page/1](https://sourceforge.net/projects/speech2text/forums/forum/672426/topic/3889153/index/page/1)

---

### Post by KrisBerg on 2011-04-08
Got this one to install at last :) Haven't tried it yet, so I don't know if it'll work. 
[https://launchpad.net/~grasch-simon-listens/+archive/simon/+buildjob/2012745](https://launchpad.net/~grasch-simon-listens/+archive/simon/+buildjob/2012745)

---

### Post by theOGRE on 2011-05-26
thank you for the link. I finally got it installed!!! Now to figure out how to configure it!

---

### Post by basil2style on 2011-12-14
But didn't get it.Plz help now itself i got error in libqt-multimedia.Please help!!

---

