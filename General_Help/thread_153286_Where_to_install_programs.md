---
title: "Where to install programs"
date: 2006-03-31
forum: General Help
---

### Post by DiGiTY on 2006-03-31
In what directory should I install my apps??? specifically the ones where they don't have a default path.

I'm assuming, in /usr/bin, I should then make a link to the app or make some kind of executable script thing to run the app???

---

### Post by Michael Matthews on 2006-03-31
The convention is in /usr/local. Best not to mix your stuff with system stuff.
Put /usr/local/bin in user's PATH.
If you upgrade system your stuff will be un-effected.

---

### Post by localzuk on 2006-03-31
Well that depends. /usr/bin is for the executable itself or a symlink to it. Personally, I install extra apps into /opt/ but others install into /usr/local/ and /usr/share/.

---

### Post by DiGiTY on 2006-03-31
so it should look like this? (for example)...:

folders/directory/path:

/usr/local/LimeWire
/usr/local/iTunes
/usr/local/Spankster

and the symlink or the .sh script set to run it:

/usr/local/bin/limewire.sh
/usr/local/bin/iTunes (symlink)
/usr/local/bin/spankster.sh

???

---

### Post by localzuk on 2006-03-31
Yep, except you will want the files not to have .sh for tidyness sake. You will also want those .sh files to be executable.

As the person above mentions, if you want them in /usr/local/bin you will need to have it in your path (to do this, alter /etc/profile or your personal .profile file.

---

