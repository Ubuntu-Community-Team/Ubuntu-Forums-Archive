---
title: "Hardy-Hardy dual boot"
date: 2010-01-05
forum: General Help
---

### Post by james_mcl on 2010-01-05
I've had issues with the later versions of Ubuntu, so in an effort to road-test Firefox 3.5 on Hardy I'd like to change my Karmic/Hardy dual boot to a Hardy/Hardy dual boot, and follow the instructions in [https://help.ubuntu.com/community/FirefoxNewVersion/MozillaBuilds](https://help.ubuntu.com/community/FirefoxNewVersion/MozillaBuilds) to put the Mozilla build of 3.5 on the new installation.

I can't see any reason why a Hardy/Hardy dual-boot shouldn't work, but does anyone know of any issues with this I might not be aware of?

Thanks,

James.

---

### Post by Cheesemill on 2010-01-05
There shouldn't be any problems with this, but why don't you just install Firefox 3.5 on your current Hardy? You can have more than one version of Firefox on the same installation co-existing quite happily.

---

### Post by james_mcl on 2010-01-05
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion) and other sources (some of which are no longer online) imply that it's a bit of a risky business, though I agree with you that as long as the two Firefoxes aren't sharing the same profile it doesn't *seem* particularly risky.

I'm probably just being over-cautious.

---

### Post by Zoot7 on 2010-01-05
> **james_mcl said:**
> I've had issues with the later versions of Ubuntu, so in an effort to road-test Firefox 3.5 on Hardy I'd like to change my Karmic/Hardy dual boot to a Hardy/Hardy dual boot, and follow the instructions in [https://help.ubuntu.com/community/FirefoxNewVersion/MozillaBuilds](https://help.ubuntu.com/community/FirefoxNewVersion/MozillaBuilds) to put the Mozilla build of 3.5 on the new installation.

I can't see any reason why a Hardy/Hardy dual-boot shouldn't work, but does anyone know of any issues with this I might not be aware of?

Thanks,

James.
Why don't you just download the tarball from Mozilla, extract to someplace like /opt, and put a launcher on your desktop with the command **sh /opt/firefox/firefox** or it's equivilant?
That'll cut out dealing with dependencies or repositories entirely.

And if you're worried about your firefox profile just run this to back it up:
```
cp -r ~/.mozilla ~/.mozilla.backup
```

---

### Post by RRFarFar on 2010-01-05
The help might now be needed anymore, but you should not worry using ff3.5 in ubuntu hardy. I am having no problems with it, just remember not to call firefox2 after installing 3.5.
I dont recommend using daily build repositories, since it is a daily build. I made my choice to use LTS version only, and daily builds to me are like alpha versions coming every week or so.
I would suggest to use Ubuntuzilla. This script will install the most recent ff for you.
[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page")
[http://sourceforge.net/projects/ubuntuzilla/files/]("http://sourceforge.net/projects/ubuntuzilla/files/")
[http://ubuntumanual.org/posts/193/installing-firefox-3-5-in-ubuntu-the-easy-way]("http://ubuntumanual.org/posts/193/installing-firefox-3-5-in-ubuntu-the-easy-way")

---

### Post by nanotube on 2010-01-05
> **RRFarFar said:**
> The help might now be needed anymore, but you should not worry using ff3.5 in ubuntu hardy. I am having no problems with it, just remember not to call firefox2 after installing 3.5.
I dont recommend using daily build repositories, since it is a daily build. I made my choice to use LTS version only, and daily builds to me are like alpha versions coming every week or so.
I would suggest to use Ubuntuzilla. This script will install the most recent ff for you.
[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page")
[http://sourceforge.net/projects/ubuntuzilla/files/]("http://sourceforge.net/projects/ubuntuzilla/files/")
[http://ubuntumanual.org/posts/193/installing-firefox-3-5-in-ubuntu-the-easy-way]("http://ubuntumanual.org/posts/193/installing-firefox-3-5-in-ubuntu-the-easy-way")

fyi: ubuntuzilla is no longer an installer script, but a repository of mozilla builds. even better and easier to use. :) (but that means that ubuntumanual post is now outdated)

---

### Post by james_mcl on 2010-01-06
Thanks everyone!

Firefox 3.5 now up and running thanks to Ubuntuzilla.

---

### Post by nanotube on 2010-01-06
> **james_mcl said:**
> Thanks everyone!

Firefox 3.5 now up and running thanks to Ubuntuzilla.

excellent! :)

---

### Post by RRFarFar on 2010-01-07
> **nanotube said:**
> fyi: ubuntuzilla is no longer an installer script, but a repository of mozilla builds. even better and easier to use. :) (but that means that ubuntumanual post is now outdated)

What does fyi mean? 

Sometimes even an old and outdated info leads to solution:)))

---

### Post by nanotube on 2010-01-07
> **RRFarFar said:**
> What does fyi mean? 


fyi = for your information :)

---

### Post by RRFarFar on 2010-01-08
;)That's good, I thought of something bad
Cheers

---

### Post by nanotube on 2010-01-09
> **RRFarFar said:**
> ;)That's good, I thought of something bad
Cheers

hahaha i see :)

---

