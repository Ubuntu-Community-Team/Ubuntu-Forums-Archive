---
title: "Accidently deleted weatherbug"
date: 2011-11-24
forum: General Help
---

### Post by waltwin on 2011-11-24
I had weatherbug working really well. For some unknown reason two weatherbug widgets were displayed on my panel so I deleted one. "Good bye weatherbug".

The program is still installed but I can't activate it. I tried to reinstall the program but my system tells me that it is installed. I am using ubuntu 10.10. Any assistance would be greatly appreciated.

waltwin

---

### Post by MG&amp;TL on 2011-11-24
Type into the terminal:

```
sudo apt-get remove --purge weatherbug && sudo apt-get install weatherbug
```

This should purge any config files and put back to normal.

---

### Post by waltwin on 2011-11-24
> **MG&TL said:**
> Type into the terminal:

```
sudo apt-get remove --purge weatherbug && sudo apt-get install weatherbug
```

This should purge any config files and put back to normal.
That didn't go well. Your suggestion did delete all traces of weatherbug from my system. If that was your intent, shame on you or shame on me, not sure which. This is the very first time I have gotten really bad advise when I have asked a question on this circuit. But you have a Happy Thanksgiving any way.

---

### Post by MG&amp;TL on 2011-11-25
My apologies if something did not go well, that is not my intent.

I shall explain the commands bit by bit, then you can see why I suggested them.

sudo-makes you root, so you access restricted places to install things

apt-get remove -removes a package

--purge -removes a package and kills all config along with it. (I wanted to get it back to a default install of weatherbug with them open, not closed.

weatherbug -the package in question

&& -and-connective in the terminal

sudo -as above

apt-get install -installs a package

weatherbug-installing package.


Now what problem occurred with that, and I might be able to help.

I fail to see any problem with my advice. But if you disagree, maybe you can PM about it.

And happy thanksgiving too. :)

---

### Post by stinkeye on 2011-11-25
> **waltwin said:**
> That didn't go well. Your suggestion did delete all traces of weatherbug from my system. If that was your intent, shame on you or shame on me, not sure which. This is the very first time I have gotten really bad advise when I have asked a question on this circuit. But you have a Happy Thanksgiving any way.
See your own [**_[COLOR="DarkRed"]thread[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1811396").
Where you downloaded a deb file to install.It's not in the repos.
The config file is at **~/.weatherbug** and deleting that folder should set it back to defaults.

All MG&TL did was uninstall weatherbug and remove the config @ **~/.weatherbug**.
Reinstall the deb.

and a quote from the same thread
> Disclosure: I happen work closely with the parent company and would desperately love to see a community project around the API. Evidence of this can be provided to any interested developers via a PM to my user account. Would be in appropriate to post my email, etc, to an open thread.

 Also, the Java app "sort of" works with 11.04, although not officially. Reason being it runs really poorly and it sends the CPU into fits with every mouse click.

---

### Post by MG&amp;TL on 2011-11-25
My apologies, I assumed it was in the repos when you said you had tried to reinstall. Sorry. :(

---

