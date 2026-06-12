---
title: "Problem installing latest version of libqtcore4"
date: 2011-12-03
forum: General Help
---

### Post by Jammanuser on 2011-12-03
Hello.
Ok, so first off, I was trying to get CoolReader3 installed and working, but kept getting complaints about a dependency (i.e. libqtcore4) package version not being >= the version the package "cr3" (CoolReader) needs. So, I went to the terminal of course, and ran:

```

sudo apt-get install libqtcore4

```

but was informed the latest version (4.4.6.2, or some such version) was already installed. However, I knew it was lying seeing as the Package Manager was telling me that cr3 depends on a version like "4.4.7.0" or greater. :D So, next I went hunting manually for the package by Googling it, and was able to find the latest on their website, and downloaded it manually. I next tried to install it through the Package Manager, but failed to because of some error I can't remember. So I went and installed it manually through dpkg in the Terminal, which I guess replaced the older version on there. So now that caused a whole host of problems (even though I finally managed to install cr3 through dpkg), because I went to Synaptic (after finding out CoolReader3, and also Qt Creator wasn't opening), trying to fix the problem there, and learned that several different Qt modules depend on the older version of libqtcore4 (which I replaced with the newer version). 

So now I'm trying to figure out how to remove the new version of libqtcore4, install the old version which was on there, and put everything back the way it was before (since CoolReader3 isn't working anyway, and now a bunch of other applications aren't working). However, attempting to remove it first with Synaptic, and then with dpkg, **I have learned I cannot without first removing all of the applications which depend on the module** (which I do NOT want to do). So now I'm at a loss of what to do now...

Any ideas anyone? :confused:

Thanks in advance.

EDIT: And note that I'm now running the 10.04 version of Ubuntu.

---

### Post by oldtimer7777 on 2011-12-03
This is why I think Remastersys backup is so cool.   Everyone should have a backup of their entire system if they are going to be fooling around with broken pipes and stuff like that. 

Let's wait this out and see if anyone has a solution. 

> **Jammanuser said:**
> Hello.
Ok, so first off, I was trying to get CoolReader3 installed and working, but kept getting complaints about a dependency (i.e. libqtcore4) package version not being >= the version the package "cr3" (CoolReader) needs. So, I went to the terminal of course, and ran:

```

sudo apt-get install libqtcore4

```but was informed the latest version (4.4.6.2, or some such version) was already installed. However, I knew it was lying seeing as the Package Manager was telling me that cr3 depends on a version like "4.4.7.0" or greater. :D So, next I went hunting manually for the package by Googling it, and was able to find the latest on their website, and downloaded it manually. I next tried to install it through the Package Manager, but failed to because of some error I can't remember. So I went and installed it manually through dpkg in the Terminal, which I guess replaced the older version on there. So now that caused a whole host of problems (even though I finally managed to install cr3 through dpkg), because I went to Synaptic (after finding out CoolReader3, and also Qt Creator wasn't opening), trying to fix the problem there, and learned that several different Qt modules depend on the older version of libqtcore4 (which I replaced with the newer version). 

So now I'm trying to figure out how to remove the new version of libqtcore4, install the old version which was on there, and put everything back the way it was before (since CoolReader3 isn't working anyway, and now a bunch of other applications aren't working). However, attempting to remove it first with Synaptic, and then with dpkg, **I have learned I cannot without first removing all of the applications which depend on the module** (which I do NOT want to do). So now I'm at a loss of what to do now...

Any ideas anyone? :confused:

Thanks in advance.

EDIT: And note that I'm now running the 10.04 version of Ubuntu.

---

### Post by Jammanuser on 2011-12-03
> **oldtimer7777 said:**
> This is why I think Remastersys backup is so cool.   Everyone should have a backup of their entire system if they are going to be fooling around with broken pipes and stuff like that. 

Let's wait this out and see if anyone has a solution.
What is "Remastersys backup"??

---

### Post by oldtimer7777 on 2011-12-03
> **Jammanuser said:**
> What is "Remastersys backup"??

[https://debianhelp.wordpress.com/2011/10/12/relinux-a-new-fork-of-remastersys/](https://debianhelp.wordpress.com/2011/10/12/relinux-a-new-fork-of-remastersys/)

I always use a backup of my entire fully installed system before I start playing around with Ubuntu.  It is no fun having to always reinstall everything over and over and over again..   15 minutes and you are back in business from a live flash drive with a custom.iso of your OS on it to install from.

---

### Post by Jammanuser on 2011-12-04
Ok, nevermind, I guess.
I finally broke down and allowed Synaptic to uninstall all of the applications that depended on the "libqtcore4" module, after first writing the names of the packages down. And then I reinstalled them all, except for cr3, since that requires a later version of libqtcore4, ad is what caused the whole problem to begin with.

So its all good now, except I still don't have any application installed to read .epub files, which is what I was originally trying to install CoolReader3 for, but oh well...:(

I found another program called "FBReader" in the Ubuntu Software Center which can supposedly read .epub files to, so I'm going to go ahead and try installing that, which will hopefully work.

Cheers. :popcorn:

-Jam Man

:guitar:

---

