---
title: "Namoroka???"
date: 2010-04-13
forum: General Help
---

### Post by RobinJ1995 on 2010-04-13
I was just looking around at Launchpad when he update manager popped up, I chose to install the updates now and continued browsing in Firefox.
When suddenly another window pops up aying I'll have to restart Firefox, so I close Firefox and when I go to the Gnome Panel to start it again I see this:
[IMG]http://i39.tinypic.com/b8mwpu.png[/IMG]
The tooltip text still said Firefox Webbrowser so I click it and get a Firefox update screen (with another logo) saying ALL of my Firefox add-ons are incompatible!
I clicked Next and get presented with Firefox as i know it but then slower and with another name and logo...
But what I most hate about Namoroka is that it doesn't do anything but crashing!
I had to type this text 3 times because "Namoroka" froze whole my desktop enviorenment!
So the now I installed Google Chrome (wich I don't like that much :S).

Why the **** are they replacing Firefox by this stupid browser named Namaroko and saying it's a Firefox update???
I thought only Microsoft did things like that with updates?!
--

EDIT:
Ok i read this article:
> **"http://blog.mozilla.com/blog/2009/12/16/namoroka-its-not-just-the-code-name-for-firefox-3-6/"]At Mozilla we foster a healthy ecosystem of communities that promote the ability to freely access, modify and distribute software and creative works. These ecosystems create a digital commons said:**
> 

.... So it's just the pre-release of Firefox...
But why under another name? Why are my add-ons incompatible if it's still Firefox? Why does it always crash? And why isn't there a dutch translation before they put it with the updates? I don't get it why don't they just keep the name Firefox and wait untill everything works properly before giving an update?

How may I be able to undo this update?
Can I just do this?
[QUOTE]sudo aptitude remove firefox
sudo aptitude install firefox

---

### Post by Vaphell on 2010-04-13
[B].... So it's just the pre-release of Firefox...
But why under another name?[/B]

ubuntu has a policy that they major versions of software is locked during the life of the release to minimize number of possible combinations but the problem is that the webbrowser is a major component and lagging with versions is not cool - security and performance issues of older versions. Such updates are pretty much necessary to keep up. Apparently 3.0 or 3.5 was the official version of Firefox and 3.6 slapped on top of that has to use different name

**Why are my add-ons incompatible if it's still Firefox?**

all of them? addons have some kind of definition file that defines which versions are supported. If the addon is for versions 3.0-3.5 then 3.6 will be detected as incompatible. It's the responsibility of addon creator. If the update doesn't work you can try Nightly Tester Tools addon - it can force the browser to use incompatible addons. Usually nothing spectacular happens though there can be bugs.

**Why does it always crash? And why isn't there a dutch translation before they put it with the updates? I don't get it why don't they just keep the name Firefox and wait untill everything works properly before giving an update?**

I use Namoroka for many months and it's rock solid for me, you got unlucky.

Where did you take the firefox update from? Official repos? You can try adding mozilla team stable PPA repos which provide stable versions or daily builds to get bleeding edge stuff.
Also try running firefox from terminal, usually linux apps spew warning and error messages there before they crash. Maybe there will be some hint. Backing up your ff profile and trying with fresh one can help too if something got corrupted in profile files.
Btw, how many versions of firefox binaries are there in your system? In terminal write firefox and tap tab key, it should autocomplete if there is only 1 or list all possibilities - different versions have number attached to the name firefox-3.0, firefox-3.5 etc

If the old version is there (which it should) you can use it

---

