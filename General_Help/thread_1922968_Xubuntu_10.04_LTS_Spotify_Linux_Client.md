---
title: "Xubuntu 10.04 LTS Spotify Linux Client"
date: 2012-02-09
forum: General Help
---

### Post by fleamour on 2012-02-09
Not working.  :(  Crashes.  This is CLI output:
```
fleamour@IBM-T21:~$ spotify
22:13:16.328 I [breakpad.cpp:36] Registered Breakpad for product: spotify

22:13:16.330 I [translate.cpp:123] Reloading all languages
22:13:16.464 I [breakpad.cpp:94] Searching for crashdumps: /home/fleamour/.cache/spotify/*.dmp

22:13:28.543 I [breakpad.cpp:74] Uploading crash dump: /home/fleamour/.cache/spotify/6cc98941-748e-b1d1-2960d8f5-56d7a0c3.dmp

22:13:29.966 I [breakpad.cpp:60] Crashdump upload complete: error: 0, result: 200

22:13:39.965 I [user_cache:138] UserCache::initiateGetUsers() will query for 1 users
QDBusArgument: write from a read-only object
22:13:43.428 I [ap:1754] Connecting to AP C3.spotify.com:4070
22:13:43.691 I [ap:1212] Connected to AP: 193.182.8.81:4070
Segmentation fault
```

---

### Post by cogier on 2012-02-09
Your profile says that you are running 11.10 but you say the problem relates to 10.04?

I have used Windows Spotify on 10.04, until they decided to charge for their services, with no issues at all.

Are you running the Windows version under Wine or the Linux version?

I am not saying I know the answer to your problem but you do need to be a little more specific so that others understand your problem.

---

### Post by fleamour on 2012-02-09
Sorry for the confusion.  The question is in relation to Xubuntu 10.04.  I cannot get the Linux client working, it'll crash at launch immediately after login.  Spotify GNOME Support will not install due to dependency on older version of Spotify client, but I'm not sure it is needed under XFCE.

The last time I tried Spotify Windows under Wine, it was not successful.

---

### Post by cogier on 2012-02-09
It seems strange that you can't get either the Windows version (I presume you have installed Wine) or the Linux version to work.

All I can suggest is either uninstall everything to do with Spotify and try again or reinstall Xubuntu or Ubuntu 10.04. Sorry but that's all I can think of.

---

### Post by jayshomebrew on 2012-02-10
spotify under wine:

install latest playonlinux:
```
sudo wget http://deb.playonlinux.com/playonlinux_lucid.list -O /etc/apt/sources.list.d/playonlinux.list
wget -q -O - http://deb.playonlinux.com/public.gpg | sudo apt-key add - 
sudo apt-get update
sudo apt-get install playonlinux
```

run playonlinux, click install [IMG]http://img29.imageshack.us/img29/8326/tmpcye7i8.png[/IMG]


then install spotify:
[IMG]http://img641.imageshack.us/img641/6311/tmpdpvasd.png[/IMG]

then let playonlinux install & download..
and login:
[IMG]http://img213.imageshack.us/img213/9623/tmp0h7b1p.png[/IMG]

---

