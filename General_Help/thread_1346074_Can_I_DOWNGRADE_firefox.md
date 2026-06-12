---
title: "Can I DOWNGRADE firefox?"
date: 2009-12-04
forum: General Help
---

### Post by Dee_Ann on 2009-12-04
Hi,

I somehow have a messed up copy of firefox installed, it says it's 3.5.7pre

Here's the info from the about screen,

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.7pre) Gecko/20091203 Ubuntu/9.04 (jaunty) Shiretoko/3.5.7pre

Well, it's really, really, really messed up.  :(

And I can not figure out how in the world to down grade it to an older version, like 3.4 or something that's had all the bugs fixed.  This one, it's got a bazillion bugs and I just can't use it.  Everything is broken.  Well, almost everything.  

Can I downgrade it?  Where can I find old copies of it and instructions to install it?
I don't know about all that compiling stuff, I tried it before and it's way over my head.
I need a way to click through the installation, like the dumbie version. ;)
I have a lot of plugins/addons, bookmarks, etc.  I can't lose that stuff, I really need it.
And I really need a copy of firefox that isn't broken experimental stuff.

Thanks!

---

### Post by HappyFeet on 2009-12-04
FF 3.5.5 should be in synaptic package manager. Remove 3.5.7 first.

---

### Post by Leppie on 2009-12-04
Can you not remove the current version from your system using synaptic? Do a search on "firefox" and right click all the entries referring to 3.5.7 and select "Mark for removal" (**_not_** "Mark for complete removal" as this will also remove personal settings, etc.).
Then reinstall v.3.5.5 (or whichever version you have that's not 3.5.7 in synaptic).

---

### Post by judge jankum on 2009-12-04
That's what i did. then I went back to 3.0.15  For now it's my favorite..

---

### Post by wojox on 2009-12-04
Firefox 3.5.7pre is a pre-release. That's why your addon's don't seem to function. In synaptic go to Status > Installed (local or obsolete) and mark Firefox 3.5.7pre for complete removal. This wont remove your settings in /home/username/.mozilla (bookmarks, addon's and such). Then install Firefox-3.5

---

### Post by Dee_Ann on 2009-12-04
> **wojox said:**
> Firefox 3.5.7pre is a pre-release. That's why your addon's don't seem to function. In synaptic go to Status > Installed (local or obsolete) and mark Firefox 3.5.7pre for complete removal. This wont remove your settings in /home/username/.mozilla (bookmarks, addon's and such). Then install Firefox-3.5


Well the problem is, there are no other versions of 3.5 showing in synaptic, just the 3.5.7pre