### Post by cong06 on 2010-04-13
> **ErJeeB said:**
> 
But why under another name?
Developers like to "codename" different releases. I guess it helps them keep track of which release.
Instead of saying "3.2 is the one with the bug" they can say "firefly is the one with the bug" (I don't know the codename for 3.2... so maybe that was a bad example.
Anyway, names are easier for humans to keep track then numbers, usually anyway.

> **ErJeeB said:**
> Why are my add-ons incompatible if it's still Firefox?
Well, each version of firefox comes with different features/restrictions. The pulgins you downloaded were designed for a different version, so they may be requiring different things.
No worries, when the release is actually "stable" then most likely the plugins will be "re-done" so that they're working for the release
> **ErJeeB said:**
> Why does it always crash? And why isn't there a dutch translation before they put it with the updates? I don't get it why don't they just keep the name Firefox and wait untill everything works properly before giving an update?
Well, Ubuntu has a thing about giving "unstable" releases. Now, generally these are with new versions, ie: if you install 10.04 now, they'll give you the newest version of Firefox and stick with it till the end of time (or rather the end of 10.04).

I'm not entirely sure how this new version (what version number is it, btw?) was installed for you. One possibility is that you added a repository to your "/etc/apt/sources.list" file.
If that's what you did, then just remove it and then run update, remove firefox, install firefox.
Though, you'd probably want to post your "/etc/apt/source.list" file and give us your ubuntu version number unless you're sure you know how to proceed from here.
```

cat /etc/apt/sources.list

```

---

### Post by RobinJ1995 on 2010-04-13
> 
Btw, how many versions of firefox binaries are there in your system? In terminal write firefox and tap tab key, it should autocomplete if there is only 1 or list all possibilities - different versions have number attached to the name firefox-3.0, firefox-3.5 etc

If the old version is there (which it should) you can use it

At the terminal there's only "firefox", no other one's show up with tab-autocomplete, and when I press enter, Namaroka just starts...

> Where did you take the firefox update from? Official repos? You can try adding mozilla team stable PPA repos which provide stable versions or daily builds to get bleeding edge stuff.

Don't know... Update Manager just popped up, didn't check wich updates there were and where they came from, i just clicked "Install" :)

> Though, you'd probably want to post your "/etc/apt/source.list" file and give us your ubuntu version number unless you're sure you know how to proceed from here.
```
$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://be.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://be.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://be.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://be.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://be.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://be.archive.ubuntu.com/ubuntu/ karmic universe
deb http://be.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://be.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://be.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://be.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://be.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://be.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://be.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://be.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse

```

I'm starting to like Midori webbrowser, it's even faster than firefox :P

---

### Post by cong06 on 2010-04-14
Ok, based off your sources.list file, it seems you're using 9.10 Karmic Koala.
I am also using this version, but as I haven't had the bandwidth to, I haven't had a chance to upgrade my firefox package.
That being said, my firefox package is still 3.5, whereas yours (apparently?) is 3.6.

Um, I should have told you this before, but go ahead and run this:
```

cat /etc/apt/sources.list.d/*

```
and post the output (if any).

If there isn't any, then I'm at a loss as to what actually happened, unless someone else using Karmic had the same "accidental" upgrade to firefox.

That being said, you can always remove and reinstall and see if that fixes it.

---

### Post by RobinJ1995 on 2010-04-14
> **cong06 said:**
> Ok, based off your sources.list file, it seems you're using 9.10 Karmic Koala.
I am also using this version, but as I haven't had the bandwidth to, I haven't had a chance to upgrade my firefox package.
That being said, my firefox package is still 3.5, whereas yours (apparently?) is 3.6.

Um, I should have told you this before, but go ahead and run this:
```

cat /etc/apt/sources.list.d/*

```
and post the output (if any).

If there isn't any, then I'm at a loss as to what actually happened, unless someone else using Karmic had the same "accidental" upgrade to firefox.

That being said, you can always remove and reinstall and see if that fixes it.

```
$ cat /etc/apt/sources.list.d/*
deb http://dl.google.com/linux/deb/ stable main
deb http://dl.google.com/linux/deb/ stable main
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu karmic main

```

---

### Post by cong06 on 2010-04-14
So as I though (and hoped), you added another repository so you could get the latest Firefox.

Open up "System > Administration > Software Sources"
Go to the "Third Party" tab
uncheck the one that looks like:
```

deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu karmic main

```

Then run:
```

aptitude search firefox

```
And post all the output from this command.

---

### Post by RobinJ1995 on 2010-04-14
> **cong06 said:**
> So as I though (and hoped), you added another repository so you could get the latest Firefox.

Open up "System > Administration > Software Sources"
Go to the "Third Party" tab
uncheck the one that looks like:
```

deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu karmic main

```

Then run:
```

aptitude search firefox

```
And post all the output from this command.

I did what you said and reinstalled firefox...
And what the heck now I just have "A Webbrowser" in my Gnome menu under Internet/Network xD
[IMG]http://i41.tinypic.com/qsmi5k.png[/IMG]
Same as with Namoroka only now it just says "Web Browser" in stead of "Namoroka", only this seems to work lot better :)

---

### Post by cong06 on 2010-04-14
> **ErJeeB said:**
> 
Same as with Namoroka only now it just says "Web Browser" in stead of "Namoroka", only this seems to work lot better :)

lol.

Well, that works...
but if you want to post the output of:
```

aptitude search firefox

```
We can figure out how many firefox browsers you have installed, and maybe do something about it.

---

### Post by RobinJ1995 on 2010-04-14
> **cong06 said:**
> lol.

