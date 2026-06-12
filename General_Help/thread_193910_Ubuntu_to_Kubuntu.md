---
title: "Ubuntu to Kubuntu"
date: 2006-06-10
forum: General Help
---

### Post by Cable on 2006-06-10
I'm thinking about reinstalling and moving to Kubuntu.  If I do decide to do this, what should I do in preparation?  I currently have a dual boot with WinXP Pro and Ubuntu.  Would I be able to just reinstall on my Ubuntu partition and let it install GRUB again and it'll work fine, or will I have to do something else?  My /home directory is on it's own partition, so I don't need to worry about anything there.  Or if I should worry about something with my /home partition, tell me.  I'm assuming KDE works the same way as GNOME when it comes to /home.   If you'd recommend *not* moving to KDE, tell me.  All the hardware that works with GNOME works with KDE as well, right?  I'm assuming so, since it's probably not the desktop environment that determines that.  Anyway, let me know.

---

### Post by skymt on 2006-06-10
There's no reason to re-install. Just install kubuntu-desktop in Synaptic.

---

### Post by FredSambo on 2006-06-10
or

```
sudo apt-get install kubuntu-desktop
```

---

### Post by Cable on 2006-06-10
Is that what would enable me to choose between GNOME or KDE before I log in?  I've seen some people say install kubuntu-desktop, and I've seen others say install kdm.  What's the difference?

---

### Post by FredSambo on 2006-06-10
yep, after you install kubuntu-desktop, log off and select KDE for your next session at the log on screen.  it will then ask you if you'd like to make KDE your default desktop environment, if you choose yes, the next time you log on you'll experience the blue kubuntu login screen, and it will log on to KDE by default.  

good luck!

---

### Post by Cable on 2006-06-10
Will having GNOME and KDE installed take up unnecessary amounts of space on my hdd?  I guess it seems like it may take up a decent amount of room to me...using 2 desktop environments at the same time...

---

### Post by FredSambo on 2006-06-10
how much hdd space do you have?

KDE is kind of memory (RAM) intensive due to all the eye candy, so how much RAM do you have?

---

### Post by FredSambo on 2006-06-10
you should go ahead and give it a shot and if the performance is sub-par you can always remove KDE via:

```
sudo apt-get remove kubuntu-desktop
```

---

### Post by Cable on 2006-06-10
I have 1GB of RAM.

---

### Post by FredSambo on 2006-06-10
you'll be fine, i say go for it!

---

### Post by Cable on 2006-06-10
Another thing...if I do decide to remove KDE, or stick with KDE and remove GNOME...how would I remove all the apps that synaptic downloaded that KDE needed, since GNOME doesn't use those?  And vice versa for removing GNOME.

---

### Post by CronoDekar on 2006-06-10
One sec, channeling the spirit of aysiu:

[QUOTE=Spirit of aysiu (in a spooky voice)]
Uuuuuuse:

sudo aptitude install kubuntu-desktop

rather than apt-ggggggget.  If you insaaaaall it with aaaaaptitude it is eaaasier to remoooove laaaaater if you do not waaaaant it, with:

sudo aptitude remove kubuntu-desktop
[/QUOTE]

Spooky!  Probably a version which wouldn't cost me invoking the Dark Magicks thereby damning my eternal soul would have just been to point you here:

[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)

And I haven't installed kubuntu myself, so I don't know how much space it takes up.

---

### Post by marcog on 2006-06-10
I recently went ahead I installed kubuntu-desktop along with ubuntu and it used up about 400-500MB.

---

### Post by FredSambo on 2006-06-10
yeah, i like aptitude as well (especiall in the terminal) but i don't buy the 'easier to uninstall' argument.

---

### Post by CronoDekar on 2006-06-10
[QUOTE=FredSambo]yeah, i like aptitude as well (especiall in the terminal) but i don't buy the 'easier to uninstall' argument.[/QUOTE]

I don't know myself, that's just what I always hear aysiu say!

---

### Post by FredSambo on 2006-06-10
[QUOTE=FredSambo]yeah, i like aptitude as well (especiall in the terminal) but i don't buy the 'easier to uninstall' argument.[/QUOTE]

but i do like the way aptitude logs everything in /var/log/aptitude.  apt-get doesn't log anything as far as i can tell.

---

### Post by FredSambo on 2006-06-10
[QUOTE=CronoDekar]I don't know myself, that's just what I always hear aysiu say![/QUOTE]

yeah, i have read that aptitude deals with dependencies better during uninstall, although as far as i can tell, both apt-get and aptitude are similar.

