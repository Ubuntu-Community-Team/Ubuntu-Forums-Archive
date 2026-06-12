---
title: "Removing Overlay-Scrollbars"
date: 2011-06-01
forum: General Help
---

### Post by shark.basketball on 2011-06-01
So many of us Ubuntu (and / or variant) users have grown to really like Ubuntu. But many of us are simply unimpressed by Unity, and by the use of overlay-scrollbars. Personally, I kind of like them, they do technically do what they were meant to, and that is to give more usable screen area. But, that being said, I only like them when using a scrollwheel or a trackpad with a scrolling function. Still, I, and many others, would like to remove these altogether. So how do we do that? Well, it's extremely simple. But if you dont really want to go and remove a package by hand, if you aren't comfortable, this can be a daunting task. So what I did is make a simple shell script that firstly removes the required package, and then logs you out to fully apply the settings. Below I'll post the script itself if you don't want to download the script file, which I'll also give a link.

*Note: This script uses the sudo command, so this must be available to you. Just put in your password when necessary. Also, it'll ask you to remove two packages, these are liboverlay-scrollbar and overlay-scrollbar. You can say n for no, to not remove the packages, but that's the whole point, so you need to say y for yes. Also, it'll automatically log you off, so be sure to save any open documents blah blah blah you know the story.



```
#!/bin/bash
sudo apt-get remove overlay-scrollbar
gnome-session-save --kill --silent
```

File download:

[http://www.box.net/shared/oife8eq9ax]("http://www.box.net/shared/oife8eq9ax")

Please comment if you need any help, or the download doesn't work. Good luck!

---

### Post by shark.basketball on 2011-06-01
Please note: I have noticed that some overlay scrollbars still reappear. I'm working on an update.

---

### Post by shark.basketball on 2011-06-01
Ok, this here should work.

```
#!/bin/bash
sudo echo "export LIBOVERLAY_SCROLLBAR=0" > /etc/X11/Xsession.d/80overlayscrollbars
gnome-session-save --kill --silent

```


And the download link:
[http://www.box.net/shared/umc23bxpqr]("http://www.box.net/shared/umc23bxpqr")

Thanks!

---

