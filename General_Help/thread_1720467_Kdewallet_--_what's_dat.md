---
title: "Kdewallet -- what's dat?"
date: 2011-04-03
forum: General Help
---

### Post by Rocket J Squirrel on 2011-04-03
I've installed a new app, an offline blogging composition tool called "blogilo".

When I launch it, I get a dialog box that says, "The application 'Blogilo' has requested to open the wallet 'kdewallet'. Please enter the password for this wallet below."

I don't recall ever setting up a kde wallet, and none of my usual passwords work. 

The app seems to work fine after clicking "cancel" to get out of that password dialog, but I'm wondering what kdewallet is, and why something like blogilo would want to access it.

---

### Post by Frogs Hair on 2011-04-03
The application you installed is  KDE . See the link for Kdewallet. [http://utils.kde.org/projects/kwalletmanager/](http://utils.kde.org/projects/kwalletmanager/)

---

### Post by SeijiSensei on 2011-04-03
The wallet in KDE stores the passwords various applications require in a single encrypted location.  The most common situation where the wallet appears is when using wifi on KDE.  If you put your wifi password in the wallet, then the first time you connect, you'll get the wallet prompt.  Entering the master password lets the wifi manager open the wallet and use the stored wifi password.

I'm guessing you're not running KDE as your desktop environment.

It looks like the wallet manager is not a dependency of [blogilo]("http://packages.ubuntu.com/km/lucid/blogilo"), though if the application is popping up the wallet manager dialog, it probably should be.  [kwalletmanager]("http://packages.ubuntu.com/km/lucid/kwalletmanager") is part of the [kdeutils]("http://packages.ubuntu.com/km/lucid/kdeutils") package which doesn't appear in the list of dependencies for blogilo.

Does this application use a password?  I've never used blogilo.

---

### Post by Rocket J Squirrel on 2011-04-03
Thanks.

The app does not use a password, although it stores the requisite passwords and usernames to post articles to one's blog. The same ones that are used to sign in to the blogs for online composition. 

It's true, I am not using KDE as my desktop environment, am using the Unity netbook desktop.

---

### Post by techunit on 2011-04-03
you can leave the password field as blank.

---

