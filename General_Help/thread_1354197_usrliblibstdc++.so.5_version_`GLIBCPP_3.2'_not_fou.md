---
title: "/usr/lib/libstdc++.so.5: version `GLIBCPP_3.2' not found"
date: 2009-12-13
forum: General Help
---

### Post by techbrainless on 2009-12-13
Hi All,

I am trying to start Xten X-lite softphone (from Counterpaths ) on ubuntu 9.10 desktop , 

of course libstdc++.so.6.0.13 is installed on my machine so i made symbolic link
```
$sudo ln -s /usr/lib/libstdc++.so.6.0.13 /usr/lib/libstdc++.so.5
```

I am getting the following error
```
$ sudo ./xtensoftphone 
./xtensoftphone: /usr/lib/libstdc++.so.5: version `GLIBCPP_3.2' not found (required by ./xtensoftphone)
./xtensoftphone: /usr/lib/libstdc++.so.5: version `CXXABI_1.2' not found (required by ./xtensoftphone)
```

how to fix the issue...

---

### Post by mc4man on 2009-12-13
> how to fix the issue...
You may or may not be able to, (depends mainly on your app 

**Remove your symlink**, download and install libstdc++ from here for your arch.

[http://packages.ubuntu.com/jaunty/libstdc++5](http://packages.ubuntu.com/jaunty/libstdc++5)

Then see...

---

### Post by techbrainless on 2009-12-14
Thanks alot mc4man,

I have followed the instructions in your reply and works with me.

---

### Post by jctweb on 2009-12-18
This helped me in solving an issue with an old Dell 720 Printer as well - from this thread:
[http://ubuntuforums.org/showthread.php?t=49714&page=58](http://ubuntuforums.org/showthread.php?t=49714&page=58)

---

### Post by genti on 2010-02-26
If you are running x64_68 you can download the 32bit package from the link above and extract the *.deb files (dpkg-deb --extract <package> <targetdir>)
then copy the necessary library files from the extracted packages to /usr/lib32/

Edit: I got it to work but then I got Ekiga to work so I switched to Ekiga.

---