i am no expert though.

---

### Post by Ramses de Norre on 2006-06-10
Aptitude removes dependencies when the package by which they were installed is removed (and no other installed packages depend on them). That's why they say aptitude is easier for removing. I'd also use the purge command instead of remove if you're not planning to reinstall, purge removes the config files too.

---

### Post by FredSambo on 2006-06-10
> I'd also use the purge command instead of remove...

word.

cheers ramses, hope all is well in leuven!

---

### Post by Cable on 2006-06-10
How does one use the purge command?  Just so I know...

---

### Post by FredSambo on 2006-06-10
sudo apt-get --purge remove kubuntu-desktop

right?

---

### Post by Ramses de Norre on 2006-06-10
sudo aptitude purge package_name

@FredSambo: I don't really get your post, but yes all is fine;)

---

### Post by FredSambo on 2006-06-10
oops, like i said, i'm no expert.  :p

---

### Post by Ramses de Norre on 2006-06-10
That wont do anything usefull, kubuntu-desktop is a metapackage which doesn't content anything but has a lot of packages as dependency.
Thus removing it by apt-get wont do anything but removing it by aptitude will.

EDIT: hey you edited while I was replying =p and you can use your command too but you wont have the advantages of aptitude.

---

### Post by flankker on 2006-06-10
[QUOTE=Ramses de Norre]That wont do anything usefull, kubuntu-desktop is a metapackage which doesn't content anything but has a lot of packages as dependency.
Thus removing it by apt-get wont do anything but removing it by aptitude will.[/QUOTE]

will the same work for removing ubuntu?

---

### Post by Ramses de Norre on 2006-06-10
As long as it's installed with aptitude, I'm not sure about packages installed by the installer though..

---

### Post by FredSambo on 2006-06-10
> EDIT: hey you edited while I was replying =p and you can use your command too but you wont have the advantages of aptitude.

:p

---

### Post by FredSambo on 2006-06-10
thanks for the insight ramses.

---

### Post by aysiu on 2006-06-10
If you didn't install with *aptitude*, you're only hopes of returning to pure Gnome or pure XFCE are these:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by FredSambo on 2006-06-10
i was waiting for you to reply.

hi, it is a pleasure to meet you, i am fred.  :)

---

### Post by aysiu on 2006-06-10
Pleasure to meet you, too.

---

### Post by exclipy on 2006-06-10
Here's the command to get rid of ubuntu-desktop and leave Kubuntu:

```
sudo apt-get remove alacarte app-install-data-commercial at-spi bittorrent bluez-pin brltty-x11 bug-buddy contact-lookup-applet dbus-1-utils deskbar-applet ekiga eog esound evince evolution evolution-data-server evolution-exchange evolution-plugins evolution-webcal festival festlex-cmu festlex-poslex festvox-kallpc16k file-roller firefox-gnome-support fping gaim gaim-data gcalctool gconf-editor gdb gdebi gdm gedit gedit-common gimp-print gimp-python gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-btdownload gnome-cups-manager gnome-doc-utils gnome-games gnome-mag gnome-media gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-utils gnome-volume-manager gnome2-user-guide gnopernicus gok gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtk2-engines-clearlooks gtk2-engines-crux gtk2-engines-highcontrast gtk2-engines-industrial gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice gtk2-engines-ubuntulooks gtkhtml3.8 gucharmap hal-device-manager hwdb-client iso-codes language-selector libatspi1.0-0 libbeagle0 libbtctl2 libcompfaceg1 libdjvulibre15 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1 libedataserverui1.2-6 libeel2-2 libeel2-data libesd-alsa0 libestools1.2 libexchange-storage1.2-1 libgail-gnome-module libgda2-3 libgda2-common libgdl-1-0 libgdl-1-common libglew1 libglib2.0-data libgnome-mag2 libgnome-pilot2 libgnome-speech3 libgnome2-canvas-perl libgnome2-perl libgnome2-vfs-perl libgnomebt0 libgnomecups1.0-1 libgnomecupsui1.0-1c2a libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomevfs2-bin libgnomevfs2-extra libgtkhtml3.8-15 libgtksourceview-common libgtksourceview1.0-0 libgtkspell0 libgtop2-7 libgucharmap4 libgutenprintui2-1 libkpathsea4 liblpint-bonobo0 libnautilus-burn3 libnotify1 libopal-2.2.0 libpanel-applet2-0 libpisync0 libpoppler1-glib libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libsexy2 libtotem-plparser1 libvte-common libvte4 metacity nautilus nautilus-cd-burner nautilus-data nautilus-sendto notification-daemon openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk python-gnome2-desktop python-gnome2-extras python-gst0.10 python-gtk2 python-launchpad-integration python-libxml2 python-vte python2.4-gnome2-desktop python2.4-gnome2-extras rhythmbox rss-glx scim scim-gtk2-immodule scim-modules-socket screensaver-default-images serpentine sound-juicer ssh-askpass-gnome synaptic system-tools-backends tangerine-icon-theme tango-icon-theme tango-icon-theme-common totem totem-gstreamer tsclient ttf-arphic-ukai ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds unattended-upgrades update-manager update-notifier vino vnc-common xsane xsane-common xscreensaver-data xscreensaver-gl xsltproc xvncviewer yelp
```

