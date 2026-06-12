---
title: "Update manager - Could not exec dpkg!"
date: 2010-03-11
forum: General Help
---

### Post by davidpbrown on 2010-03-11
Update manager stuck today, with 8 'important' updates - several Apache and a dpkg-dev.

Error is 
```
Preconfiguring packages ...
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)
A package failed to install. Trying to recover:
sh: dpkg: Permission denied

```

this is a little beyond me but I gathered that sometimes it helps doing ```
sudo apt-get -f install
```

Output from that is 
```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  liballegro4.2-plugin-jack libaldmb1 libdns50 libguichan-0.8.1-1
  liblog4j1.2-java libcommons-cli-java libswt-gtk-3.4-java libflickrnet2.2-cil
  libswt-gnome-gtk-3.4-jni libguichan-allegro-0.8.1-1 language-pack-zh-base
  libdumb1 libcommons-lang-java language-pack-gnome-zh-base
  libswt-cairo-gtk-3.4-jni liballegro4.2 language-pack-kde-zh-base
  libswt-gtk-3.4-jni java-wrappers libswt-mozilla-gtk-3.4-jni
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)

```

I stopped apache but that makes no difference.

I can't see mention of this already but then haven't been doing anything extra-ordinary. The system updates itself automatically for important changes and I do others regularly but not had this before.

?

---

### Post by davidpbrown on 2010-03-11
It struck me the cause of this might be the obvious access to dpkg. I found /usr/bin/dpkg had no rights for root or any other!

So, I made those rights the same as deb-dpkg. That is read write for owner, read only for group and others.

That fixed it but what caused it still isn't known.

---

### Post by danharris83 on 2011-04-11
i had a similar error Could NOt Exec dpkg!

all i did is changded the dpkg file so it could be used as a exe dont know why it had ben changed but all good now.

---

