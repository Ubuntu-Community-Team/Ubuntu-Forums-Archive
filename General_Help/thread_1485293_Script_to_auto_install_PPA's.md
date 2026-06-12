---
title: "Script to auto install PPA's"
date: 2010-05-16
forum: General Help
---

### Post by held7over on 2010-05-16
Ubuntu 10.04

I am working on a bash script to auto install PPA's in /etc/apt/sources.list. Here is a sample:

```

echo
echo "Empathy needs Telepathy  (geolocation and audio/video chat for MSN)"
echo
sudo add-apt-repository ppa:telepathy/ppa
echo

echo "Gwibber updates"
sudo add-apt-repository ppa:gwibber-team/ppa
echo

echo "Gnome Extra Themes"
sudo add-apt-repository ppa:bisigi/ppa 
echo

echo "Web Browsing"
echo
sudo add-apt-repository ppa:webkit-team/epiphany
sudo add-apt-repository ppa:webkit-team/ppa
sudo add-apt-repository ppa:chromium-daily/beta
echo 

```

Does this get the job done, or is there some other file(s) that need to be addressed yet?

---

### Post by sisco311 on 2010-05-17
Yep, that should do the trick. Before you start downloading/upgrading from the new repositories, you have to resynchronize the package index files:
```
sudo apt-get update
```

---

### Post by held7over on 2010-05-17
Thanks sisco311!

I have noticed that when "sudo apt-get update" runs, it mainly displays 3 types of output: Get, Hit, Ign 

Does Ign mean Ignore?  And is this bad....meaning something needs my attention?

---

### Post by SaintDanBert on 2010-05-17
I have sought, without success, for an article that lists "the top NN repositories to add to your *buntu package manager".  Does anyone know of such a list or article?

There are dozens of lists for "top NN" desktop tweaks, brower add-on, openoffice extensions, media players, media burners, yada yada.  Why don't we have a set of repository addition files to load into our
/etc/apt/sources.list.d folders?

Cheers,
~~~ 0;-Dan

---

### Post by drewsus on 2010-05-17
well this is my list of PPAs (and showing the package(s) to install):

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu

sudo add-apt-repository ppa:deluge-team/ppa #deluge
sudo add-apt-repository ppa:dockbar-main/ppa #gnome-dockbar-applet gnome-dockbarx-applet dockbarx dockbar
sudo add-apt-repository ppa:tualatrix/ppa #ubuntu-tweak
sudo add-apt-repository ppa:team-xbmc-svn/ppa #xbmc
sudo add-apt-repository ppa:docky-core/ppa #docky
sudo add-apt-repository ppa:banshee-team/ppa #banshee
sudo add-apt-repository ppa:bjfs/ppa # emesene ##weekly emesene svn
sudo add-apt-repository ppa:awn-testing/ppa #avant-window-navigator-trunk 
sudo add-apt-repository ppa:jonoomph/openshot-edge #openshot video editor
sudo add-apt-repository ppa:globalmenu-team/ppa #gnome-globalmenu
sudo add-apt-repository ppa:gnome-media-player-development/development #gnome-media-player
sudo add-apt-repository ppa:nuovodna/nuovodna-stuff #clementine (Lucid only)
sudo add-apt-repository ppa:eugenesan/ppa #googsystray
sudo add-apt-repository ppa:chromium-daily/beta #chromium-browser
sudo add-apt-repository ppa:pmcenery/ppa #for ipod touch and iphone support
sudo add-apt-repository ppa:deja-dup-team/ppa #deja-dup duplicity
sudo add-apt-repository ppa:xsisqox/ppa #viewnior
sudo add-apt-repository ppa:muravjov-il/ppa #bombono-dvd
sudo add-apt-repository ppa:gloobus-dev/covergloobus #covergloobus
sudo add-apt-repository ppa:gcstar/ppa #gcstar
sudo add-apt-repository ppa:elementaryart #elementary-theme elementary-icon-theme
sudo add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa  ##update and upgrade will do it followed by "nautilus -q". Nautilus Elementary
sudo add-apt-repository "deb http://linux.getdropbox.com/ubuntu karmic main" #dropbox PPA
sudo add-apt-repository "deb-src http://linux.getdropbox.com/ubuntu karmic main" #dropbox src-PPA
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner" #lucids partner repo
	##sun-java6-jre sun-java6-jdk sun-java6-plugin sun-java6-fonts
sudo add-apt-repository ppa:b-sides/ppa
```

---

### Post by held7over on 2010-05-17
I agree with you SaintDanBert.  It would be really handy right now to have such a thing. 

I am sure Ubuntu probably shouldn't directly do this. But, it would be nice if a third party would create such a list and let the users rate each site, etc.

I have seen warnings about untrustworthy software or repositories, but I have no idea who they are or if they still exist.

Not all the PPA's I found were active, but I found most of them from:

[http://blog.thesilentnumber.me/](http://blog.thesilentnumber.me/)

If you know of any good sites, I'd sure appreciate their URLs.

---

### Post by SaintDanBert on 2010-05-20
> **drewsus said:**
> well this is my list of PPAs (and showing the package(s) to install):
```

sudo add-apt-repository ...

```


[color=green]**Thanks for sharing your details with the community.**[/color] Too often folks that have something working seem reluctant to share enough details so that others might follow in their steps. Rather, they offer morsels seemingly in hopes that their readers will discover success. I often wonder if there isn't a touch of vendetta: "I had to tinker for hours and search out details. Here is a crumb for you to tinker with. Keep searching and tinkering."

[highlight]Other readers:[/highlight]  If you have a list of repositories that you make certain to add following every fresh install, **consider sharing** your favorites here.

Sadly, I'm running Jaunty (v9.04) for a variety of reasons and do not have access to **add-apt-repository** as of yet. I think that I can translate from your commands to the details I need to edit files in /etc/apt/sources.list.d.

Cheers,
~~~ 0;-Dan

---

### Post by dino99 on 2010-05-20
dont forget that lot of ppas are not regularly updated and are not highly trusted: so be ready to fight with dependencies, conflicts and other nice mess :confused:

---

### Post by held7over on 2010-05-20
So, dino99, are you saying you think it is better not to get involved with PPA's at this time?  

I am setting several computers up for friends who don't know much about their systems. Maybe it would be better not to include PPA's on their systems?

---

### Post by drewsus on 2010-05-20
All the PPAs that I listed I have used for numerous installs on numerous systems for friends family and others. 
All of them seem to be updated as regularly as needed and all I think can be trusted. Most are just the official PPAs of relevant apps. 
I will say that you are perfectly safe to use the ones I provided. But, if you just search on google for the part after "sudo add-apt-repository" you can see all the listed packages and when they were last updated, etc. 
PPAs are so much better than just downloading and installing random .deb files. I'd say its less secure to NOT opt for a way to have them get updated regularly. 

As for **SaintDanBert** I am more than happy to share my hard work! I actually have a fairly long script that I use when I install a new system, although it needs some polishing. But I would be happy to share that as well. Uses zenity to add a GUI flare to it too ;)

edit: when I say polish its just in style, not efficiency

---

### Post by held7over on 2010-05-21
drewsus. I'd really appreciate seeing your script and how you did things!

---

### Post by drewsus on 2010-05-21
Alright, I'll brush it up while I organize my TV Shows and Movies and post it when its all good and sexy ;)

---

