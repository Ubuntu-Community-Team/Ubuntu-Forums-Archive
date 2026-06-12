---
title: "For asking help"
date: 2009-08-09
forum: General Help
---

### Post by linux_bd on 2009-08-09
Recently i have switch to Ubuntu 8.10. Now i can realize that open source is the best. Now as a new user of Linux i am facing some problem. the problems are

1. i cant access yahoo messenger by Pidgin Messenger.( I want a link of yahoo messenger for Ubuntu 8.10)

2. I cant play the DVD .....................

Please help me for using the Ubuntu. I wont go back to Microsoft ( unsafe operating system )

---

### Post by charliehorse55 on 2009-08-09
To Get DVDs Working: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Open Pidgin, Go to accounts, click add, Select type "Yahoo Messenger" and fill in account info. Make sure in the accounts screen that the "Enabled" Check Box is checked. If an error appears, please post it here.

---

### Post by linux_bd on 2009-08-10
Thanks for dvd link. But although i cant connect yahoo in pidgin. Please give me the link of yahoo messenger for Ubuntu

---

### Post by jerrrys on 2009-08-10
[http://www.google.com/search?q=yahoo+messenger+for+Ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=yahoo+messenger+for+Ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by linux_bd on 2009-08-10
bro this method know as a infant computer user. i want actually link. where i can get the actually massenger

---

### Post by lisati on 2009-08-10
> **linux_bd said:**
> bro this method know as a infant computer user. i want actually link. where i can get the actually massenger

I don't think Yahoo messenger comes in a form that can easily be used by a new computer user with Ubuntu.

Go to the Applications->Internet->Pidgin Internet Messenger and use that instead, it can be used with Yahoo.

---

### Post by Anxious Nut on 2009-08-10
copy and paste this in your terminal:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8

echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list

> Once this PPA is setup, Pidgin updates will show up in Update Manager along with the usual Ubuntu updates. The PPA will need to be re-setup only after upgrading Ubuntu.

This PPA is maintained by one developer, so please be patient. It often lags behind the source releases a couple of days.

---

### Post by jerrrys on 2009-08-10
bro, be surprise how many do not know this...

---

### Post by linux_bd on 2009-08-10
Thanks bro for your suggestion . But i found another solution. Installing wine . Now i can use yahoo messenger 9 as like as windows

---

### Post by zkriesse on 2009-08-10
Go to this link to REALLY get your DVD's working...trust me man... [https://help.ubuntu.com/8.10/musicvideophotos/C/video.html#video-dvd](https://help.ubuntu.com/8.10/musicvideophotos/C/video.html#video-dvd)

---

### Post by linux_bd on 2009-08-10
Thanks a lot man ............

---

### Post by zkriesse on 2009-08-10
Yo man you welcome...

---

