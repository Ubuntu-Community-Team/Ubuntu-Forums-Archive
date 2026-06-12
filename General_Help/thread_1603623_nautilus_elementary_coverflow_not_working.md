---
title: "nautilus elementary coverflow not working"
date: 2010-10-23
forum: General Help
---

### Post by TheNerdAL on 2010-10-23
I installed it and press F4 and nothing happens. :( Can anyone help me? 

Thanks.

---

### Post by TheNerdAL on 2010-10-23
Bump.

---

### Post by inameiname on 2010-10-23
I'm guessing all it's doing is giving you a blank screen where coverflow should be, similar to the built-in terminal, but without the command prompt, right? If so, it's an easy fix.

You must add this line to the file "/etc/environment":

export CLUTTER_VBLANK=none

Then restart.

FYI, for me, the only thing that was written on the text file already (prior to adding the above line below it) was something like this. Maybe it's the same for you:

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

Here is a similar thread that was solved about this, which even has the creator of nautilus-elementary, Ammonkey, commenting on this being why it's not working at default.

[http://wwww.ubuntuforums.org/showthread.php?t=1592064](http://wwww.ubuntuforums.org/showthread.php?t=1592064)

---

### Post by TheNerdAL on 2010-10-23
It doesn't give me a blank screen, nothing happens. Like if I were to go to the music folder and press F4, nothing would happen.

---

### Post by inameiname on 2010-10-23
I've never opened clutterflow that way, so I'm not sure. (I never really use the thing.) Have you tried opening it by clicking View >> Clutterflow in the menubar?

---

### Post by TheNerdAL on 2010-10-23
> **inameiname said:**
> I've never opened clutterflow that way, so I'm not sure. (I never really use the thing.) Have you tried opening it by clicking View >> Clutterflow in the menubar?

It doesn't give me that option.

---

### Post by inameiname on 2010-10-23
That's strange. How did you install nautilus-elementary? 

I just use the nautilus-elementary ppa, and am using Maverick, and have the option right there under 'View', below the Zooming in and out options, and above Embed Terminal and my current icon view, Icons, List, Compact. 

If you don't have that option, sounds to me like you are having a greater issue than just clutterflow not working, as yours shouldn't be any different than mine.

I guess maybe if it was an older nautilus-elementary version, from bzr, then it might not have all installed, to which I suggest installing the latest from the PPA.

---

### Post by TheNerdAL on 2010-10-23
> **inameiname said:**
> That's strange. How did you install nautilus-elementary? 

I just use the nautilus-elementary ppa, and am using Maverick, and have the option right there under 'View', below the Zooming in and out options, and above Embed Terminal and my current icon view, Icons, List, Compact. 

If you don't have that option, sounds to me like you are having a greater issue than just clutterflow not working, as yours shouldn't be any different than mine.

I guess maybe if it was an older nautilus-elementary version, from bzr, then it might not have all installed, to which I suggest installing the latest from the PPA.

I installed from PPA as well.

---

### Post by inameiname on 2010-10-23
Hmmm, well I don't really know what to tell you then. It's a little out of my knowledge base. Perhaps you should file a bug:

[https://bugs.launchpad.net/nautilus-elementary](https://bugs.launchpad.net/nautilus-elementary)


Or perhaps reinstall nautilus-elementary, Maverick edition, and see if that fixes things, idk.


Did you try adding that line to /etc/environment and restart to see if it fixed your clutterflow issue anyway?

---

### Post by TheNerdAL on 2010-10-23
> **inameiname said:**
> Hmmm, well I don't really know what to tell you then. It's a little out of my knowledge base. Perhaps you should file a bug:

[https://bugs.launchpad.net/nautilus-elementary](https://bugs.launchpad.net/nautilus-elementary)


Or perhaps reinstall nautilus-elementary, Maverick edition, and see if that fixes things, idk.


Did you try adding that line to /etc/environment and restart to see if it fixed your clutterflow issue anyway?


How do I reinstall because I just did what this page told me to do: [http://aroundtheweb.info/2010/10/install-nautilus-elementary-ubuntu-10-10-maverick-meerkat-clutter-view-ppa/](http://aroundtheweb.info/2010/10/install-nautilus-elementary-ubuntu-10-10-maverick-meerkat-clutter-view-ppa/)

but I still get the same thing.

---

### Post by inameiname on 2010-10-24
[B]Yeah, that is how to install it. Uhm, well personally, to know it's not a nautilus-elementary issue if it happens again after a reinstall, I'd ppa-purge the whole thing, and then add it again, just as you did before.

If you don't have ppa-purge already, I suggest adding it, as it's a handy thing in case of a bad ppa repo. It merely uninstalls all that is from the selected ppa, and restores versions of any files (such as nautilus) from the rest of the sources.list you have, mainly official ones.

Anyway, that's just:

sudo apt-get install ppa-purge
sudo ppa-purge ppa:am-monkeyd/nautilus-elementary-ppa
sudo nautilus -q
...and then readd it again...
sudo add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa
sudo apt-get update
sudo apt-get upgrade
sudo nautilus -q

FYI, if you have Ubuntu-Tweak installed (another useful gem if you don't have already), has ppa-purge built-in. Just find ppa:am-monkeyd/nautilus-elementary-ppa.&#65279;[/B]

---

### Post by TheNerdAL on 2010-10-24
I get this error when updating: 
```
adrian@adrian-desktop:~$ sudo apt-get update
E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-maverick.list
E: The list of sources could not be read.

```

---

### Post by inameiname on 2010-10-24
Sounds like you have a typo in your sources.list. Can you post it?:

sudo gedit /etc/apt/sources.list

---

### Post by TheNerdAL on 2010-10-24
> **inameiname said:**
> Sounds like you have a typo in your sources.list. Can you post it?:

sudo gedit /etc/apt/sources.list

Yes. 
```
deb http://download.tuxfamily.org/gericom/libreoffice /
deb http://archive.ubuntu.com/ubuntu maverick universe main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick universe main restricted multiverse #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ maverick-security universe main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu/ maverick-security universe main restricted multiverse
deb http://archive.ubuntu.com/ubuntu maverick-updates universe main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick-updates universe main restricted multiverse
deb http://archive.ubuntu.com/ubuntu maverick-backports universe main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick-backports universe main restricted multiverse
deb http://archive.ubuntu.com/ubuntu maverick-proposed universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-proposed universe main multiverse restricted
```

---

### Post by inameiname on 2010-10-24
Oops. Seems you have your various sources listed separately, in separate files, inside /etc/apt/sources.list.d/ folder, instead of one larger text file, called sources.list, inside /etc/apt/.

On default, there is just one, and it would normally look like this:

```

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-proposed restricted main multiverse universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse

```Personally, that's easier for me, to have all my sources in one file, (the 'official repos ones like the example I gave above, and additional PPAs and other repos I add below that), but some prefer them separate. I guess then, what I need to see is the particular sources.list for nautilus-elementary.

Another way to see them is in ubuntu-tweak, to which you can see how they've all been separated into many text files.

This is at least what I'm guessing, as the one you provided isn't much of a sources.list if that's all that's there. Especially since it doesn't have nautilus-elementary's ppa in it.

Update:

Yeah, I'm an idiot. I didn't notice the error you gave was found in nautilus-elementary's sources.list:

adrian@adrian-desktop:~$ sudo apt-get update
E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-maverick.list
E: The list of sources could not be read.

sudo gedit /etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-maverick.list

---

### Post by TheNerdAL on 2010-10-24
Will this help? 
[IMG]http://i.imgur.com/41gBG.png[/IMG]

---

### Post by inameiname on 2010-10-24
Well that's the line, but if the "#" is there in front, then your nautilus-elementary ppa is disabled. That must not be there for it to read that line, and that ppa, and to get the updates for nautilus-elementary.

Thus, I believe the reason you got the error is your sources.list for nautilus-elementary was already disabled, due to you upgrading to Maverick. It does that for all of your sources that aren't official ones, so I'd look into if you have other ppas that are also disabled.

This also means that the reason you cannot find clutterflow is because you only have nautilus-elementary for Lucid, as you've never had the Maverick repo for it to upgrade to Nautilus-Elementary, Maverick edition. Once you've added the ppa, just by removing that #, you will find it'll update. No need to reinstall then, if this is the culprit from the start.

The line on mine is this (the deb-src line isn't needed, but is merely needed if ever you want the nautilus-elementary source files, that's all):

```

deb http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu maverick main        #Nautilus Elementary
deb-src http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu maverick main

```

---

### Post by TheNerdAL on 2010-10-24
I didn't see your edit. 

This is how it looks like: ```
deb http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu maverick main
deb-src http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu maverick main
ain
```

---

### Post by inameiname on 2010-10-24
Remove the 'ain' on the third line. That's the error.

But I'm also a tad confused, as you gave me that line with '#' before it. Seems now you don't have that line on there. 

Regardless, 'ain' must've been some junk left over accidentally. Just rid yourself of that and do what was said in the beginning. Guess you do have Maverick version installed if the ppa wasn't disabled.

---

### Post by TheNerdAL on 2010-10-24
> **inameiname said:**
> Remove the 'ain' on the third line. That's the error.

But I'm also a tad confused, as you gave me that line with '#' before it. Seems now you don't have that line on there. 

Regardless, 'ain' must've been some junk left over accidentally. Just rid yourself of that and do what was said in the beginning. Guess you do have Maverick version installed if the ppa wasn't disabled.

I removed the "#" before I posted that. 

I reinstalled it and restarted but it still gives me the same thing.

---

### Post by inameiname on 2010-10-24
Hmm, well I'm not sure what else to say. Guess file a bug at the above mentioned place, and see if someone there can specifically help you. Ammonkey is awesome at finding time to help around town. Sorry.

---