At least, that's the list of packages that were installed when I installed ubuntu-desktop on top of my Kubuntu.

---

### Post by aysiu on 2006-06-10
It should be the same list of packages as is on this page:
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

That I got from "installing" Ubuntu on top of a Kubuntu Dapper live CD.

---

### Post by FredSambo on 2006-06-10
just beware of taking such advise if you have a web server set up.  :)

---

### Post by aysiu on 2006-06-10
[QUOTE=FredSambo]just beware of taking such advise if you have a web server set up.  :)[/QUOTE]
Does that command remove Apache or something? I'm just curious as to why you made that statement.

---

### Post by FredSambo on 2006-06-10
yes, it does.

---

### Post by FredSambo on 2006-06-10
but pure is pure right?

---

### Post by aysiu on 2006-06-10
Interesting. I didn't know that.

---

### Post by FredSambo on 2006-06-10
you are welcome.  :)

---

### Post by Cable on 2006-06-11
Okay, so I installed the kubuntu-desktop package.  Installed perfectly, and I can log in using KDE just fine.  But, say I'm in GNOME, and decide to log in using KDE.  So, I log out, change the session, type in my info, and hit enter.  The screen then goes to change resolution to show the desktop, and remains black.  Nothing happens.  So I have to reboot to get it working okay again.  The same happens if I'm logged in to KDE and decide to switch to GNOME.  **EDIT:  This actually happens no matter what now.  If I'm in GNOME, log out, then attempt to log back in to GNOME, it just hangs as well.**

Also, sometimes the three buttons on the login screen aren't even "clickable."  I don't know if this has anything to do with installing KDE (I'm pretty sure it did this before too).  Would this be due to the login screen I have chosen, or something else?

Last, installing KDE changed the bootup screen from the brownish Ubuntu one to the blue Kubuntu one.  If I wanted to do so, how would I change it back?

---

### Post by aysiu on 2006-06-11
Wow. I've never heard of that problem before.

I do know, though, that you don't have to reboot. You can just press Control-Alt-Backspace to get back to the login screen.

---

### Post by Cable on 2006-06-11
So...no idea as to what I should do to get it to quit doing that then?

---

### Post by aysiu on 2006-06-11
To be honest, I haven't a clue.

If you're able to, give it 24 hours, though. Someone else more knowledgeable than I may step in and have a good solution.

---

### Post by throbi on 2006-06-11
[QUOTE=Cable]Is that what would enable me to choose between GNOME or KDE before I log in? [/QUOTE]

**gdmflexiserver** is the word for you. Type it into a command line or launch it with ALT+F2. It launches a new X server, you can chose the session (Gnome or KDE).  This way you can have Gnome & KDE running at the same time :)  Use CTRL+ALT+F7, CTRL+ALT+F8 to swap them.  

This allows you to have multiple users loged in at the same time, too. For security reasons you might be required to enter your password to unblock the inactive session. 

You can have more than two active sessions/users at the same time.   CTRL+ALT+F7, CTRL+ALT+F8, CTRL+ALT+F9... are the keys for them.

Right now both Gnome & KDE are running on my Athlon 2200+ with 512 MB RAM and both of them are happy.  I have only installed the **kde** package (+dependencies) from Synaptic.

 Plus: yesterday I upgraded to Drapper and the switching between Gnome and KDE sessions got much-much faster, almost instant (just like many other things including booting - but that's another story).

---

### Post by flankker on 2006-06-11
[QUOTE=throbi]**gdmflexiserver** is the word for you. Type it into a command line or launch it with ALT+F2. It launches a new X server, you can chose the session (Gnome or KDE).  This way you can have Gnome & KDE running at the same time :)  Use ALT+F7, ALT+F8 to swap them.  

