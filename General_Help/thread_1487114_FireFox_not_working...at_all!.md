---
title: "FireFox not working...at all!"
date: 2010-05-18
forum: General Help
---

### Post by ace0022 on 2010-05-18
Hi all, newbie here.  I've been working flawlesly with ubuntu for a while now and today clicked on firefox and nothing.  You see it trying to launch and it won't.  Tried to do the firefox -safe-mode and nothing happens.

Any help would be great!


Thanks!

---

### Post by doas777 on 2010-05-18
it may help to get an error message. open a terminal and type 'firefox'. then make post back of any errors.


here are some more generic approaches to the problem. removing potentially bad config files, and if needed reinstalling the app.

try running this command:
```

mv ~/.mozilla ~/.mozilla.broken

```
then relaunch firefox. it will back up your firefox config, then remove it. when FF opens again, it will recreate ~/.mozilla and it's contents

if that doesn't work, you can try reinstalling FF:
```

sudo apt-get install firefox --reinstall

```
this just reinstalls FF.

and if that doesn't work, perhaps this will:
```

sudo apt-get purge firefox
sudo apt-get install firefox

```
this will purge all files related to FF, before trying to install it again, in case there is a corrupt system config file. 

good luck

---

### Post by r_s on 2010-05-18
why don't you install firefox directly from the mozilla website, it will contain the latest updates from mozilla.

---

### Post by ace0022 on 2010-05-18
Oh man, that was quick and awesome!  Thanks so much [doas777]("http://ubuntuforums.org/member.php?u=451394")!  This one helped right off the bat!

mv ~/.mozilla ~/.mozilla.broken

I'll keep this one with my notes!

---

### Post by lovinglinux on 2010-05-18
> **ace0022 said:**
> Oh man, that was quick and awesome!  Thanks so much [doas777]("http://ubuntuforums.org/member.php?u=451394")!  This one helped right off the bat!

mv ~/.mozilla ~/.mozilla.broken

I'll keep this one with my notes!

I prefer and recommend trying to pinpoint the problem first, otherwise you will have to restore bookmarks, extensions, passwords, settings and so on.

See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by ace0022 on 2010-05-19
Thanks so much for the info.  I'm starting to learn my way around here with you guys help.  Thanks for the reply [lovinglinux]("http://ubuntuforums.org/member.php?u=649167").  I'm starting to really learn this ubuntu world, so any bit of info will help.  I'll look at the thread you posted and l'm pretty sure I will learn something.

Thanks again!

---

