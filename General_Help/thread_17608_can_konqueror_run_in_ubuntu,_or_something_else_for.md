---
title: "can konqueror run in ubuntu, or something else for ftp"
date: 2005-03-01
forum: General Help
---

### Post by beerorkid on 2005-03-01
First I am falling in love with ubuntu.
I have learned all of my linux stuff on SuSE 9.1 & 9.2.  One of the things I rely on suse having is the konqueror web browsers ability to act like an FTP program.

In konqueror you can split the view into two seperate instances.  I log into my ftp/web server on one side, and the other side is my linux file browser (home).

The cool thing is that I can delete whole folders or move them around with great ease.  No recursive deletes or other typical issues associated with ftp programs.
I create my web stuff in winxp and reboot to SuSE to mess with the ftp stuff with konqueror because it rocks for that purpose.

konqueror is a KDE app and is imbedded in the KDE package.

Can konqueror run in ubuntu or can anybody suggest another package / program that will have these functions?

This is the only thing keeping me from switching from SuSE to ubuntu at work, and home.  I hated gnome for a little bit, but have grown to like it.

---

### Post by beerorkid on 2005-03-01
maybe, I found this page and it shows that knoquror is an universe package.
[http://higgs.djpig.de/ubuntu/www/hoary/web/konqueror](http://higgs.djpig.de/ubuntu/www/hoary/web/konqueror)

it seems like I would have to install the kde stuff to get it.  Can I install the kde stuff and will this work?

---

### Post by landotter on 2005-03-01
[QUOTE=beerorkid]maybe, I found this page and it shows that knoquror is an universe package.
[http://higgs.djpig.de/ubuntu/www/hoary/web/konqueror](http://higgs.djpig.de/ubuntu/www/hoary/web/konqueror)

it seems like I would have to install the kde stuff to get it.  Can I install the kde stuff and will this work?[/QUOTE]
 installing konqueror will only install the bare minimum of KDE to make it work.

I do think that for a QT app, Krusader is a better ftp client, but of course it's all personal preference.

Gftp is the defacto "standard" graphical gtk toolkit ftp client these days. Available via Synaptic. Dead simple to learn.

Nautilus is capable of ftp as well, as I recently learned on these boards. It's good for a site or two that you access often as it doesn't have a "site manager". Open up a nautilus window, then "file/connect to server". It'll put an icon on your desktop for easy access to the ftp site. Very handy. :D

---

### Post by beerorkid on 2005-03-01
frickin sweet....
Thanks so much for the reply.  I have the warty disk in my work pc and am ready to reboot, would'nt mind the horay but this will do.

I was reading up on this issue while awaiting a response and learned about the natulus thing.  Is that the same as what my home directory opens up in?  I did not see a place to type file locations.  I will look harder next time.

Also I read on [www.madpenguin.com](www.madpenguin.com) that there is an update thing like the synaptic manager, is that only available with horay.  I am a little confused on the horay thing.

Thanks again.

---

### Post by landotter on 2005-03-01
[QUOTE=beerorkid]frickin sweet....

I was reading up on this issue while awaiting a response and learned about the natulus thing. Is that the same as what my home directory opens up in? I did not see a place to type file locations. I will look harder next time.
[/QUOTE]

the default Nautilus view, this is your defaut file manager's strange name btw ;), is without an adress bar or navigation buttons. You can change it to look more like a regular browser in the preferences, or just right click/browse folder to get a "browser".

to access the ftp server you'll get a dialog box when you do "file/connect to server" and it will allow you to add the address and username/password if needed.

---

### Post by beerorkid on 2005-03-02
I have it working, konqueror that is.
I have an issue with the no root thing, so I have done the "sudo passwd root" thing.

I just su and then type konqueror
and it opens Konq    horray!!!!!!

I am ububtu for good now.

It kind of comes down to everybody in my place of work has a diferent distro that they use and I will be a little different.

Thanks for the  suggestions

---

### Post by lordofkhemenu on 2005-03-02
[QUOTE=landotter]installing konqueror will only install the bare minimum of KDE to make it work.

I do think that for a QT app, Krusader is a better ftp client, but of course it's all personal preference.

Gftp is the defacto "standard" graphical gtk toolkit ftp client these days. Available via Synaptic. Dead simple to learn.

Nautilus is capable of ftp as well, as I recently learned on these boards. It's good for a site or two that you access often as it doesn't have a "site manager". Open up a nautilus window, then "file/connect to server". It'll put an icon on your desktop for easy access to the ftp site. Very handy. :D[/QUOTE]
Yup, this is exactly what I do, as well. Very handy, that drag n drop thing...;)

---

