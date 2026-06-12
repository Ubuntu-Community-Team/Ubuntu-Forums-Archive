---
title: "How to play DVD's"
date: 2009-12-08
forum: General Help
---

### Post by freedom_p on 2009-12-08
Thanks for helping me to switch from Windows to a Wonderful World Ubuntu...

I would like to know how to play DVD's?

I am running 64bit Ubuntu and installed Adobe flash player and Java, 
May I know whether I can install "Restricted Extras" from Ubuntu Software Center as I already installed Flash and Java, will this conflict?

Restricted Extra already contains Flash and Java that's the reason I am worried....

---

### Post by plusnplus on 2009-12-08
Hi freedom_p,
you can install vlc player. try google it for how to install it :)

---

### Post by Citadel1980 on 2009-12-08
I don't use 64 bit Ubuntu but I do know that there are problems when it is used in conjunction with Flash/Java.

I can't tell you how to overcome these limitations other than installing 32 bit Ubuntu. 

This webpage explains your problem and offers some solutions:

[http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/](http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/)



Also, here is a Google Search of your problem:

[http://www.google.com/search?q=ubuntu+64+bit+flash+and+java&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=ubuntu+64+bit+flash+and+java&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)


Sorry I couldn't offer more help.

---

### Post by kdcoetzee on 2009-12-08
try mplayer.

```
sudo apt-get install mplayer
```

then to play a movie

```
mplayer dvd://
```

and if you want to play encrypted dvd you will need libdvdcss

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by jmszr on 2009-12-08
freedom_p,

This should be of help: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

