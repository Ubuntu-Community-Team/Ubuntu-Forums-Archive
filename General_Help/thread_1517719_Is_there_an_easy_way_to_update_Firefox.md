---
title: "Is there an easy way to update Firefox?"
date: 2010-06-25
forum: General Help
---

### Post by Vanillalite on 2010-06-25
I've never quite understood why they won't like Firefox just update on it's own. Instead it appears all of the FF updates always have to come through the update manager. 3.6.4 has been out since Tuesday and while I can go to the FF website and grab the tar of the new version I'd rather you know just upgrade my existing version like I've already easily done in Windows.

Seriously if this was a security flaw update and we had to wait this long you'd think people would be up in arms. Luckly 3.6.4 is mainly just extra functionality.

Still am I just left at the mercy of whenever it appears in the update stream or is there an easy way to update what I already have installed verses having two versions of FF?

---

### Post by philinux on 2010-06-25
[http://ubuntuforums.org/showthread.php?t=330386](http://ubuntuforums.org/showthread.php?t=330386)

And

[http://ubuntuforums.org/showpost.php?p=9502858&postcount=22](http://ubuntuforums.org/showpost.php?p=9502858&postcount=22)

---

### Post by QIII on 2010-06-25
Thanks, Philinux.

Just to add a bit of a philosophical note...

I don't think this is a simple matter of not "letting" Firefox update on its  own.

Mozilla's own documentation gives details about how to update in Linux if you do not want to wait for it to appear in the repo,  and it is not as simple as clicking an update box in the application  itself as in Windows.  Remember that, in general, Linux does exactly  what you tell it to do and only what you tell it to do.  Linux distros  generally do not take it on themselves to do what they think you want or  ought to do.

If you want to update outside of the repo, you can follow Mozilla's update instructions.  You can  well imagine that if Mozilla's own documentation requires some effort to  update in Linux, then some effort will be required somewhere along the  line for someone else to make it happen, even if it is via the repos.

I use both Debian-based and RPM-based distros.  None of them just  "automagically" updates Firefox.

The reason that it takes some time to get updates into Ubuntu (and other  Debian-based distros as well as RPM based distros) is that someone,  somewhere, has to prioritize updates in their queue, package the new  version, test deployment, make adjustments to the package, test again,  etc.  

For a security flaw, the priority would be very high.  So the update would likely be very quick in coming.

To make it easier to update when Mozilla provides an update, Mozilla  would have to build that in to Firefox.  They won't  do it, I am sure.  Not for Linux.  The Linux community would definitely frown on any  application developer who took it on themselves to update such a ubiquitous application on your machine  without what amounts to your explicit consent and absolute control.

I wouldn't want that.  I'm in control of my machine, not a software developer.

---

### Post by Vanillalite on 2010-06-25
Thanks for the reply QIII.

I do have some questions though. I know it's your machine and not the developers, but I mean your getting the updates from them either way right? It's just HOW the updates are getting to you right either via mozilla themselves or through the update manager in Ubuntu right?

How does this go to I'm in control of my machine and not a software developer. Your getting the same update either way? I guess if you don't want the update you could make it optional like it already is in the update manager. Still it's the software developers update either way at least in terms of the base update. Obviously you can do your own think to it post update.

Maybe it's just me, but I don't think adding an update feature into the Linux version wouldn't be that hard to do. I can understand that line of reasoning you gave though.

---

### Post by QIII on 2010-06-25
For any one of 300 Linux distributions, Debian-based, RPM-based, Slackware-based, WhoKnowWhat-based, Mozilla would have to make some simplifying assumptions about how to do the update because to do otherwise would require that they program the installation to match the method each distribution uses to both place the files and to allow them to be updated, removed, reinstalled, etc, via the particular distribution's package management system.  Not only would that be cost prohibitive, it would also present 300 opportunities to get something terribly wrong.

While there ARE some defacto standards about where files are placed in general across Linux distributions, it would be misguided to assume that they are universal.

And how do they handle Solaris, OpenSolaris, OpenBSD, FreeBSD ... ?

I doubt that they would take it on themselves to make those assumptions.

If you install based on your package management system, you are effectively in control of how it is installed because you are aware of where and how it is being installed.  If you are not a "power user", then at least you are aware that it is being installed in a manner consistent with the standard package management installation.

If you use their instructions for installing outside of your package management system, you are aware of where and how it is being installed.  That will probably be outside of your package management system's understanding of where to look to update, remove and reinstall.  But that is your choice.  You can uninstall manually using their instructions.  That is your choice.  In each case, you are in control.

Any outsider's *assumptions* about your machine are someone else's decisions, not yours.

---

### Post by bodhi.zazen on 2010-06-25
Firefox is distributed as a binary

[http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux](http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux)

You can manually extract it or it is for the most part point an click.

Or you can add any of the various firefox repositories:

[https://help.ubuntu.com/community/FirefoxNewVersion/MozillaBuilds](https://help.ubuntu.com/community/FirefoxNewVersion/MozillaBuilds)

---

### Post by QIII on 2010-06-25
Thanks, bodhi.

Most important to the OP's question...

"Generally, you should install from package management..."

---

### Post by bodhi.zazen on 2010-06-25
> **QIII said:**
> Thanks, bodhi.

Most important to the OP's question...

"Generally, you should install from package management..."

That works well if you do not want the most recent version of firefox.

Installing the firefox binary from mozilla is, IMO, trivial and is, IMO the easiest and best option. Certainly easier then editing your sources, adding a gpg key and then running apt-get.

---

### Post by QIII on 2010-06-25
> **bodhi.zazen said:**
> That works well if you do not want the most recent version of firefox.

Installing the firefox binary from mozilla is, IMO, trivial and is, IMO the easiest and best option. Certainly easier then editing your sources, adding a gpg key and then running apt-get.

I'm all for installing binaries as long as the user knows they are doing that.  There are plenty of things I do that way.  That is a deliberate change initiated by the user and under his direct control.  I said the user has that option and it his choice.

Es ist mir egal.  (I like the German idiom for "It's all the same to me.")

My point goes more to "automatic updates" to a new version initiated by applications themselves.

(Edit:  But I don't have a problem with a pop-up that says "Update Me?" in the same version, I guess.)

---

