---
title: "Is it possible to install Dropbox with a different file manager than Nautilus?"
date: 2011-05-18
forum: General Help
---

### Post by Kivech on 2011-05-18
As the title says.

I would like to use DropBox, but I really don't want Nautilus on my system.

I downloaded the source to compile, thinking it would allow me to use a different file browser, but unfortunately it seems they made it dependent on Nautilus.

Is there a way to compile it using a different file browser (Thunar in this case)? And if not, is there an alternative to DropBox out there that works on multiple platforms?

---

### Post by marvin_littlewood on 2011-05-18
Yes it works fine with Thunar and XUbuntu up to 10.10

On my very old Vaio machine, upgrade to Natty (11.04), stops Dropbox from installing - it freezes at 97% on downloading and installing the Dropbox daemon after you have run the initial linux installation.

There are sites that suggest fixes that are easily found on Google but I have decided to wait until the official version works.

Marv

---

### Post by Kivech on 2011-05-18
Oki, thanks mate. I better hold off for a bit also then.

Appreciate the reply. :)

---

### Post by mobilediesel on 2011-05-18
I'm not using the newest Ubuntu but I use Thunar with Dropbox. I have a script called nautilus saved in ~/bin
```
#!/bin/bash
exec thunar ${@/#--no-desktop}
exit 0

```
When you click on the Dropbox icon it'll call that script when nautilus isn't actually installed. There's also a plugin for thunar called [thunar-dropbox]("http://softwarebakery.com/maato/thunar-dropbox.html") that will let you right-click a file to get its public link or gallery link.

---

### Post by Kivech on 2011-05-18
> **mobilediesel said:**
> I'm not using the newest Ubuntu but I use Thunar with Dropbox. I have a script called nautilus saved in ~/bin
```
#!/bin/bash
exec thunar ${@/#--no-desktop}
exit 0

```
When you click on the Dropbox icon it'll call that script when nautilus isn't actually installed. There's also a plugin for thunar called [thunar-dropbox]("http://softwarebakery.com/maato/thunar-dropbox.html") that will let you right-click a file to get its public link or gallery link.

Oh, I'm going to try that one out later for sure. That sounds pretty nifty to me. Thanks for the tip mate.

---

### Post by Kivech on 2011-05-20
@ mobilediesel
Just out of curiosity. What did you do, did you compile the source, ignoring the dependency errors and then afterwards you created the script?

When I run ./configure it obviously comes up with the error that it cannot find Nautilus, but then installing it, all should be ok once you made the script the way you did, right?

I just want to make sure I'm not going to make a mess. :P

---

### Post by mobilediesel on 2011-05-20
> **Kivech said:**
> @ mobilediesel
Just out of curiosity. What did you do, did you compile the source, ignoring the dependency errors and then afterwards you created the script?

When I run ./configure it obviously comes up with the error that it cannot find Nautilus, but then installing it, all should be ok once you made the script the way you did, right?

I just want to make sure I'm not going to make a mess. :P

I used the instructions here: [http://wiki.dropbox.com/TipsAndTricks/TextBasedLinuxInstall](http://wiki.dropbox.com/TipsAndTricks/TextBasedLinuxInstall)
It's a bit less simple than running the .deb file but it doesn't complain about nautilus not being there or force you to install it.

---

### Post by Jacobonbuntu on 2011-05-21
Huh? A few days ago I installed Dropbox on 2 computers, the "easy way"  (.deb package from their site; Xubuntu 11.04, Thunar) no problem whatsoever. Did you try the straightforward install from the .deb package?

---

### Post by Kivech on 2011-05-21
Well, the problem is that it depends upon Nautilus, which is the Gnome file browser. That one in turn depends on Gnome, so it will install all kinds of Gnome environment stuff with it.

I don't want to do that, because I want my xfce environment to stay as 'clean' as possible.

To give you another example: aptoncd is very handy package that allows you to backup your whole system on a disk and automatically install your system the way you installed it.
Unfortunately though, it is dependent on K3b, the KDE disk burning software. I didn't know that, installed it without checking what it would install, and next thing I know, I had half the KDE environment on my PC. :shock:

For me, keeping xfce clean is fundamental (though Xubuntu already puts some Gnome stuff on there that I'd rather not have on my system) since I run many servers on my PC that I need. So anything that adds to the load is too much.

It would also be such a nice feature if they were to separate software for specific desktop environments. Just so you know that if you want to use some program, it will install the desktop environment upon which it depends. But that is a different story.

Anyway, long answer to a short question. :P

So I really want to get DropBox working with Thunar, and not with Nautilus.

Clicking the .deb package clearly gives the message:
> Nautilus Dropbox is an extension that integrates the Dropbox web service with your GNOME Desktop.
So you might want to check what Gnome packages you have on your system now, as a result of installing it in this fashion.

---

### Post by Jacobonbuntu on 2011-05-21
> **Kivech said:**
> Well, the problem is that it depends upon Nautilus, which is the Gnome file browser. That one in turn depends on Gnome, so it will install all kinds of Gnome environment stuff with it.

I don't want to do that, because I want my xfce environment to stay as 'clean' as possible.

To give you another example: aptoncd is very handy package that allows you to backup your whole system on a disk and automatically install your system the way you installed it.
Unfortunately though, it is dependent on K3b, the KDE disk burning software. I didn't know that, installed it without checking what it would install, and next thing I know, I had half the KDE environment on my PC. :shock:

For me, keeping xfce clean is fundamental (though Xubuntu already puts some Gnome stuff on there that I'd rather not have on my system) since I run many servers on my PC that I need. So anything that adds to the load is too much.

It would also be such a nice feature if they were to separate software for specific desktop environments. Just so you know that if you want to use some program, it will install the desktop environment upon which it depends. But that is a different story.

Anyway, long answer to a short question. :P

So I really want to get DropBox working with Thunar, and not with Nautilus.

Clicking the .deb package clearly gives the message:

So you might want to check what Gnome packages you have on your system now, as a result of installing it in this fashion.

You are abslutely right.....
when I click on the Dropbox- icon in my panel, a Nautilus window pops up instead of the usual Thunar.... I didn 't notice!

---

### Post by Jacobonbuntu on 2011-05-22
........but, after removing Nautilus, the script Mobilediesel mentioned works perfectly in Thunar.

---

### Post by Kivech on 2011-05-23
> **Jacobonbuntu said:**
> ........but, after removing Nautilus, the script Mobilediesel mentioned works perfectly in Thunar.

Interesting... Thanks for letting us know.

Meanwhile I am still browsing around to find a 'clean' xfce environment without any gnome stuff in there. Seems to be more challenging than I thought. :P

If I get this working the way I'd like to, I'll make sure to post my results here.

---

### Post by linuxinstalledfromhdd on 2011-05-23
Crunchbang Statler XFCE.  Goodluck. It's pure debian too, which you might like as well.

---

