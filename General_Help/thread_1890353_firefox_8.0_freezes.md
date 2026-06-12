---
title: "firefox 8.0 freezes"
date: 2011-12-03
forum: General Help
---

### Post by lalawawa on 2011-12-03
I recently upgraded to Ubuntu 11.04 Natty Narwhal, and with it upgraded to firefox 8.0.

Now, upon loading a new web page, firefox often (not always) freezes for a minute or two.  When it does, it says

/usr/lib/firefox-8.0/plugin-container: /usr/lib/libnss3.so: version `NSS_3.12.10' not found (required by /usr/lib/firefox-8.0/libxul.so)

I checked and I do indeed have the library /usr/lib/libnss3.so.  So what do I have to do to get firefox working right?

---

### Post by 2F4U on 2011-12-03
There seems to be a workaround in this bug description:

[https://bugs.launchpad.net/ubuntu/+source/nss/+bug/880566](https://bugs.launchpad.net/ubuntu/+source/nss/+bug/880566)

---

### Post by oldtimer7777 on 2011-12-03
Have you installed the PPA for firefox and then updated? 

[https://debianhelp.wordpress.com/2011/07/05/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](https://debianhelp.wordpress.com/2011/07/05/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

It is about 1/3rd the way down the list to get that installed...  enjoy

> **lalawawa said:**
> I recently upgraded to Ubuntu 11.04 Natty Narwhal, and with it upgraded to firefox 8.0.

Now, upon loading a new web page, firefox often (not always) freezes for a minute or two.  When it does, it says

/usr/lib/firefox-8.0/plugin-container: /usr/lib/libnss3.so: version `NSS_3.12.10' not found (required by /usr/lib/firefox-8.0/libxul.so)

I checked and I do indeed have the library /usr/lib/libnss3.so.  So what do I have to do to get firefox working right?

---

### Post by lalawawa on 2011-12-04
I looked on the web page you cited and did

$ sudo add-apt-repository ppa:mozillateam/firefox-stable
$ sudo apt-get update
$ sudo apt-get upgrade

and rebooted.  But web pages still freeze.

---

### Post by lalawawa on 2011-12-04
2F4U's post said the problem went away in 11.10.  Also, firefox 7 is available on that version, so I can always go back to firefox 7 if I get 11.10.

---

### Post by lswb on 2011-12-04
Perhaps not related to your problem, but is it happening on sites that use java, and if so, are you using the Sun/Oracle version? I've experienced the gray-out freezing when using sun java but it went away when I switched to the iced tea version.

---

### Post by lalawawa on 2011-12-04
I upgraded to 11.10 and *HATED* it.  There was a graphics glitch at the top of my background.  All the menus are changed around and I couldn't find anything.  I figured I would get used to it, then EVERYTHING but the cursor froze solid and stayed that way.  So I had gone from having one firefox window at a time freezing for a couple of minutes to having ALL windows freeze solid and stay that way.

I had backed up before the upgrade, so I wiped my disk clean and re-installed Ubuntu 10.04.  I'm now running firefox 3.6.24, so I expect my problems will be over.

---

