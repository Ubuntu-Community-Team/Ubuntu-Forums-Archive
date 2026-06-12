---
title: "Firefox 3-5 E. broken packages"
date: 2009-08-10
forum: General Help
---

### Post by zitstif on 2009-08-10
I have a bit of an annoying qualm on my hands:

[B]
E: /var/cache/apt/archives/firefox-3.5-branding_3.5.3~hg20090809r26204+nobinonly-0ubuntu1~umd1~hardy_i386.deb: trying to overwrite `/usr/share/applications/firefox.desktop', which is also in package firefox-3.0[/B]

I have previously installed a beta version of firefox "Shiretoko" and after trying to do some updates at a later time, ran into this problem.

Has anyone else had this specific problem?

I've tried:

sudo apt-get -f install 

but this yields:

[B]Do you want to continue [Y/n]? y
(Reading database ... 191031 files and directories currently installed.)
Preparing to replace firefox-3.5-branding 3.5.3~hg20090803r26189+nobinonly-0ubuntu2~umd1~hardy (using .../firefox-3.5-branding_3.5.3~hg20090809r26204+nobinonly-0ubuntu1~umd1~hardy_i386.deb) ...
Unpacking replacement firefox-3.5-branding ...
dpkg: error processing /var/cache/apt/archives/firefox-3.5-branding_3.5.3~hg20090809r26204+nobinonly-0ubuntu1~umd1~hardy_i386.deb (--unpack):
 trying to overwrite `/usr/share/applications/firefox.desktop', which is also in package firefox-3.0
Errors were encountered while processing:
 /var/cache/apt/archives/firefox-3.5-branding_3.5.3~hg20090809r26204+nobinonly-0ubuntu1~umd1~hardy_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/B]

Any words of wisdom I would greatly appreciate.

---

### Post by pototo on 2009-08-10
Same problem here, now I can't use apt-get to install new packages.

---

### Post by liska on 2009-08-10
quick fix:
!!! will remove firefox-3.0, so you'll end up with firefox-3.5 only !!!

```
dpkg -r firefox-3.0-gnome-support
dpkg -r firefox-3.0
apt-get -f install
```

---

### Post by pototo on 2009-08-10
thank you liska, that solved the problem. I wasn't using firefox 3 anymore.

---

### Post by mantid on 2009-08-13
I too had this problem and also needed to remove mozilla-mplayer:
```
dpkg -r mozilla-mplayer
```

before being able to properly install firefox-3.5-branding.

---

### Post by zitstif on 2009-08-13
Ah thank you, when I get a chance I will do this.

---

### Post by Rob_H on 2009-08-13
> **pototo said:**
> thank you liska, that solved the problem. I wasn't using firefox 3 anymore.

I tried doing this a while back and all of the default search engines disappeared from Firefox 3.5. I had to reinstall 3.0 to get them back. But 3.0 and 3.5 coexist peacefully on my box. I just change the **/usr/bin/firefox** symlink to point to 3.5, delete the "Preview Browser" icon, and 3.0 is effectively hidden.

---

### Post by Ranax on 2009-08-13
Is Firefox 3.5 now being shipped by Canonical?

---

### Post by Rob_H on 2009-08-13
> **Ranax said:**
> Is Firefox 3.5 now being shipped by Canonical?

If by "shipped" you mean is it in the Jaunty repository, then yes. The package name is "firefox-3.5". It installs alongside Firefox 3.0, though. It does not replace it. But you can easily make it the default using the process I mentioned above: switch the symlink, delete one of the icons.

---

### Post by Ranax on 2009-08-13
> **Rob_H said:**
> If by "shipped" you mean is it in the Jaunty repository, then yes. The package name is "firefox-3.5". It installs alongside Firefox 3.0, though. It does not replace it. But you can easily make it the default using the process I mentioned above: switch the symlink, delete one of the icons.

So basically it's still Shiretoko?

---

### Post by Rob_H on 2009-08-13
> **Ranax said:**
> So basically it's still Shiretoko?

I believe so. It's 3.5.2 in any case.

---

### Post by jmzolezzi on 2009-08-13
Sorry if this is a newbie question, but when could I expect Ubuntu to update our current Firefox installation to 3.5.2 via the Update Manager?

I've read how to enable Firefox 3.5 but I'd prefer not to have 2 copies of Firefox and wait until Ubuntu updates it.

---

### Post by Ranax on 2009-08-13
> **jmzolezzi said:**
> Sorry if this is a newbie question, but when could I expect Ubuntu to update our current Firefox installation to 3.5.2 via the Update Manager?

I've read how to enable Firefox 3.5 but I'd prefer not to have 2 copies of Firefox and wait until Ubuntu updates it.

They are only releasing the official Firefox 3.5.x for 9.10/Karmic, not 9.04/Jaunty.

---

