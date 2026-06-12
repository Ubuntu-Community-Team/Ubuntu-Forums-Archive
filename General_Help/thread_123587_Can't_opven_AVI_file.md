---
title: "Can't opven AVI file"
date: 2006-01-30
forum: General Help
---

### Post by Elakt on 2006-01-30
Can't open a avi file made from a windows friend..not in any program..vlc..totem mplayer... help!

---

### Post by Neo Ex on 2006-01-30
Install the codecs: go at [http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html) and download the package, unpack it and copy the codecs in /usr/lib/win32.
To do this you can use Konqueror as root (type 'kdesu konqueror' in a terminal) or, if you prefer, typing
sudo mkdir /usr/lib/win32
sudo cp essential-20050412/* /usr/lib/win32

---

### Post by olale on 2006-01-30
Or, add "multiverse" to your repositories and install the package "w32codecs".

In adept, try the menu Adept -> Manage Repositories and look for the comment "Main ubuntu repository". In the components section to the right on the line below the comment add "multiverse". Then perform a "fetch updates" and search for the package "w32codecs".

---

### Post by Elakt on 2006-01-30
thx olale that solved it :)

---

### Post by olale on 2006-01-30
You're welcome, glad I could help :)

---

