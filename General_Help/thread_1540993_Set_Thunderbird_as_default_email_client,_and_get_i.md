---
title: "Set Thunderbird as default email client, and get it to open with the mail icon"
date: 2010-07-28
forum: General Help
---

### Post by neigaard on 2010-07-28
Hi

How do I set Thunderbird to be my default email client, and make the little mail icon in the top menu bar?

Thank you
Søren

---

### Post by howefield on 2010-07-28
> **neigaard said:**
> How do I set Thunderbird to be my default email client,

System > Preferences > Preferred Applications.

> and make the little mail icon in the top menu bar?

Try this guide.

[http://www.omgubuntu.co.uk/2010/05/how-to-add-thunderbird-to-messaging.html](http://www.omgubuntu.co.uk/2010/05/how-to-add-thunderbird-to-messaging.html)

---

### Post by spikoley on 2011-03-18
> **howefield said:**
> System > Preferences > Preferred Applications.

Try this guide.

[http://www.omgubuntu.co.uk/2010/05/how-to-add-thunderbird-to-messaging.html](http://www.omgubuntu.co.uk/2010/05/how-to-add-thunderbird-to-messaging.html)

This worked for me.  I used the custom option to open Yahoo! Mail.

Select Custom on the drop down then enter in the browser with the website address.

```
google-chrome http://mail.yahoo.com
```

---

### Post by bobpress on 2011-03-18
[B][SIZE=1][B]Thunderbird Indicator puts notification in the mail icon.
[/B][/SIZE][/B]

[https://launchpad.net/libnotify-mozilla](https://launchpad.net/libnotify-mozilla)

---

### Post by kopiluac on 2011-03-18
Would have deleted the post but don't see how to do that. My apologies.

---

### Post by xannen on 2011-04-29
> **bobpress said:**
> [B][SIZE=1][B]Thunderbird Indicator puts notification in the mail icon.
[/B][/SIZE][/B]

[https://launchpad.net/libnotify-mozilla](https://launchpad.net/libnotify-mozilla)

Hi

I'm new to linux and Ubuntu.  I've installed Ubuntu 11.04.

I have always used Thunderbird, and it would be nice if I can continue doing so when I am on linux.

I've changed the default mail reader to Thunderbird via: System > Preferences > Preferred Applications.

However, the system tray icon is still link with Evolution.

I went to look into the guide: [http://www.omgubuntu.co.uk/2010/05/h...messaging.html]("http://www.omgubuntu.co.uk/2010/05/how-to-add-thunderbird-to-messaging.html")

But the link was broken.

Next I saw: [https://launchpad.net/libnotify-mozilla](https://launchpad.net/libnotify-mozilla)

However, I don't know how to install it.  I've not familiar with command line installation, but I'm learning.  So far I only know how to use the sypnatic package manager: installing, upgrading, removing programs, and adding new repository.

Can someone enlighten me on how to make Thunderbird my standard email client, as if it was installed as default email, similar to Evolution?

Thank you in advance.

Xannen

---

### Post by Rasa1111 on 2011-04-29
Hi xannen,

 Here is the omgubuntu link, fixed~ [http://www.omgubuntu.co.uk/2010/05/how-to-add-thunderbird-to-the-ubuntu-messaging-menu/](http://www.omgubuntu.co.uk/2010/05/how-to-add-thunderbird-to-the-ubuntu-messaging-menu/)

Im going to attempt to get this working on my system, and if I succeed, I'll come back and tell you how. lol

:)

---

### Post by Rasa1111 on 2011-04-29
Well that was quick! (and easy!)

 on the launchpad page, [https://launchpad.net/~ruben-verweij/+archive/thunderbird-indicator/+packages](https://launchpad.net/~ruben-verweij/+archive/thunderbird-indicator/+packages)
.... is this .deb package~ [https://launchpad.net/~ruben-verweij/+archive/thunderbird-indicator/+files/xul-ext-indicator_1.4-0ubuntu1_all.deb](https://launchpad.net/~ruben-verweij/+archive/thunderbird-indicator/+files/xul-ext-indicator_1.4-0ubuntu1_all.deb)

 I simply downloaded the .deb file, 
installed it via software center 
(just clicking deb file after downloaded will open it in software center), let it install..
and as soon as it was finished..
Thunderbird is now is my menu! :)

See proof>[ATTACH]190346[/ATTACH]  lol  
Opens and works perfectly. <3

Good luck! hope it works for you. :guitar:

---

### Post by Rasa1111 on 2011-04-29
One last word..

To allow it to "minimize to tray" ,
install this thunderbird add-on [https://addons.mozilla.org/en-US/thunderbird/addon/minimizetotray-plus/](https://addons.mozilla.org/en-US/thunderbird/addon/minimizetotray-plus/)

It gives a handful of nice options, and works great!  :)

---

