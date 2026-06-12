---
title: "Unity's bar configuration file?"
date: 2011-06-26
forum: General Help
---

### Post by hakermania on 2011-06-26
I learned how to do unity-interaction and I want to add there a single entry that contains a  bunch of scripts (on the right click) to do simple programming and such jobs, like compile, archive, send to the server via ftp etc...

But, as you know, scripts are NON-GUI and so that's why I cannot just search for the application (actually it searches for the .desktop file which points to the application (the .desktop file also is responsible for the unity interaction) in /usr/share/applications/ folder) and launch it, and then pin it on the launcher and use the interaction whenever I want.

So, I'd like to pin the .desktop file by hand.
It should be a configuration file somewhere around that remembers the current launchers etc :)

Any help appreciated :)

---

### Post by hakermania on 2011-06-27
bummmp

---

### Post by hakermania on 2011-07-03
desperate bump!

---

### Post by hakermania on 2011-07-09
More desperate bump!

---

### Post by fragos on 2011-07-09
Perhaps this will help you.

[http://ubuntuguide.net/manage-ubuntu-11-04-unity-launcher-quicklist-using-unity-launcher-editor](http://ubuntuguide.net/manage-ubuntu-11-04-unity-launcher-quicklist-using-unity-launcher-editor)

---

### Post by drs305 on 2011-07-09
> **hakermania said:**
> 
So, I'd like to pin the .desktop file by hand.
It should be a configuration file somewhere around that remembers the current launchers etc :)


I have Oneiric open at the moment but suspect it's the same in Natty. If you have dconf-tools installed you can open dconf-editor and drill down to *desktop.unity.launcher favorites* and it will display the ones added with "Keep in launcher".

---

### Post by hakermania on 2011-07-10
thanks guys!

---

