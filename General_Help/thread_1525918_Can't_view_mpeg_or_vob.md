---
title: "Can't view mpeg or vob"
date: 2010-07-07
forum: General Help
---

### Post by bzzzzz on 2010-07-07
Every time I try to view an mpeg or vob using either gnomeplayer, movieplayer or vlc it fails to work.

Movieplayer and vlc often crash/force close.

gnomeplayer actually works and i hear sound, but the picture just contains a bluescreen.

I think it has something to do with the intel gm 855 onboard chipset as I had a few problems when installing but most of them seem to have been ironed out.

Any help much appreciated.

I'm running this on a dell d505 latitude

---

### Post by dino99 on 2010-07-07
look at ubuntu-restricted-extras into synaptic, might be installed

add medibuntu repo: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

might activate canonical-partner repo too into synaptic

then update, upgrade

---

### Post by bzzzzz on 2010-07-07
Hi thanks

When I tried to install the medibuntu repo I get this message

 sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
--2010-07-07 18:42:52--  [http://www.medibuntu.org/sources.list.d/isadora.list](http://www.medibuntu.org/sources.list.d/isadora.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-07-07 18:42:53 ERROR 404: Not Found.

---

