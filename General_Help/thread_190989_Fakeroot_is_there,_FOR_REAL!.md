---
title: "Fakeroot is there, FOR REAL!"
date: 2006-06-06
forum: General Help
---

### Post by SZF2001 on 2006-06-06
Ugh. I'm trying to install the latest ndiswrapper.

I went to the wiki page ([here](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?highlight=%28ndis%29)) and I get to the fakeroot part (4.3) and this is what I get:

```
root@ColemanNetwork:~/ndis/ndiswrapper-1.17# fakeroot debian/rules binary-modules
/usr/bin/fakeroot: line 150: debian/rules: No such file or directory

```

Please note I've updated to 6.06 Ubuntu lately. Wow, what an improvement, it's even MORE a pain in the *** then it ever was before. Thanks! ](*,)

EDIT: And just in case, yes, I've already run apt-get install fakeroot and it says it's already in the system. No updates either, it's the highest datest fakeroot. It's there. I don't understand...

---

### Post by ejos on 2006-06-06
I don't think it's complaining about fakeroot not being there, but rather that debian/rules thing on line 150. This is what's on line 150 of fakeroot: FAKEROOTKEY=$FAKEROOTKEY LD_LIBRARY_PATH="$PATHS" LD_PRELOAD="$LIB" "$@"

I have no idea what the problem is though.

---

### Post by SZF2001 on 2006-06-06
Well... Yea. I guess so.

But still. 5.10 used to be able to do this - where did the debian/rule thing go?:mad:

---

### Post by ejos on 2006-06-06
OOOOOOOOOHHHHHHHHHH!!!!
Try putting fakeroot "debian/rules" binary-modules instead.
debian/rules is usually a file for making debian packages.

---

### Post by SZF2001 on 2006-06-06
Should I just edit it using sudo gedit?

EDIT: I think in your excitement you... kinda confused me. Just switch the words or something?

I gotta make the .deb packages to get ndiswrapper though.

EDIT2: In the terminal I tried that again putting the " things around it. No luck, same error message.

---

### Post by ejos on 2006-06-06
well type "ls" and see if debian/rules is actually in that folder.

---