Well, that works...
but if you want to post the output of:
```

aptitude search firefox

```
We can figure out how many firefox browsers you have installed, and maybe do something about it.

```
$ aptitude search firefox
c   firefox                                                                - safe and easy web browser from Mozilla                                          
v   firefox-2                                                              -                                                                                 
v   firefox-2-dom-inspector                                                -                                                                                 
v   firefox-2-libthai                                                      -                                                                                 
p   firefox-3.0                                                            - dummy upgrade package for firefox-3.0 -> firefox-3.5                            
p   firefox-3.0-branding                                                   - dummy upgrade package for firefox-3.0 -> firefox-3.5                            
p   firefox-3.0-dev                                                        - dummy upgrade package for firefox-3.1 -> firefox-3.5                            
p   firefox-3.0-dom-inspector                                              - dummy upgrade package for firefox-3.0 -> firefox-3.5                            
p   firefox-3.0-gnome-support                                              - dummy upgrade package for firefox-3.0 -> firefox-3.5                            
p   firefox-3.0-venkman                                                    - dummy upgrade package for firefox-3.0 -> firefox-3.5                            
p   firefox-3.1                                                            - dummy upgrade package for firefox-3.1 -> firefox-3.5                            
p   firefox-3.1-branding                                                   - dummy upgrade package for firefox-3.1 -> firefox-3.5                            
p   firefox-3.1-dbg                                                        - dummy upgrade package for firefox-3.1 -> firefox-3.5                            
p   firefox-3.1-dev                                                        - dummy upgrade package for firefox-3.1 -> firefox-3.5                            
p   firefox-3.1-gnome-support                                              - dummy upgrade package for firefox-3.1 -> firefox-3.5                            
i A firefox-3.5                                                            - safe and easy web browser from Mozilla                                          
p   firefox-3.5-branding                                                   - Package that ships the firefox branding                                         
p   firefox-3.5-dbg                                                        - firefox-3.5 debug symbols                                                       
p   firefox-3.5-dev                                                        - Development files for Mozilla Firefox                                           
pi  firefox-3.5-gnome-support                                              - Support for Gnome in Mozilla Firefox                                            
i   firefox-3.6                                                            - special transitional package for ffox 3.6 daily users                           
v   firefox-adblock-plus                                                   -                                                                                 
v   firefox-bindwood                                                       -                                                                                 
p   firefox-dom-inspector                                                  - dummy upgrade package for firefox-3.0 -> firefox-3.5                            
pi  firefox-gnome-support                                                  - meta package pointing to the latest gnome-support package for firefox           
p   firefox-greasemonkey                                                   - dummy transitional package for firefox-greasemonkey -> greasemonkey             
p   firefox-launchpad-plugin                                               - Launchpad firefox integration                                                   
p   firefox-linky                                                          - firefox extension to handle web and image links                                 
v   firefox-mozgest                                                        -                                                                                 
p   firefox-notify                                                         - integrate Firefox download messages with desktop notifications                  
v   firefox-pwdhash                                                        -                                                                                 
p   firefox-sage                                                           - Lightweight RSS and Atom feed reader for Firefox                                
p   firefox-showcase                                                       - Showcase provides a new way to manage your Firefox tabs and windows.            
v   firefox-speeddial                                                      -                                                                                 
p   firefox-ubuntu-it-menu                                                 - Firefox extension for a quick browse of Ubuntu-it community                     
p   firefox-webdeveloper                                                   - web developer extension for the Firefox web browser                             
p   kubuntu-firefox-installer                                              - Firefox installer for Kubuntu                                                   
p   mozilla-firefox-adblock                                                - advertisement blocking extension for web browsers (dummy package)  
```

But if it comes to me, the problem is solved :P
"A Webbrowser" looks silly in my menu but works as good as the old firefox :)

---

### Post by Vaphell on 2010-04-14
it looks like PPA with daily builds messed up a little. It's ok to use it but one should expect screwups.
If you prefer 'stable' versions use this one instead
[https://launchpad.net/~mozillateam/+archive/firefox-stable](https://launchpad.net/~mozillateam/+archive/firefox-stable)

less updates, less hassle.

---

### Post by cong06 on 2010-04-15
Well, try this:
```

apt-get remove firefox-3.5 firefox-3.6
apt-get install firefox

```

note: it's interesting that you reinstalled firefox, and yet aptitude thinks that the "firefox" package isn't installed.

---

### Post by RobinJ1995 on 2010-04-15
Thanks everyone, problem solved!
I have my old-trusted FireFox back! :)

---

