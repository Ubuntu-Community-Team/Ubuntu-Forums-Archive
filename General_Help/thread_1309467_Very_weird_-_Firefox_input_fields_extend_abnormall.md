---
title: "Very weird - Firefox input fields extend abnormally long - screwing up page layouts."
date: 2009-11-01
forum: General Help
---

### Post by Shekibobo on 2009-11-01
This started shortly after upgrading to Karmic beta a little over a week ago.  Web pages that have text fields of an unspecified size default to overly large widths.  It only seems to be happening on my computer (I've checked other linux computers, but under Fedora), and only on Firefox (I also use Chrome, but everything's fine there).  I'm using Mozilla Firefox for Ubuntu version 3.5.4 under Karmic.

I've attached a  screenshot of this phenomenon.

Also, the upload image page is a particular problem, as the window is a certain size, but the input fields extend to about twice the window width.  Very strange.

---

### Post by Syam_ on 2009-11-02
Have the same issue :( (Karmic upgrade from Jaunty)

Not tested on Windows Firefox 3.5 version

[Edit]
Not happen on my laptop Ubuntu installation (Karmic upgrade from Jaunty too)

---

### Post by Shekibobo on 2009-11-02
Solved.

Apparently it is an issue with the font being used in the system.  I was using an emulated Lucida Grande Mac font as the system default which has a bad standard character width (from what I figured out from [https://bugzilla.mozilla.org/show_bug.cgi?id=491114](https://bugzilla.mozilla.org/show_bug.cgi?id=491114)).  I removed the counterfeit Lucida fonts from my system and replaced them with the official mac fonts found here: [http://isuman.blogspot.com/2008/09/lucida-grande-fonts-for-windows.html](http://isuman.blogspot.com/2008/09/lucida-grande-fonts-for-windows.html), and changed my system fonts using these.  All my Firefox input field woes are now in the past.  Change your font, fix the problem.

---

### Post by Syam_ on 2009-11-02
I found this quick fix for the font rendering in FF :
[http://timka.org/tech/2009/05/02/firefox-3.5-in-jaunty/](http://timka.org/tech/2009/05/02/firefox-3.5-in-jaunty/)

Work great for font rendering.

(don't have restarted my FF cause need to keep some sessions until tonight. so don't know if it fix the input issue, will post later tonight)

---

### Post by Syam_ on 2009-11-02
Thanks for fix !

---

### Post by haocheng on 2009-11-02
Changed font fixed my problem, too. Thanks a lot!!

---

