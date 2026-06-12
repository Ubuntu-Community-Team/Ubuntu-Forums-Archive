---
title: "SOLUTION: How to Install Flash 10.3.183 manually"
date: 2011-12-07
forum: General Help
---

### Post by Spannered on 2011-12-07
Just in case you need to install manually:

When you attempt to view flash content you will receive a dialogue telling you there is a new version out, clicking this will take you to the adobe website and the package you need to download.

Alternatively you can head to Adobe.com and find the Linux package by following the links.  You'll need to close whatever browser you are using (in my case Firefox) to do the install, so copy this stuff into a gedit or similar.

If you installed the previous version through the repositories follow this process:

First you need to remove the old version, open a Terminal:```
sudo apt-get remove flashplugin-nonfree
```

Then use the copy command to move the new library into the flashplugin-installer folder: (Location 1 is wherever you downloaded the flash package to)

```
sudo cp Location1/libflashplayer.so /usr/lib/flashplugin-installer
```Open your browser again and you should be able to view up to date flash content.  In the case of Firefox stick

```
about:plugins
```into the URL bar and at the bottom of the list you should see "Flash 10.3 r183

Hope this has been helpful!

---

### Post by WorMzy on 2011-12-07
Why would you install 10.3 when 11.1 has been been out for ages?

---

### Post by pholden on 2011-12-07
The Ubuntu Software Centre will do it for you, so you shouldn't need to do anything manually... you can also add the Flash PPA to get the package through apt, see [here]("https://help.ubuntu.com/community/RestrictedFormats/Flash") :eek:

---

### Post by pretty_whistle on 2011-12-07
flashplugin-installer?

There were several threads about this installer saying it was corrupted.  It was.  I tried installing it and a window came up that said some error occurred and a partial upgrade of the OS would fix it.  I took the upgrade and then several programs would no longer work.  I ended up having to restore my system with a saved disk image backup I had.  After that, I blacklisted this thing and wouldn't take no matter what.

Several people reported the same thing I got.

---

### Post by pretty_whistle on 2011-12-07
Yeah, it can be had through the software center just don't pick the one with the word "installer" in its description.  There's another one there which doesn't have the word in it.

---

