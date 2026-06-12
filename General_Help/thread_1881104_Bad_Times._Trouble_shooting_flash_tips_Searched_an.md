---
title: "Bad Times. Trouble shooting flash tips? Searched and tried &amp; nothing worked"
date: 2011-11-14
forum: General Help
---

### Post by mindgernade on 2011-11-14
Some not all youtube video's will just be black and no sound or video. Some other video's will just play sound and no/ or choppy video. Other video's play perfect. I have tryed removing and purging all data using.

sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

and I reinstalled the flash deb.
I also tried just removing and reinstalling. Is there a way to trouble shoot, like maybe a page that has many formats on it so I can tell what its failing on.

---

### Post by jerrrys on 2011-11-16
have you tried flashaid?

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/?src=search](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/?src=search)

a good place for ff answers

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

