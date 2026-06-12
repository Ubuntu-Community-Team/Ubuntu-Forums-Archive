---
title: "Software Sources Problem"
date: 2009-08-11
forum: General Help
---

### Post by ssdt on 2009-08-11
I am facing again a rather troublesome software sources problem. I installed or at least tried because I couldn't succeed on installing Microblog purple, the Pidgin plugin. But I was not able to. I tried to install their Software sources and seem to now mess it up. When I click on Restore Default on both the Authentication and Third-Party Software Tab, they do not seem to change. Currently I have only:

WineHQ for 9.04
ppa.launchpad.net/pidgin-developers/ppa/ubuntu-jaunty
ppa.launchpad.net/ubuntuone/beta/ubuntu jaunty main
ppa.launchpad.net/ubuntuone/beta/ubuntu jaunty main (Source Code)
[http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable main

Please help me and tell me any other information that I might need to provide

---

### Post by quixote on 2009-08-12
I'm not sure from your description what the problem with your Sources is.  I don't see a "Restore Default".  And I think "Revert" just reverts to the last saved set, which doesn't help, in your case.  Authentication doesn't affect the list of repositories.

If you go to the Third Party tab, how many entries are there?  How many of them are selected?  They won't be active unless their tick box is selected.  (Sorry if I'm telling you things you already know.  The problem is, I'm not sure where you're at in this :) )

I'm not sure why you're using the sources you have listed for microblog-purple.  The format is also wrong, the way you have it because they need "deb" at the start of the line.

[This site]("http://webupd8.blogspot.com/2009/03/twitter-in-pidgin-plugin.html"), for instance, has these instructions, which seem to make sense.  I haven't tried them myself.

> For Ubuntu Linux, add these repositories:
deb [http://ppa.launchpad.net/sugree/ppa/ubuntu](http://ppa.launchpad.net/sugree/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/sugree/ppa/ubuntu](http://ppa.launchpad.net/sugree/ppa/ubuntu) jaunty main

of course, depending on your distro. Then open a terminal and type this in order to import the key:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0CF459B8DF37ED8B
```
Then you would need to reload the repositories, either in the Software Sources or Synaptic window, or, if you're in a terminal:
```
sudo apt-get update
```
And then:
```
sudo apt-get install pidgin-microblog
```

---

### Post by michy99 on 2009-08-12
Post your sources.list file so we can see if there are any problems with it.```
cat /etc/apt/sources.list
```

---

### Post by ssdt on 2009-08-13
Thank you. I found the answer.

---

### Post by quixote on 2009-08-13
How about telling us what the answer was, so that other people can be helped to if they need the info on this thread?

---

### Post by ssdt on 2009-08-16
Um, really I didn't even understand what had happened but it was fixed.

---

