---
title: "converting a dual boot system"
date: 2006-03-10
forum: General Help
---

### Post by sloth boy on 2006-03-10
hi all

i currently have my system dual booting Ubuntu (gnome) and XP pro. grub dose it's thing at boot letting me choose to OS o choice.
i have a few issues with Gnome and am wanting to install Kubuntu insted of it.
my main issue with installing Kubuntu is, will it stuff with the grub boot loder??

i have three HDD in my system. two of which are NTFS (soon to be changed) 
and both OS's live on there own HDD's 

sorry i a little n00b, but i am trying......   ;)

thanks 
jord

---

### Post by nrwilk on 2006-03-10
Kubuntu is the exact same system as ubuntu except that it uses the K Display Environment (KDE) instead of Gnome.  You can use any bootloader which works with a ubuntu install will also work on a Kubuntu install.

Let us know if you need any more help with the install.

Good luck, hope it goes well!  :)

---

### Post by Dakaru on 2006-03-10
and why not just install KDE using Synaptic or somthing?

---

### Post by sloth boy on 2006-03-10
thanks for that super quick help!

i wasnt to keen on downloding all of the KDE desktop (this internet conection is only 56k......) 
as i allready have the Kubuntu install iso on cd.  

thanks once again,
jord

---

### Post by Jucato on 2006-03-10
alternatively, I think you could use that Kubunt install CD (once you burned the ISO) as a repository to install kde-core or kubuntu-desktop. 

However, I have to tell you that you might need to update KDE to 3.5.1 anyway (the install comes with KDE 3.4.3 only) as this update fixes many bugs, especially regarding Administrative Mode.

---

### Post by nrwilk on 2006-03-10
[QUOTE=Dakaru]and why not just install KDE using Synaptic or somthing?[/QUOTE]
True, I assumed that he wanted to wipe and reinstall, but the may not be the case.

@sloth boy, if you just want to remove Gnome and install KDE on your existing install, then do the following:

1. Install KDE:

```
sudo apt-get install kubuntu-desktop
```

2. Reboot.  When the login screen appears, click on "System Menu" and select KDE instead of Gnome.  Log in.

[COLOR="Red"]Note: at this point, you CAN leave Gnome installed if you have enough space and if you want to use both, or if you want to use KDE while you try to fix Gnome.  It's up to you.  It's fine to have multiple display environments installed on a system, in fact many distros install by default with both KDE and Gnome.  If you're sure you want to remove Gnome, continue.[/COLOR]

3. Open up Konsole, KDE's terminal app.  It should be under the "System" sub-menu in the K-menu (at the lower left).  Issue the following command all together as one.  I know it's big, but copy and paste it all.  (you can paste into Konsole by hitting <shift><insert>.  <ctrl><v> won't work with most consoles because it has an alternate use which has been around since before computers could cut and paste text.):

```
sudo apt-get remove bittorrent bluez-pin bug-buddy capplets-data contact-lookup-applet dbus-1-utils desktop-file-utils eog esound evince evolution evolution-data-server evolution-exchange evolution-plugins evolution-webcal file-roller firefox firefox-gnome-support fping gaim gaim-data gcalctool gconf-editor gdb gdm gedit gedit-common gimp gimp-data gimp-python gksu gnome-about gnome-app-install gnome-applets gnome-applets-data gnome-btdownload gnome-control-center gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-media gnome-menus gnome-mime-data gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-utils gnome-volume-manager gnome2-user-guide gnomemeeting gstreamer0.8-esd gstreamer0.8-gnomevfs gthumb gtk2-engines-clearlooks gtk2-engines-crux gtk2-engines-industrial gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice gtkhtml3.8 gucharmap guile-1.6-libs hal-device-manager hwdb-client language-selector launchpad-integration libaa1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libcamel1.2-6 libcompfaceg1 libcroco3 libdjvulibre15 libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1 libedataserver1.2-4 libedataserverui1.2-6 libeel2-2 libeel2-data libegroupwise1.2-8 libesd-alsa0 libexchange-storage1.2-0 libgail-common libgail17 libgda2-3 libgda2-common libgimp2.0 libgksu1.2-0 libgksuui1.0-0 libglade2-0 libgle3 libglib-perl libglib2.0-data libgnome-desktop-2 libgnome-keyring0 libgnome-menu2 libgnome-pilot2 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomecupsui1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgsf-1 libgtk2-perl libgtkhtml2-0 libgtkhtml3.8-15 libgtksourceview-common libgtksourceview1.0-0 libgtkspell0 libgtop2-5 libgucharmap4 libguile-ltdl-1 libkpathsea3 liblaunchpad-integration0 liblircclient0 liblpint-bonobo0 libmetacity0 libnautilus-burn2 libnautilus-extension1 libnotify0 libopenal0 libopenh323-1.15.3c2 libpanel-applet2-0 libpisync0 libpoppler0c2-glib libpt-1.8.3c2 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libqthreads-12 librsvg2-2 librsvg2-common libsmpeg0c2 libsoup2.2-8 libtotem-plparser0 libvte-common libvte4 libwmf0.2-7 libwnck-common libwnck18 libxklavier10 libxml2-utils libxres1 metacity nautilus nautilus-cd-burner nautilus-data nautilus-sendto notification-daemon openoffice.org2-evolution openoffice.org2-gnome python-glade2 python-gmenu python-gnome2 python-gnome2-extras python-gst python-gtk2 python-launchpad-integration python2.4-cairo python2.4-glade2 python2.4-gnome2 python2.4-gnome2-extras python2.4-gtk2 rdesktop rhythmbox rss-glx serpentine shared-mime-info smeg sound-juicer ssh-askpass-gnome synaptic system-tools-backends totem totem-gstreamer tsclient ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds update-manager update-notifier vino vnc-common whois xchat xchat-common xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl xsltproc xvncviewer yelp zenity

```

You're done!

Don't worry that the remove command has a bunch of stuff that you might want in it, some of that stuff will be installed by kubuntu-desktop.  Then you can reinstall other things that Kubuntu may not install by default, like firefox, with this command:
```

sudo apt-get install <packagename>

```

Have fun with KDE! :D

P.S.  The remove command is from Aysiu's howto located at this thread: [http://ubuntuforums.org/showthread.php?t=96046](http://ubuntuforums.org/showthread.php?t=96046)
If you find that the command works well, it would be nice to post a reply there letting Aysiu know that his method worked well for you.  Only a couple have so far.

Again, good luck!

---

### Post by sloth boy on 2006-03-11
hey all again,

Im happy to say that i have got Kubuntu (KDE) installed and up and running, i opted to install it fully overtop of Ubuntu as im not to fond of the Gnome desktop.

all i did was boot up Kubuntu install cd and followed that through. as i found out the installer is the same as the one for Ubuntu so it just re did the grub install even though that probebly wouldn't have been needed....

well thanks once again to all of you for you help!
Im off to find the latest Nvidia drivers....   just carnt live at 640X480....  ;)

jord,

---

