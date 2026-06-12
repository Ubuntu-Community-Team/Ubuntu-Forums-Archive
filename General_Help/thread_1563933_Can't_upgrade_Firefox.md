---
title: "Can't upgrade Firefox"
date: 2010-08-29
forum: General Help
---

### Post by rMatey on 2010-08-29
I upgraded from 9.10 to 10.04 on my laptop.  Worked great, no problems.  Now I tried to upgrade Firefox to 3.6.9 from 3.6.8 using Ubuntuzilla.  Any way I get the following from the terminal:
E: firefox-mozilla-build: subprocess installed post-removal script returned error exit status 2
  This is an earlier package which somehow got corrupted.  Anyhow, the Package Manager and every other way I tried to remove it doesn't work.  How to do???

---

### Post by blazemore on 2010-08-29
You can force-remove the offending package using the terminal.

Enter the following command, followed by pressing Enter:
```
sudo dpkg --force-all -r firefox-mozilla-build
```

Ubuntuzilla doesn't support Lucid (I think).

However, Mozilla provide a ppa with upstream builds, which they publish on Launchpad.

Use the following command to add this PPA:
```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```

I hope this helps.

---

### Post by lovinglinux on 2010-08-29
Ubuntuzilla supports Lucid, what it doesn't support is 64bit.

See other methods of Firefox installation and additional PPA repositories at [[COLOR="Sienna"]**Installing Other Versions**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html) tutorial.

If you want to try Firefox 4 Beta, then see [http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html](http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html)

---

### Post by rMatey on 2010-08-30
Terminal reports "dpkg-divert:mismatch on package when removing 'diversion of /usr/bin/firefox.ubuntu by firefox-mozilla-build.   found 'local diversion of usr/bin/firefox to /usr/bin/firefox.ubuntu'     error processing firefox-mozilla-build )--remove)      subprocess installed post-removal script returned exit status 2.

  That's what I've been getting.  I tired Debfoster and all of the package removing techniques that I knew.  Looks like I need to just re-install from a fresh disc.  I prolly upgraded once too many times.  And playing with packages and different upgrades to programs just did me in.  (It's 32-bit anyhow.
   :}    I got a fresh backup of all my files, so I'm good.   Thanks!!!!

---

### Post by rMatey on 2010-08-30
32-bit.  But I updated from the Software Center, Ubuntuzilla and Ubuntu Tweak.   Not to mention straight from Mozilla.org

  Gee!  I don't understand why I have a problem.   (snark)

---

### Post by wojox on 2010-08-30
Make sure you bookmark lovinglinux's page. I've yet to see a Firefox problem he hasn't resolved.

---

### Post by rMatey on 2010-08-30
**SOLVED**


> **wojox said:**
> Make sure you bookmark lovinglinux's page. I've yet to see a Firefox problem he hasn't resolved.
I checked lovinglinux's page.  It wouldn't let  me install a new FF either.  Couldn't execute a removal, too.  I fixed it.  A fresh re-install.  It worked a lot nicer than the distro upgrades.  I mean it worked, but somehow some crud must have gotten smeared from each upgrade from 7.04 thru 10.04.  Now I gots me a fresh new install...with a backup of all my files carried over.

---

### Post by lovinglinux on 2010-08-30
> **wojox said:**
> Make sure you bookmark lovinglinux's page. I've yet to see a Firefox problem he hasn't resolved.

Thanks wojox, but I do have a list of unresolved threads. Is not huge, but it exists :)

> **rMatey said:**
> **SOLVED**

I checked lovinglinux's page.  It wouldn't let  me install a new FF either.  Couldn't execute a removal, too.  I fixed it.  A fresh re-install.  It worked a lot nicer than the distro upgrades.  I mean it worked, but somehow some crud must have gotten smeared from each upgrade from 7.04 thru 10.04.  Now I gots me a fresh new install...with a backup of all my files carried over.

I'm glad you solved it. We could have fixed it without a clean install. Nevertheless, since you have been upgrading since 7.04 it was a good move. I only do clean installs here. Have you created a separate partition for home?

---

### Post by rMatey on 2010-08-31
> **lovinglinux said:**
> Thanks wojox, but I do have a list of unresolved threads. Is not huge, but it exists :)



I'm glad you solved it. We could have fixed it without a clean install. Nevertheless, since you have been upgrading since 7.04 it was a good move. I only do clean installs here. Have you created a separate partition for home?
Yes on the /home partition.  I also use a 500 Gig USB harddrive for a safety backup of the /home paretition on the second harddrive.... just in case.

---

