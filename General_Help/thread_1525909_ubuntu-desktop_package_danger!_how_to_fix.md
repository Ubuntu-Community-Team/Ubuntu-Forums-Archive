---
title: "ubuntu-desktop package danger! how to fix?"
date: 2010-07-07
forum: General Help
---

### Post by mavicus on 2010-07-07
Currently using Ubuntu 9.10
I've been using ubuntu since somewhere around 2005 and love it.
I have learned a lot. One of the things I have learned is: DON'T UNINSTALL "ubuntu-desktop" from the package manager. Any time I remove packages, I always check to make sure it isn't going to uninstall "ubuntu-desktop", because I know what the results can look like.

Last night I installed and then uninstalled several things at once from the command line with apt-get and apparently one of them triggered the uninstall of "ubuntu-desktop". I believe it was a pulseaudio package. THERE WAS NO WARNING and within seconds my entire OS was botched. How WOULD I recover from this? (I have already reinstalled from scratch), but I would seriously like to know a couple things:

1. ***How would I have recovered from this?*** I did manage to install and reinstall "ubuntu-desktop" but it did not get me back to my original state. In particular, my sound didn't work except for the startup sounds, and a few other things. (Not important what they are at this point I suppose)

2. This seems like it should be a pretty big issue. I mean no average user is NORMALLY going to choose to remove this package. It is so seamless, automatic, suprising, and devastating, especially from the command line. ***Is there a way to protect against this in the future?***

Thanks to anyone who has experience or answers to share. It's so terrible that I fear uninstalling ANYTHING. (And have for a while. Apparently with good reason, because it finally ate me.):popcorn:

---

### Post by philinux on 2010-07-07
Must have changed then.

```
sudo apt-get purge ubuntu-desktop
[sudo] password for philcb: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  ubuntu-desktop*
0 upgraded, 0 newly installed, **1 to remove** and 0 not upgraded.
After this operation, 61.4kB disk space will be freed.
Do you want to continue [Y/n]? n

```

I think you did more than you think. Try looking though your terminal log.
```
cat ~/.bash_history
```

---

### Post by sandyd on 2010-07-07
> **mavicus said:**
> Currently using Ubuntu 9.10
I've been using ubuntu since somewhere around 2005 and love it.
I have learned a lot. One of the things I have learned is: DON'T UNINSTALL "ubuntu-desktop" from the package manager. Any time I remove packages, I always check to make sure it isn't going to uninstall "ubuntu-desktop", because I know what the results can look like.

Last night I installed and then uninstalled several things at once from the command line with apt-get and apparently one of them triggered the uninstall of "ubuntu-desktop". I believe it was a pulseaudio package. THERE WAS NO WARNING and within seconds my entire OS was botched. How WOULD I recover from this? (I have already reinstalled from scratch), but I would seriously like to know a couple things:

1. ***How would I have recovered from this?*** I did manage to install and reinstall "ubuntu-desktop" but it did not get me back to my original state. In particular, my sound didn't work except for the startup sounds, and a few other things. (Not important what they are at this point I suppose)

2. This seems like it should be a pretty big issue. I mean no average user is NORMALLY going to choose to remove this package. It is so seamless, automatic, suprising, and devastating, especially from the command line. ***Is there a way to protect against this in the future?***

Thanks to anyone who has experience or answers to share. It's so terrible that I fear uninstalling ANYTHING. (And have for a while. Apparently with good reason, because it finally ate me.):popcorn:

1. you removed pulseaudio, so you will have to reconfigure the sound 2. im on my cell, so I cant redirect you to the thread but if you look in my posts (click on my username -> find posts) youll find a thread called "protecting packages). discussion is still going on.

---

### Post by SlugSlug on 2010-07-07
uninstalling pulse does state it will uninstall ubuntu-desktop -- i need to do this on each install..

however the desktop remains in perfect working order.

---

### Post by Strongman332 on 2010-07-07
to tell you the truth Ubuntu-desktop is only there to make it easier to install the gnome environment, after install you can actually remove this component as i have done. however what you have done is uninstalled something that Ubuntu-desktop depended on. this does not always mean that you have done some thing that is completely catastrophic to your system. and to fix it simply re install Ubuntu-desktop. warning though this may remove some of your newly installed programs. specifically the one that uninstalled Ubuntu desktop. then go threw one buy one and reinstall everything and check to see which one removes Ubuntu-desktop. and keep in mind that both synaptic, and the command line will warn you when a package will be removed, you just have to do a bit of reading.

---

### Post by mavicus on 2010-07-07
Yeah, I'm sure I can probably say without looking at the log that I typed yes to that prompt. *Therefore I recant the part about "no warning".* (even though the list was huge and it was probably scrolled off the top of the screen or buried in a wall of text, I *should* have been a good user and looked at all of it)

But this is kind of like removing the liver from the total ubuntu experience when it happens. I personally think it shouldn't be a click and boom experience. My cousin for example has done this as well from within synaptic, he doesn't even understand that package removals can remove other packages etc. and I present the argument that he shouldn't *need* to know this with Ubuntu. Otherwise, there's no need to give him Ubuntu. We are trying to compete with that OS that's made of glass right?
Can't expect him to go from vista to slackware exactly.

Is there any thing I can to do lock myself out of uninstalling THIS particular package?

Is there a fast way to recover besides from backup?

Edit: (And thanks for the replies, you all replied too fast for me.)

---

