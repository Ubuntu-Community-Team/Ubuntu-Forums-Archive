---
title: "Google Chrome update again?"
date: 2011-09-17
forum: General Help
---

### Post by gonzo74405 on 2011-09-17
Once a week or so I click on the update icon to get what's new. It seems like at least every third or fourth time the updates include yet another twenty-some meg Google Chrome package. Is it : 1)I'm doing something wrong and this shouldn't be happening?, 2)Google likes to make lots of incremental upgrades instead of waiting a while between versions?, or 3)is this some alien plot to grab bandwidth for some evil purpose?

---

### Post by bapoumba on 2011-09-17
Which Ubuntu release are you using ?
I have not noticed anything strange. May be the aliens shipped a blurring gas to me too :)

---

### Post by ubudog on 2011-09-17
Do you have the dev ppa?  If so, that's normal.

If not, then that's very weird... aliens can be strange creatures sometimes...

---

### Post by bapoumba on 2011-09-17
> **ubudog said:**
> Do you have the dev ppa?  If so, that's normal.

If not, then that's very weird... aliens can be strange creatures sometimes...
Yeah, I'm using stock chromium and have not got any particular upgrades (nothing that caught my attention). But I could have been mystified by these aliens :)

---

### Post by ubudog on 2011-09-17
> **bapoumba said:**
> Yeah, I'm using stock chromium and have not got any particular upgrades (nothing that caught my attention). But I could have been mystified by these aliens :)

Same here.

:lolflag:

---

### Post by gonzo74405 on 2011-09-18
Using 11.04. Chrome works fine, just get frequent upgrades. Have no idea what a dev ppa is so it's hard to tell.

---

### Post by sikander3786 on 2011-09-18
> **gonzo74405 said:**
> Using 11.04. Chrome works fine, just get frequent upgrades. Have no idea what a dev ppa is so it's hard to tell.
If you are using Google Chrome and not Chromium, perhaps it is not a Dev PPA but instead updates are coming from the Chrome stable channel as they just released v14 of Google Chrome, yesterday I think.

---

### Post by jramshu on 2011-09-18
I have chrome on another machine and it does seem to update a lot. This one has chromium and it doesn't seem to get many updates.

Still waiting on the aliens.

---

### Post by sikander3786 on 2011-09-18
> **jramshu said:**
> I have chrome on another machine and it does seem to update a lot. This one has chromium and it doesn't seem to get many updates.

Still waiting on the aliens.
Then please post the outputs of these commands from Terminal:

```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d
```

So, let's hunt the aliens ;)

---

### Post by vasa1 on 2011-09-18
> **sikander3786 said:**
> If you are using Google Chrome and not Chromium, perhaps it is not a Dev PPA but instead updates are coming from the Chrome stable channel as they just released v14 of Google Chrome, yesterday I think.

I installed Google Chrome (v13, Stable Channel) a couple of days ago. As part of the installation, Google added its **own** ppa which is now listed in the Software Center.

As of this morning, no update (to v14) was pushed to me. There have been a few posts about update problems from v13 to v14. 

-http://googlechromereleases.blogspot.com/2011/09/stable-channel-update_16.html-

Let's see.

---

### Post by cottfcfan on 2011-09-18
vasa1 is correct.
If you downloaded Chrome from the Google website, it adds its own ppa to your software sources.
And YES there are a lot of updates, seems like about once a week, but at least you always have the latest version. Version 14 came through on Friday.

---

### Post by jramshu on 2011-09-18
@sikander3786

Sorry, jumped off here right after this.

Here is the chrome-stable
```
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main
```

Sources list:
```
#deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse
```

Edit: Yes, when you agree to the terms they add the repos automatically.

---

### Post by vasa1 on 2011-09-18
> **vasa1 said:**
> ...

As of this morning, no update (to v14) was pushed to me. There have been a few posts about update problems from v13 to v14. 

