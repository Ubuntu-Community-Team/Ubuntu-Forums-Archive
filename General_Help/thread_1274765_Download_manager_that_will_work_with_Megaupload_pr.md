---
title: "Download manager that will work with Megaupload premium account"
date: 2009-09-24
forum: General Help
---

### Post by Zatara214 on 2009-09-24
One of the two things that is keeping me from switching to Ubuntu from Windows full time is a proper download manager (the other is Guitar Pro, which is offset by Tuxguitar).

I've tried everything from Gwget to DownThemAll to just about every manager that's compatible with FlashGot.  I cannot find a manager that can integrate with Firefox that will keep my Megaupload premium account stored in the settings.

The issue at hand is that when I download several large files in a queue (I'm following Umineko, can you blame me?), the first download completes, and the rest end up as html files with the coding for the megaupload page in them.

Internet Download Manager, under Windows, does not have a feature for pluging in usernames and passwords.  However, it has worked for me with MU for at least three years now.  I need an Ubuntu equivalent that will integrate with Firefox (putting in links manually for all of those files would just be too much).

---

### Post by michy99 on 2009-09-24
Have you tried jDownloader?

[http://jdownloader.org/](http://jdownloader.org/)

---

### Post by kingchipo on 2009-09-24
um? im not exactly sure but this is how i worked around with my rapidshare premium account..


Download kget.. its a kde program but it will work with gnome althowe when you close it it crashes o.0

sudo apt-get install kget

Then 

Sudo apt-get install konqueror

Now kget remembers passwords that were stored in konquerors password wallet so log on to your megaupload account via konqueror and save your password.

Set flashgot to use kget as download manager. and you should have a good working dl manager that automaticly remembers your megaupload account so you can download multiple links instantly

also you do not have to use konqueror to download the links you can flashgot selection from any browser you wish

---

### Post by Zatara214 on 2009-09-25
I have tried jdownloader, and I got the same result out of it, although it did work for a few more downloads than usual (maybe three or four).

I'll try Kget with Konqueror and report back.

---

### Post by Zatara214 on 2009-09-25
Or not.  Apparently in order to install Kget, I need to uninstall my Nvidia driver.  Weird dependancies.  That just doesn't work for me.

---

### Post by ndxtg on 2010-11-30
Came accross this problem today.

I found [http://mundogeek.net/megaupload-dl/](http://mundogeek.net/megaupload-dl/) but looks like the author didnt update since last year.

Then found: [http://www.minasolution.com/tools/codepad/ubuntu-megaupload-on-command-line-downloader-1291156718.html](http://www.minasolution.com/tools/codepad/ubuntu-megaupload-on-command-line-downloader-1291156718.html)

which works perfectly on command line. Cheers.:popcorn:

p/s: it will ask your premium username and password on first use and it saves somewhere in ~./home I guess... need to delete that file if you want to change username/password (search for megaupload-dl.ini in your home directory)

---

