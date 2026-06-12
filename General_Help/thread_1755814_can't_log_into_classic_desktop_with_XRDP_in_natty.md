---
title: "can't log into classic desktop with XRDP in natty"
date: 2011-05-11
forum: General Help
---

### Post by miatawnt2b on 2011-05-11
I am using xRDP to remotely log into my desktop. I have my user set up to use the classic no-effects desktop when logging into the console.  Problem is, when I log in via xRDP, it uses unity.  How do I tell the machine to use classic no-effects when using xRDP?

-J

---

### Post by rockorequin on 2011-07-10
The site [http://scarygliders.net/2011/01/21/ubuntu-natty-xrdp-gnome-session-no-valid-session-found/](http://scarygliders.net/2011/01/21/ubuntu-natty-xrdp-gnome-session-no-valid-session-found/) points out that xrdp reads the contents of ~/.xsession to determine its session.

eg if you set this file to contain:
```

gnome-session --session=2d-gnome
```

it will start unity2d.

If you set it to:
```

gnome-session --session=classic-gnome
```

it will start with the classic desktop.

Note: xrdp seems to cache this file, so you may need to restart it first with:
```

sudo /etc/init.d/xrdp restart
```

---

