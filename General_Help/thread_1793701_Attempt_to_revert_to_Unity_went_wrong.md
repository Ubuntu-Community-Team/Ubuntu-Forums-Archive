---
title: "Attempt to revert to Unity went wrong"
date: 2011-06-29
forum: General Help
---

### Post by crustydusty on 2011-06-29
So here is the scoop I am posting this from my "other OS".  Today I tried to install the Gnome3 desktop environment to see if I like it.  I stupidly disregarded the warnings that this would destroy my unity desktop (read: By disregarded I mean did not read).  And well when I rebooted I was not very happy,  not because my unity was missing I would have been ok with that.  I will stop rambling now, I rebooted only to find that not only was I not given the option to choose my desktop env. When I logged I was greeted with a not working theme(ie. missing window buttons very basic graphics and the like) and cairo/glx dock not functioning correctly.  Any how I am getting to the question now.  I ran a command in the terminal that was supposed to effectively remove gnome and bring back unity.

```
sudo apt-get remove libgtk-3-common
sudo apt-get install ppa-purge
sudo ppa-purge ppa:gnome3-team/gnome3
sudo apt-get install gnome-panel
```

And that made everything worse now I don't have a panel and the hotkeys for running the terminal and the launcher prompt do nothing. Question=what can I do to get my desktop environment working again? Any and all help will be greatly appreciated.  Thank you in advance for your time.:)

---

