---
title: "Firefox Probs"
date: 2006-04-28
forum: General Help
---

### Post by Rick Myers on 2006-04-28
I've checked through the forum here and elsewhere. I have not been able to solve these issues;

1) Mailto links do not open any email client. I'm using Thunderbird 1.5. I've done "System Setting>User Account>Email Client>Use Different Email Client:mozilla-thunderbird". Still NG.

2) Firefox>Help>Check for update... is gray (not enabled). Consequently I can't check for updates. Any thoughts?

Same problem in Gnome too.


Help would be appreciated.
Rick

---

### Post by awakatanka on 2006-04-28
1 i dunno

2. Its because (k)ubuntu devs has made a version that is a little different from original, but if i'm right if you start it wit root you can update it.

---

### Post by dejitarob on 2006-04-28
Awakatanka is correct. If you open up the command line and type 'sudo firefox', check for updates, restart later, exit then 'sudo firefox' again, it will work.

I found [this thread]("http://ubuntuforums.org/showthread.php?t=22333&page=1&pp=10") on the forums, also some more fixes [via google]("http://www.google.com/search?hl=en&q=linux%20firefox%20mailto"). Btw, I found these by searching for 'linux firefox mailto'.

---

### Post by gingermark on 2006-04-28
As a general rule you shouldn't use sudo for graphical applications. Do ```
kdesu firefox
``` instead.

---

### Post by Ensnared on 2006-04-28
For #1, Firefox has a nasty habit of using the Gnome settings for determining your default email-client, even if you're using KDE. It's stupid, but it's true.

So, if you have Gnome installed (which I guess you do), first close Firefox, then run the following command:```
gnome-default-applications-properties
``` and configure thunderbird under the "Mail Reader" tab (it's probably set to Evolution as default, and if you don't have that installed it explains why nothing happens when you click a mailto-link).

If you don't have "gnome-default-applications-properties" but have Gconf installed, try starting the```
gconf-editor
```...but you may have to install it first:```
apt-get install gconf-editor
```

In the gconf-editor, browse to /desktop/gnome/url-handlers/mailto and change the value for "command" from whatever it says (probably "evolution %s") to "mozilla-thunderbird %s", and close the window.

Note: If you've installed Thunderbird through non-conventional means (e.g. by not using apt/dpkg, which I suspect is the case when you're using version 1.5 since 1.07 is the latest version in the Breezy repositories), you'll have to specify the complete path to to the executable in order to make it work.

---

### Post by Rick Myers on 2006-04-29
[QUOTE=dejitarob]Awakatanka is correct. If you open up the command line and type 'sudo firefox', check for updates, restart later, exit then 'sudo firefox' again, it will work.

I found [this thread]("http://ubuntuforums.org/showthread.php?t=22333&page=1&pp=10") on the forums, also some more fixes [via google]("http://www.google.com/search?hl=en&q=linux%20firefox%20mailto"). Btw, I found these by searching for 'linux firefox mailto'.[/QUOTE]


This resolved the problems. Thanks!!

---

### Post by Chris Tucker on 2006-04-29
I used the wiki, FirefoxNewVersion .. works great, updates work too, without sudo.
I have one problem, which i dont think is because of my alternate install method, but i can not get KDE to use firefox as its default browser, the command being firefox , i have it set in the components dialogs but it just doesnt work, it loads konq! Anyone got any ideas?

---

### Post by Ensnared on 2006-04-29
Some applications may try to execute x-www-browser instead of the one you've specified. If so, you can fix it by doing```
sudo update-alternatives --config x-www-browser
```...and enter the number that represents the firefox executable.

---

### Post by mattack on 2006-06-08
[QUOTE=Ensnared]For #1, Firefox has a nasty habit of using the Gnome settings for determining your default email-client, even if you're using KDE. It's stupid, but it's true.

So, if you have Gnome installed (which I guess you do), first close Firefox, then run the following command:```
gnome-default-applications-properties
``` and configure thunderbird under the "Mail Reader" tab (it's probably set to Evolution as default, and if you don't have that installed it explains why nothing happens when you click a mailto-link).
[/QUOTE]

I'm using KDE (I installed kubuntu-desktop after installing standard ubuntu-desktop). This worked for me except one little annoying caveat, the new compse window in Thunderbird doesn't have focus.
I solved it with the Configure Window Behavior Control Module (right-click on the titlebar of any window and select Configrue Window Behavior). Select Advanced and change the Focus stealing prevention level dropdown menu to "None."

---

