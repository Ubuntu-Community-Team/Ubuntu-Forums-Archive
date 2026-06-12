---
title: "libstdc++ issues"
date: 2010-02-15
forum: General Help
---

### Post by portlandaudio on 2010-02-15
Hello
I am trying to install americas army 2.5 on my kubuntu laptop. It installed fine but when i try to start the game it says....

./armyops-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory


So i have read on forums that i need to install libstdc++.so.5 

When i attempt this from terminal i type sudo apt-get install libstdc++.so.5 and it says.... 

E: Couldn't find package libstdc++.so.5


And it turns out i already have a newer version of libstdc. I have libstdc++6

So how do i work around this?

Please! Any help would be great!!!!

---

### Post by ellgor on 2010-02-16
Hi,

To get the Lib you need, go to Debian packages (type it in the search bar and it'll get you there) look for Lenny packages when you get the list for it look for "Old Libaries", if this hasn't got it try one of the other releases, Sid or Squeeze, until you find it. As to getting it to work it may call for the removal of the newer lib, try adding the old first and see if it complains, if it does you will have to remove the newer one (watch for any apps later looking for it).

Regards, Ellgor.

---

### Post by portlandaudio on 2010-02-16
Ok, so i found this....


[http://packages.debian.org/lenny/i386/libstdc++5/download](http://packages.debian.org/lenny/i386/libstdc++5/download)

And i downloaded it. How do i run it? Sorry, im a noob to linux.

---

### Post by portlandaudio on 2010-02-16
ok, scratch that. I found the download and it just opened and installed. The game ran after that but it would not log on to the internet to load my player account. Any ideas? My firefox has internet. Is there an update for this game that i dont know about? Im using americas army 2.5 for linux. I believe its the latest version supported.

---

