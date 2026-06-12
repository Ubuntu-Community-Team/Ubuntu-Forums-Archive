---
title: "Where does Firefox store it's Bookmarks?"
date: 2011-02-14
forum: General Help
---

### Post by daldude on 2011-02-14
Where does Firefox store or save it's bookmarks as you add more of them? If someone did not backup their bookmarks after adding some new ones what directory can the go to find where Firefox stores or saves the bookmarks?

---

### Post by oldfred on 2011-02-14
It is in your profile. I houseclean and backup full profiles for Firefox & Thunderbird.

I saved this command so it must be where it is saved as it now is in a sqlite file. There are multiple sqlite files for different things.
sqlite3 $HOME/.mozilla/firefox/yourprofile/places.sqlite "vacuum"

Firefox optimization and troubleshooting thread 
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

[http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html](http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html)

[http://kb.mozillazine.org/Profile_Manager#Linux](http://kb.mozillazine.org/Profile_Manager#Linux)

---

### Post by jerrrys on 2011-02-14
is this what your looking for ?

[ATTACH]183457[/ATTACH]

---

