---
title: "Wallch headache..."
date: 2011-08-25
forum: General Help
---

### Post by pasha811 on 2011-08-25
I am running Natty @ 64bit. It seems no package exists for Wallch, the Gnome Wallpaper changer compatible with Unity except for a 32bit version. Did anybody succeed in installing it on a 64bit system?
Can you provide instructions or (yes.. I am lazy) a package? I'd avoid to compile from source if possible. :confused:

- Best
- Pasha811

---

### Post by IWantFroyo on 2011-08-25
If you install the ia32 library, you will be able to run 32-bit programs.
```
sudo apt-get install ia32-libs
```

---

### Post by mendhak on 2011-08-25
Have a look at the [omgubuntu article about wallch]("http://www.omgubuntu.co.uk/2011/08/wallch-wallpaper-changer-adds-unity-features/"), in the comments.  A guy named 'Robin Jacobs' posted a link to a 64 bit deb of wallch.

There's also a comment by 'Manuel Trujillo' about compiling it in 64 bit.

I don't actually know anything about compiling it for 64bit but I do remember the article and comments on omgubuntu from a few days ago.

---

### Post by pasha811 on 2011-08-26
Just used Robin Jacobs links you suggested, installation was a breeze!

Thank you!:P

---

### Post by hakermania on 2011-08-26
Hello pasha811, as a developer I suggest trying the 64 bit testing ppas, they are good ;)
Sorry for not providing instantly the 64 bit DEBs but we are all newbies with packaging and the whole system :)
[https://launchpad.net/~wallch/+archive/wallch-gnome2/+builds?build_state=built]("https://launchpad.net/%7Ewallch/+archive/wallch-gnome2/+builds?build_state=built")

---

