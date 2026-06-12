---
title: "Gmail notifier"
date: 2006-03-26
forum: General Help
---

### Post by chocolatetoothpaste on 2006-03-26
I hope I am not lightyears behind with this, but I just wanted to let everyone know that gmail has a notifier app, and there is a linux version in the repos!  It is soooooooo  good to see major corps supporting linux!  Lets keep pushing guys!  Linux will very soon become a major entity among desktops, I predict.  And would we ever love that!  Could you imagine, linux drivers with EVERY digital camera/camcorder?  PDA's with sync software for linux or windows?  PDA's themselves with linux pre-installed.  I love it.  My Dell Axim 30 crashes too much.  It is as bad as my family's XP box.  BTW, does anyone know of any linux projects for the Axim30?  Anyway, it makes me feel good that the linux community is commanding a lot of attention.

edit:
My bad!  Hehe, even if google didn't write, it is still cool that stuff keeps getting written!  Keep up the good work!

---

### Post by fuxoft on 2006-03-26
What do you mean? If you are referring to "gmail-notify" package, it was not created by Google.

---

### Post by chocolatetoothpaste on 2006-03-26
Yeah I am talking about gmail-notify.  I didn't know google didn't make it.  Who did?

---

### Post by rfruth on 2006-03-26
I use the google toolbar which has a gmail envelope on it [http://www.google.com/tools/firefox/toolbar/index.html]("http://www.google.com/tools/firefox/toolbar/index.html")

---

### Post by engla on 2006-03-26
mailnotify is another package in the repositories that can do this.. it lives in the systray and you can set it up to check multiple different mail accounts with imap, pop or gmail..

---

### Post by hellmet on 2006-05-08
I get wierd error while installation...

[B]Unpacking replacement gmail-notify ...
dpkg: dependency problems prevent configuration of gmail-notify:
 gmail-notify depends on python2.3; however:
  Package python2.3 is not installed.
 gmail-notify depends on python (<< 2.4); however:
  Version of python on system is 2.4.2-0ubuntu2.
 gmail-notify depends on python2.3-gtk2 (>= 2.2.0); however:
  Package python2.3-gtk2 is not installed.
dpkg: error processing gmail-notify (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gmail-notify
[/B]

I have python 2.4 installed
any help??

---

### Post by nolongerlivecd on 2006-05-08
Hey, if you want Linux on a handheld, check out the next Palm OS

---

### Post by peterquistgard on 2008-02-06
You can use Gmail Notifier to check multiple gmail accounts. Heres what I did. Im sure there are more elegant ways, but this one works. You can simply start multiple instances of notifier and change the configuration of each one to suit your accounts. This takes time though. If you want to automate the process you can...

1. Make a copy of the ~/.notifier.conf file for each gmail account, and add appropriate info. Name them something else like ".notifier1.conf", ".notifier2.conf" or whatever.

2. Use a script to replace ~/.notifier.conf with each file you made, and launch an instance of notifier for each one. You will probably need to include some delay here.

3. (Optional) You can create a file called ~/.profile and add the name of your script. I found that the easiest way to get a script to run every time I log on.


My script looks like this (Sorry if its bad code. This was my first script.)

#!/bin/sh
killall -g gmail-notify
cp /home/user/.Gmailconf1 /home/user/.notifier.conf
gmail-notify & 
sleep 10
cp /home/user/.Gmailconf2 /home/user/.notifier.conf
gmail-notify &
sleep 10
cp /home/user/.GmailconfDefault /home/user/.notifier.conf
exit 0

---

