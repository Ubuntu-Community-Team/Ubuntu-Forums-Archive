---
title: "minitube not working"
date: 2011-08-04
forum: General Help
---

### Post by ghost45 on 2011-08-04
I am using Ubuntu 11.04 on a 32-bit computer. I have looked for a solution for a few hours before posting this but could not find anything. My problem is that even when I download and install all of the dependencies for minitube, it will not play the videos. I can open it and search for something but once the search is done and the list of videos comes up, minitube just starts going down the list, skipping one after another. I have tried installing different versions of minitube via different repositories but the problem still persists...Hopefully someone can help? =]

Any help is appreciated, even if I have already tried it once, I will try again because maybe I did something wrong.

Thanks in advance.

---

### Post by northwestern on 2011-08-04
This has also just started happening to me, reoved and re-installed twice, but still doing the same thing.

Northwestern

---

### Post by kerry_s on 2011-08-04
There was a change on the YouTube side, you'll have to wait for an update fix.

---

### Post by ghost45 on 2011-08-04
Oh okay well that would make sense...Hopefully there will be a fix for it here soon.

---

### Post by beew on 2011-08-05
There are some changes in Youtube that break all third party Youtube viewers, Umplayer's Youtube viewer has stopped working as well 

However, it is also true that the version of mintube in the repo is very outdated and broken even though the fix has been released months before 11.04 was released, so it wouldn't have worked even without the recent changes in Youtube if you install from Ubuntu's repo. You should add this ppa and wait for an update.  [https://launchpad.net/~nilarimogard/+archive/webupd8]("https://launchpad.net/%7Enilarimogard/+archive/webupd8")

---

### Post by Ric_NYC on 2011-08-05
I think Youtube is blocking anything that is not a web browser.

---

### Post by kerry_s on 2011-08-05
> **Ric_NYC said:**
> I think Youtube is blocking anything that is not a web browser.

I don't think so, YouTube apps on tablets still work.

---

### Post by NoBugs! on 2011-08-05
> **kerry_s said:**
> There was a change on the YouTube side, you'll have to wait for an update fix.

I'm guessing that's the reason Totem Movie Player no longer plays YouTube? Any estimate on an update?

---

### Post by kerry_s on 2011-08-05
> **NoBugs! said:**
> I'm guessing that's the reason Totem Movie Player no longer plays YouTube? Any estimate on an update?

i was using totem for youtube as well, much lighter than minitube & no qt. no idea on the fix time frame. i heard the firefox plugin got fixed, so it might be something simple & quick to fix on the others. just a waiting game for now.

---

### Post by beew on 2011-08-05
It is fixed. You can wait for update from your ppa or download version1.5  from minitube.

[http://flavio.tordini.org/minitube-1-5-to-the-rescue](http://flavio.tordini.org/minitube-1-5-to-the-rescue)

---

### Post by kerry_s on 2011-08-05
> **beew said:**
> It is fixed. You can wait for update from your ppa or download version1.5  from minitube.

[http://flavio.tordini.org/minitube-1-5-to-the-rescue](http://flavio.tordini.org/minitube-1-5-to-the-rescue)

That's good news. I guess us totem users aren't as lucky.

---

### Post by andrew.46 on 2011-08-06
Looks like youtube-dl has been updated for the latest changes:

```

andrew@skamandros~$ **[COLOR="Red"]youtube-dl --update[/COLOR]**
Updating to latest stable version...
Updated to version 2011.08.04

```

---

### Post by Anarkotiko21 on 2011-08-09
HI , im new to Linux and dont know how to upgrade to the new version ....  donwloading the binaries from the web and then ? thnx

---

### Post by fragos on 2011-08-10
The Ubuntu repositories haven't been updated for minitube yet. I follow [http://www.omgubuntu.co.uk/](http://www.omgubuntu.co.uk/) which offered the developers repository so it could be added to Ubuntu's Software Sources. Any repository in the sources will be automatically update Ubuntu for any aps you've installed.

---