There are other entries with different version numbers in the description but they all note that they are dummy links to the most current version, 3.5.7pre  :(

---

### Post by Dee_Ann on 2009-12-04
oh wait, I just downgraded it to 3.5.5 and it's still messed up.

I've sort of narrowed down the probable item that is causing me grief.

When I enable adblock like 80% of the screen is just a blank dead zone.
The adblock thingie in the toolbar doesn't show either.
I can not access or control adblock.  When I disable it, the screen appears normal but them I'm overwhelmed with twirling, whirling, waving things that I do NOT want to see. (ads)

I have removed adblock and installed new and older versions and every single one of them does the same thing, the screen gets all messed up and I can't click on things to open pop up windows, like when I'm shopping and I want to see a close up picture of the items, I used to could click and it would open a little window.  It won't do that anymore now.

I'm so aggravated!

Here's a sample,

[[IMG]http://img710.imageshack.us/img710/5092/screenshot29.th.png[/IMG]]("http://img710.imageshack.us/my.php?image=screenshot29.png")

---

### Post by winotree on 2009-12-04
Is this in your sources list?  

deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main

Removing it [as that's where the 3.5.7pre comes from] may help.

---

### Post by Dee_Ann on 2009-12-05
> **winotree said:**
> Is this in your sources list?  

deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main

Removing it [as that's where the 3.5.7pre comes from] may help.

No, not in there.

---

### Post by Dee_Ann on 2009-12-05
Ok, I downgraded it to 3.5.5 (Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.7pre) Gecko/20091203 Ubuntu/9.04 (jaunty) Shiretoko/3.5.5)

But javascript is badly broken.  Popup windows, don't pop up at all.  Javascript just doesn't work no matter what I do.  Being that most of the internet is javascript I can't do very much of anything now.

For instance I went to one website that has photos.  You click the photos and a window pops up to show you a full size version of the image.  Firefox will NOT work now.

I loaded the browser called epiphany and that same website works perfectly.
But I don't like that browser. I don't want to have to use it.  I need firefox working again like it was a week ago.

I also have an old copy of firefox installed, (Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.15) Gecko/2009102815 Ubuntu/9.04 (jaunty) Firefox/3.0.15) and it is also broken in the same way.

With or without adblock installed, doesn't matter.  I checked the setup and javascript is turned on, allowed and popups are not blocked.  I checked the add ons and none are installed that would block javascript.

I'm totally lost....

I also went into synaptic and uninstalled ALL copies of firefox then I erased the .mozilla directory in my home directory.  I then installed firefox 3.0.15 again.  Well that's just a messed up version, it won't display several websites I frequent (they are javascript heavy) so I went back to synaptic and selected to install firefox 3.1

In synaptic it notes that installing 3.1 is a dummy that actually installs 3.5.5

Well, 3.5.5 is broken too.  

Please, let me select a middle version!  Like 3.4 or 3.3 or whatever I want.
Why must I be forced to accept bleeding edge, experimental software that leaves me with an unusable computer??  Totally unacceptable.

That epiphany browser works so I know it's NOT the computer.  Something is WRONG WITH FIREFOX. 

Please, can someone tell me how to fix it?????  I am really hurting now.  This is a nasty mess and I'm very unhappy with it.

Thank you..

---

### Post by wojox on 2009-12-05
Here's a good trouble shooting thread: [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by raktarok on 2009-12-05
Ok, try this.
Add this line in the file /etc/apt/sources.list
```
deb http://getswiftfox.com/builds/debian unstable non-free #SwiftFox
```
Swiftfox is an optimized version of firefox. You can read more about it here:
[http://www.webupd8.org/2009/07/what-is-and-how-to-install-swiftfox-web.html](http://www.webupd8.org/2009/07/what-is-and-how-to-install-swiftfox-web.html)
Even though it says unstable, I have had no problems with it so far, and currently, its based on firefox 3.5.5.

Then do this:
```
sudo apt-get install swiftfox
```
You may want to select the swiftfox package corresponding to your CPU architecture. Read about it in the above link.

---

### Post by Dee_Ann on 2009-12-05
> **wojox said:**
> Here's a good trouble shooting thread: [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")


Went all the way through it.  Still broken.  Nothing at all helps.  :(

---

### Post by Dee_Ann on 2009-12-05
> **raktarok said:**
> Ok, try this.
Add this line in the file /etc/apt/sources.list
```
deb http://getswiftfox.com/builds/debian unstable non-free #SwiftFox
```Swiftfox is an optimized version of firefox. You can read more about it here:
[http://www.webupd8.org/2009/07/what-is-and-how-to-install-swiftfox-web.html](http://www.webupd8.org/2009/07/what-is-and-how-to-install-swiftfox-web.html)
Even though it says unstable, I have had no problems with it so far, and currently, its based on firefox 3.5.5.

Then do this:
```
sudo apt-get install swiftfox
```You may want to select the swiftfox package corresponding to your CPU architecture. Read about it in the above link.

Tried that and it fusses at me too,

swiftfox-athlon64:
  Depends: libgtk2.0-0 (>=2.18) but 2.16.1-0ubuntu2 is to be installed

Well, I don't have an athlon, it's an intel core duo quad.  The only intel chips I saw listed were a "prescot" and "older".  I don't even know what a prescot chip is.

Actually, I'm thinking that I should just wipe the whole stupid computer clean and start over.  I can't deal with this.  :(

---

### Post by wojox on 2009-12-05
What happens if you open a terminal and run:

```
firefox
```

What's the output?

---

### Post by raktarok on 2009-12-05
> **Dee_Ann said:**
> Tried that and it fusses at me too,

swiftfox-athlon64:
  Depends: libgtk2.0-0 (>=2.18) but 2.16.1-0ubuntu2 is to be installed

Well, I don't have an athlon, it's an intel core duo quad.  The only intel chips I saw listed were a "prescot" and "older".  I don't even know what a prescot chip is.

Actually, I'm thinking that I should just wipe the whole stupid computer clean and start over.  I can't deal with this.  :(

Try prescot. I am using dual core processor and its working fine. I don't know if it will work with quad core, but no harm in trying.
Good luck, and don't give up!

---

### Post by Dee_Ann on 2009-12-05
> **wojox said:**
> What happens if you open a terminal and run:

```
firefox
```What's the output?



Well, this is what it says,

```
dee@Xena:~$ firefox
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
dee@Xena:~$


```That runs the 3.0.x (I forget the exact version but it's the OLD one that's equally as broken)

IF I instead type firefox-3.5 it simply does the following.

```

dee@Xena:~$ firefox-3.5
dee@Xena:~$ 

```It will then open the Shiretoko 3.5.5 browser.  When I close the browser it returns to the prompt without any error messages.

---

### Post by Dee_Ann on 2009-12-05
> **raktarok said:**
> Try prescot. I am using dual core processor and its working fine. I don't know if it will work with quad core, but no harm in trying.
Good luck, and don't give up!


If javascript is broken on all versions of firefox I've tried so far, what would make it work on another version of firefox?

---

### Post by fluffman86 on 2009-12-05
You may have a problem with your settings somewhere. In firefox, backup your bookmarks by going to Bookmarks > Organize > Backup and save them to your Desktop.  Open your home folder, press ctrl+H to show hidden files, then rename .mozilla to .mozilla-backup.  

Now re-open firefox-3.5 and it will create a clean profile for you.  Now you can re-add your bookmarks and plugins.  Add *ONE PLUGIN AT A TIME* and if you start experiencing problems again, you'll know which one caused an error (maybe none).

Also, if some of your extensions won't load because that version of firefox isn't supported, you can usually get around that by typeing about:config in the address bar, press enter, then right-click > new > boolean > extensions.checkCompatibility > false.

---

### Post by raktarok on 2009-12-05
Sorry, but I don't have an answer to that question.

anyway, how did you install the Shiretoko browser in the first place? Its not available from the default repos, I think. Can you please post the contents of your file /etc/apt/sources.list plus the name of the files in the directory /etc/apt/sources.list.d? 

Since you using shiretoko(test build for firefox), you could try installing this addon and see if it helps.
[https://addons.mozilla.org/en-US/firefox/addon/6543](https://addons.mozilla.org/en-US/firefox/addon/6543)

---

### Post by Dee_Ann on 2009-12-05
No luck on swiftfox.

```
dee@Xena:~/Downloads$ sudo dpkg -i swiftfox-3.5.5-1_prescott.deb
[sudo] password for dee: 
dpkg: error processing swiftfox-3.5.5-1_prescott.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 swiftfox-3.5.5-1_prescott.deb


dee@Xena:~/Downloads$ ls swift*
swiftfox_3.5.5-1_prescott.deb
dee@Xena:~/Downloads$ sudo dpkg -i swiftfox_3.5.5-1_prescott.deb
Selecting previously deselected package swiftfox-prescott.
(Reading database ... 245669 files and directories currently installed.)
Unpacking swiftfox-prescott (from swiftfox_3.5.5-1_prescott.deb) ...
dpkg: dependency problems prevent configuration of swiftfox-prescott:
 swiftfox-prescott depends on libgtk2.0-0 (>= 2.18); however:
  Version of libgtk2.0-0 on system is 2.16.1-0ubuntu2.
dpkg: error processing swiftfox-prescott (--install):
 dependency problems - leaving unconfigured
Processing triggers for menu ...
Errors were encountered while processing:
 swiftfox-prescott
dee@Xena:~/Downloads$ 

```

---

### Post by Dee_Ann on 2009-12-05
> **raktarok said:**
> Sorry, but I don't have an answer to that question.

anyway, how did you install the Shiretoko browser in the first place? Its not available from the default repos, I think. Can you please post the contents of your file /etc/apt/sources.list plus the name of the files in the directory /etc/apt/sources.list.d? 

Since you using shiretoko(test build for firefox), you could try installing this addon and see if it helps.
[https://addons.mozilla.org/en-US/firefox/addon/6543](https://addons.mozilla.org/en-US/firefox/addon/6543)


```
dee@Xena:~/Downloads$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090421.3)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ jaunty restricted main universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://getswiftfox.com/builds/debian unstable non-free #SwiftFox

dee@Xena:~/Downloads$ 

```

---

### Post by raktarok on 2009-12-05
The above file looks fine, maybe you added a ppa? 
post the output of ls /etc/apt/sources.list.d/.

---

### Post by Dee_Ann on 2009-12-05
> **raktarok said:**
> The above file looks fine, maybe you added a ppa? 
post the output of ls /etc/apt/sources.list.d/.

```

dee@Xena:~/Downloads$ ls /etc/apt/sources.list.d/.
zfs-fuse.list  zfs-fuse.list.save
dee@Xena:~/Downloads$ 

```

---

### Post by raktarok on 2009-12-05
```
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

```

This line may be the culprit. add a # before it (or use the software sources to disable the backports and the proposed repositories)
Then remove all firefox related packages and again reinstall it.

I don't know what to do if this doesn't work :(
Good luck!

---

### Post by fluffman86 on 2009-12-05
did you try my suggestion on the previous page?

---

### Post by kiwimonster on 2009-12-05
up

---

### Post by Dee_Ann on 2009-12-05
> **fluffman86 said:**
> You may have a problem with your settings somewhere. In firefox, backup your bookmarks by going to Bookmarks > Organize > Backup and save them to your Desktop.  Open your home folder, press ctrl+H to show hidden files, then rename .mozilla to .mozilla-backup.  

Now re-open firefox-3.5 and it will create a clean profile for you.  Now you can re-add your bookmarks and plugins.  Add *ONE PLUGIN AT A TIME* and if you start experiencing problems again, you'll know which one caused an error (maybe none).

Also, if some of your extensions won't load because that version of firefox isn't supported, you can usually get around that by typeing about:config in the address bar, press enter, then right-click > new > boolean > extensions.checkCompatibility > false.


I did that last night.  Only not one at a time.  I used febe to back up and restore.
Like I *must* save my cookies, passwords, history, bookmarks, etc.  Those are non-negotiable, they MUST stay.  Other stuff, I'm not too sure.
A lot of the addons, I really need.  Especially the ad blocking.  But I've uninstalled adblock plus because when it is installed, it is totally fouled up and makes firefox totally unusable.


What about the possibility that doing updates to the system broke something?

I get notices from update manager pretty often telling me I need to update things, I always click yes, do the updates.  Maybe one of them broke things?

---

### Post by raktarok on 2009-12-05
Did you try what I said in post #24? it may bring back the stable firefox.

Yes, you probably got the shiretoko update through update-manager. I really think it's coming from the backports, so disable that,remove firefox completely, update the software package list(sudo apt-get update) and then reinstall firefox. It should bring the stable release back.

---

### Post by Dee_Ann on 2009-12-05
> **raktarok said:**
> Did you try what I said in post #24? it may bring back the stable firefox.

Yes, you probably got the shiretoko update through update-manager. I really think it's coming from the backports, so disable that,remove firefox completely, update the software package list(sudo apt-get update) and then reinstall firefox. It should bring the stable release back.


I will do that shortly, I need to take care of some personal biz right now but prolly will get to trying that in like 30-45 minutes I hope.

I'm so totally frustrated with this.

And no, I do not want the firefox 3.0.x installed, it's even more useless that the broken 3.5.5 stuff.  I need something in-between.  Like 3.4

Sigh.......

BBL...

---

### Post by Surkow on 2009-12-05
Maybe a simple and fast solution for your problem. Just [download]("http://www.mozilla-europe.org/en/firefox/") a compressed file (firefox-3.5.5.tar.bz2 for example) from the Mozilla Firefox website. After downloading it decompress it in your home directory and start the firefox binary (maybe you need to make it executable first). After starting it, it will try to load all your original settings. Just remember that you need to change all launchers to the new location (from "firefox %u" to "home/#username/firefox/firefox %u").

---

### Post by Dee_Ann on 2009-12-05
ok, I'm on epiphany now :(

I went into synaptic, marked out that repository, did a *complete* uninstallation of ALL firefox items then went to my home dir and deleted the .mozilla dir.

When I go back into synaptic the ONLY options for firefox are

3.0.1.x  (sucks and is badly broken, period.  Not usable.)

3.1 which states it's a dummy that will install 3.5.5

I do not want 3.5.5  It does not work.  It's broken and I don't want it.  I want an OLDER version, like 3.4 or something.  No 3.0.x at all.  

So how can I now install something newer that 3.0.x but older than 3.5.5 ???

---

### Post by raktarok on 2009-12-05
Give the 3.5.5 one last chance. Earlier, when you downgraded to 3.5.5, you were still using shiretoko. This should be a different one, I think. Just do this :
```
sudo apt-get install firefox
```

If this doesn't work and you want the older version, try firefox's website. They should have binaries of the older version. Download it from there and place it somewhere in your home folder. Then change your launchers to point to the older version. You can still use your older profile, if you do this.

---

### Post by Dee_Ann on 2009-12-05
> **raktarok said:**
> Give the 3.5.5 one last chance. Earlier, when you downgraded to 3.5.5, you were still using shiretoko. This should be a different one, I think. Just do this :
```
sudo apt-get install firefox
```If this doesn't work and you want the older version, try firefox's website. They should have binaries of the older version. Download it from there and place it somewhere in your home folder. Then change your launchers to point to the older version. You can still use your older profile, if you do this.


But I don't know how to compile programs. Every time I try it it gets all fussy with me, says things are missing or broken and refuses to do anything.  I learned to leave things alone.  (Mostly)

---

### Post by HeadHunter00 on 2009-12-05
I can understand your problem. But, instead of downgrading firefox, download swiftfox from [getswiftfox.com]("http://getswiftfox.com/")
It is a polished version of firefox and you get to keep all the history and bookmarks from your old firefox

---

### Post by raktarok on 2009-12-05
What is the terminal output fot the above command? Please post it..

I find installing programs through the commandline much easier. Its not hard once you get the hang of it. Don't worry! :)

---

### Post by HeadHunter00 on 2009-12-05
> sudo gedit /etc/apt/sources.list
then add this line
> deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free

then
> sudo apt-get update
and then
> sudo apt-get install swiftfox-prescott

---

### Post by Dee_Ann on 2009-12-05
Ok, I reinstalled 3.5.5 (Grrrrrr!) and without touching anything else, I went to one of the problem sites and tried it.  It works.

So how do I make sure it doesn't break again?  That's been a MASSIVE pain in the backside all week.

I have to have my bookmarks, cookies, passwords & history back.
And I had a bunch of extensions installed too, too many to list.  I need them back too but now I'm afraid I'll break it again!

---

### Post by raktarok on 2009-12-05
First, congratulations for the success! :)

The main reason you were facing this problem was because you enabled the backports repository in your software sources. Shiretoko, the pre-release version of firefox came from these repos, and as the description below (taken from sources.list file) clearly states, software installed from there may cause problems. 

```
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

```

But you might need to enable backports to install some programs. What I would suggest you is enable the backports only when you need it, and at all other times, keep it disabled.

If you want to keep the backports on,then see what updates are being offered before you use the update-manager. You can also lock version of the package in synaptic, if you don't plan to upgrade firefox.(The option is in the package menu.) The best way to avoid this would however be the first option (disabling backports and sticking to the default sources)

Hope this helped!

---

### Post by fluffman86 on 2009-12-05
Wait, so you've downgraded firefox *AND* cleared your profile?  So right now firefox works, but you don't have your passwords, etc?

So then the problem isn't necessarily with the *VERSION* of firefox, it's with your PROFILE.  I've seen firefox screw up lots before, and it's always been a profile issue.  More than a few times I've seen problems absolutely gone by simply disabling all of the extensions and re-adding them one at a time.  AdBlock Plus is known not to play nice with some extensions.

Also, there is no such thing as firefox 3.4.  There is 3.0.* and 3.5.*

And once you've backed up your bookmarks, your passwords shouldn't be an issue, since you should either know them or have them recorded.  You can, however, go to Edit > Preferences > Security > Saved Passwords > Show Passwords an record them manually.  

Your cookies are regained by just visiting the site.  Nothing special about them.

---

