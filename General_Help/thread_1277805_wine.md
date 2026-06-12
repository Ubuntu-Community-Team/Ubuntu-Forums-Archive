---
title: "wine"
date: 2009-09-28
forum: General Help
---

### Post by saias on 2009-09-28
hi!

probably simple question. just found out about itunes and wine and im trying to install itunes.

did everything as written here: [http://www.linuxscrew.com/2007/09/19/install-itunes-72-in-ubuntu-and-other-linux-distros/](http://www.linuxscrew.com/2007/09/19/install-itunes-72-in-ubuntu-and-other-linux-distros/)

but cannot install itunes. after typing: wine iTunesSetup.exe

i get this error :wine: could not load L"C:\\windows\\system32\\iTunesSetup.exe": Module not found

after trying to load itunes.exe through wine i get an error

[/home/saias/Desktop/iTunesSetup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/saias/Desktop/iTunesSetup.exe or
          /home/saias/Desktop/iTunesSetup.exe.zip, and cannot find /home/saias/Desktop/iTunesSetup.exe.ZIP, period.


any ideas?

---

### Post by zvacet on 2009-09-29
Where did you downloaded iTunesSetup.exe?I ask you this because if you downloaded it on desktop then you have to type in terminal

```
cd Desktop
```

and after that

```
wine iTunesSetup.exe
```

You can reas more about Wine [here.]("https://help.ubuntu.com/community/Wine")

---

### Post by saias on 2009-09-29
so simple!

thanks it worked.

---