This allows you to have multiple users loged in at the same time, too. For security reasons you might be required to enter your password to unblock the inactive session. 

You can have more than two active sessions/users at the same time.   ALT+F7, ALT+F8, ALT+F9... are the keys for them.

Right now both Gnome & KDE are running on my Athlon 2200+ with 512 MB RAM and both of them are happy.  I have only installed the **kde** package (+dependencies) from Synaptic.

 Plus: yesterday I upgraded to Drapper and the switching between Gnome and KDE sessions got much-much faster, almost instant (just like many other things including booting - but that's another story).[/QUOTE]

would this work for xgl/cmpiz too?

---

### Post by irv on 2006-06-11
After reading through this thread I would like to make a few comments. First, I have both gnome and KDE on my main desktop. Second, I work in gnome most of the time, but on occasion I will switch to KDE and play around. (This is my choice). And that is what it is all about "choice". I have three PC's running in my house all using Ubuntu 6.06. One server and two desktop. When updates come I just update all three PC's from my main Desktop via VNC. It works great when all are in gnome. And all would work great if all were in KDE but seeing I keep my server and one desktop on gnome I need to make sure I am in gnome when I use VNC or I have problems. I can VNC into the gnome desktop from KDE but can't get out and some of the screen draws get funky on me.

This is all I wanted to add.

---

### Post by Cable on 2006-06-11
It just so happens that the login screen buttons becoming "unclickable" happens only when I'm using gdm, not kdm.  With kdm, it works perfectly.  So, something must be screwy with gdm...any ideas?

---

### Post by georgevn on 2006-06-12
what is the differences between installing kubuntu-desktop and kde (on top of ubuntu, of course)? kde and kde-core are standard packages for KDE environment, aren't they?
if i have installed kubuntu-desktop on my ubuntu box and now want to switch completely to kubuntu, what should i do?

---

### Post by aysiu on 2006-06-12
kubuntu-desktop, kde, kdebase, and kde-core are just different metapackages for KDE. They each contain their own flavors of KDE (with different sets of default programs).

In order from fewer packages to more packages:
kdebase
kde-core
kubuntu-desktop
kde

If you want to get rid of Ubuntu and keep Kubuntu, go here:
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by Cable on 2006-06-14
Is it safe to update all the KDE stuff through the **Update Mananger **popup?  I installed kde-desktop via aptitude due to aysiu's advice about it being easier to remove later on if I so desire.  Should I just go ahead and allow that to update everything or should I update some other way?

---

### Post by Fred Doolie on 2006-06-14
I have all four desktops (Ubuntu, Kubuntu, Xubuntu and Edubuntu) installed and switch between them at will. Why? Just for fun. I have 80 gigs of space so why not? Sometimes I want to have eyecandy (K) and sometimes I want to get serious (U) and sometimes I want to be childish (E) and sometimes I just...uh....well I don't actually use Xubuntu but it's there just in case.

OK, on the serious side, most of the good KDE stuff  like KB3 and KDar and the Edubuntu stuff is accessible through regular Ubuntu Gnome so it's all good. I use the multiple systems to show off Ubuntu Linux.

"You want something like Winblows?" - Switches to Kubuntu
"You want small and fast?" - Switches to Xubuntu
"You want simpler but very useful?" - Switches to Ubuntu
"Something for the kids?" - Switches to Edubuntu.

Correct me if I'm wrong but all I'm actually "losing" is HDD space, right?

---

### Post by Cable on 2006-06-14
Nobody has an answer to my question at the end of page 5?  aysiu, you around??  :-P

---

### Post by aysiu on 2006-06-14
[QUOTE=Cable]Is it safe to update all the KDE stuff through the **Update Mananger **popup?  I installed kde-desktop via aptitude due to aysiu's advice about it being easier to remove later on if I so desire.  Should I just go ahead and allow that to update everything or should I update some other way?[/QUOTE]
At this point, now that Dapper is released officially, there won't be any new packages or removed packages--just newer versions of the same packages (for security purposes). Go ahead and update.

---

### Post by flankker on 2006-06-16
hi, i installed kubuntu-desktop so now i have both ubuntu and kubuntu.

my question is should i change anything in my sources.list to make sure i get kubuntu updates too or will this happen already?

thanx.

---

### Post by DougC on 2006-06-16
Flanker, all the packages for all the desktops are in the same repo's so you don't have to change a thing.

---

### Post by flankker on 2006-06-16
[QUOTE=DougC]Flanker, all the packages for all the desktops are in the same repo's so you don't have to change a thing.[/QUOTE]

thanx for the answer :)

---