-http://googlechromereleases.blogspot.com/2011/09/stable-channel-update_16.html-

Let's see.

While I didn't get a prompt via Ubuntu Software Center,
on running
sudo apt-get update
and sudo apt-get upgrade
I was updated to version 14. It was a **full** install of ~27 MB and the terminal screen informed me of the size before I chose to continue ([http://ubuntuforums.org/showpost.php?p=11262774&postcount=6](http://ubuntuforums.org/showpost.php?p=11262774&postcount=6)).

---

### Post by kstella on 2011-09-19
How long does it take to download? I've had the update manager open for the past 8 hrs. Of ~68MB of updates to download, the ~27MB for google-chrome-stable are not even 20% downloaded. Everything else downloaded within minutes. :/

---

### Post by vasa1 on 2011-09-19
> **kstella said:**
> How long does it take to download? I've had the update manager open for the past 8 hrs. Of ~68MB of updates to download, the ~27MB for google-chrome-stable are not even 20% downloaded. Everything else downloaded within minutes. :/

Something obviously went wrong. Is there a way to *gracefully* exit such things? And I've read somewhere about changing servers. Perhaps someone can throw some light on that as well.

But to answer your question:
```
Fetched 27.7 MB in 13min 20s (34.6 kB/s)
```
And that's about the speed I get for most of my surfing.

---

### Post by gonzo74405 on 2011-09-20
OK, just seems frequent to me. Just got ANOTHER one today (9/20) at 26 megs. Even the droids at Microsoft only update their entire operating system once a month. Is there really that much to update in a browser? Oh well, Ubuntu runs great and I wouldn't trade Chrome for anything else - onlyt wanted to know if I had a special glitch that I should worry about. Just doing what the voices tell me.....

---

### Post by cottfcfan on 2011-09-21
The Chrome repo has recently become very slow.
Thats googles issue not Ubuntus.
If your Ubuntu downloads are slow, change the mirror in software sources. "select best server".
My download speeds are about 1.6mb/second, which is as fast as it gets for me.
But obviously it will vary by computer spec and area.

---

### Post by vasa1 on 2011-09-21
Gonzo, when you're done with the aliens and the voices ;) you could check out [http://googlechromereleases.blogspot.com/](http://googlechromereleases.blogspot.com/)

This latest update was courtesy Adobe Flash. Again.

BTW, if you update Chrome on a Windows OS, you do get incremental (delta) updates and not the full ~27 MB (currently) update. Google was pretty proud of their system. You can search for "Courgette" which is what they called it a couple of years ago.

It's a pity that each update on Linux pulls down an entire installation. I've seen the same thing happening with Firefox.

---

### Post by Linux_junkie on 2011-09-21
> **gonzo74405 said:**
> OK, just seems frequent to me. Just got ANOTHER one today (9/20) at 26 megs. Even the droids at Microsoft only update their entire operating system once a month. Is there really that much to update in a browser? Oh well, Ubuntu runs great and I wouldn't trade Chrome for anything else - onlyt wanted to know if I had a special glitch that I should worry about. Just doing what the voices tell me.....

You can always move over to Chromium, doesn't update as much.  I've got Chromium on my desktop pc running Xubuntu 10.10 and the last update of Chromium was from 12 to 13.  No updates since.

---

### Post by northwestuntu on 2011-09-21
im using linux mint 11 chromium and its still has 12 on here? should i switch to chrome for better updates?

---

### Post by vasa1 on 2011-09-21
> **northwestuntu said:**
> im using linux mint 11 chromium and its still has 12 on here? should i switch to chrome for better updates?

There's a Mint forum ([http://forums.linuxmint.com/](http://forums.linuxmint.com/)) that maybe able to suggest the best route for you.

---

### Post by Duncan Williams on 2011-09-21
I would think that if you don't want constant google chrome updates, just uncheck the ppa in update manager and re-enable it say once a month to maintain an update path?

---

