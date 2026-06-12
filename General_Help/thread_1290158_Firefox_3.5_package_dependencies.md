---
title: "Firefox 3.5 package dependencies"
date: 2009-10-13
forum: General Help
---

### Post by arch0njw on 2009-10-13
Bug reporting in Launchpad is down, so I thought I would toss this out to the community.  I am running Kubuntu 9.04 with KDE 4.3.2 installed.  I wanted to give Firefox 3.5 a try, and when I went to install it, I got a ridiculous amount of package dependencies.  Anyone know why?

```
The following NEW packages will be installed:                                                                 
  apturl docbook-xml esound-clients esound-common firefox-3.5 firefox-3.5-branding gamin gksu gnome-app-install
  gnome-icon-theme gnome-mime-data gnome-mount libaudiofile0 libbonoboui2-0 libbonoboui2-common libcairo-perl  
  libcanberra0 libesd-alsa0 libgail-common libgail18 libgamin0 libgksu2-0 libglade2-0 libglib-perl libgnome2-0 
  libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnomecanvas2-0                   
  libgnomecanvas2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra  
  libgtk2-perl libgtkhtml2-0 libgtop2-7 libgtop2-common liblaunchpad-integration1 libnotify1 libpolkit-gnome0  
  librsvg2-common libscrollkeeper0 libsexy2 libtdb1 libvte-common libvte9 libwnck-common libwnck22 libxres1    
  notification-daemon policykit-gnome python-cairo python-gconf python-glade2 python-gst0.10 python-gtk2       
  python-gtkhtml2 python-launchpad-integration python-pyorbit python-sexy python-vte scrollkeeper sgml-data    
  software-properties-gtk synaptic ubufox xulrunner-1.9.1
```IMO, that's a bit absurd.

---

### Post by Meow27 on 2009-10-13
[www.getswiftfox.com](www.getswiftfox.com)

its not perfect for some extensions, but it will do the job as it has for me.

---

### Post by sigurnjak on 2009-10-13
Did you try this :
sudo apt-get --no-install-recommends install firefox-3.5

---

### Post by arch0njw on 2009-10-13
> **Meow27 said:**
> [www.getswiftfox.com]("http://www.getswiftfox.com")

its not perfect for some extensions, but it will do the job as it has for me.

Interesting.  I might give that a try.  I don't use many extensions on the machine I'm presently on, and it's a netbook, so something optimized has a certain appeal.

> **sigurnjak said:**
> Did you try this :
sudo apt-get --no-install-recommends install firefox-3.5

I did not try that.  And that shortened the list considerably!

```
firefox-3.5 firefox-3.5-branding xulrunner-1.9.1
```

Thank you to both of you.

---

### Post by arch0njw on 2009-10-14
So I am running Firefox 3.5 now nicely having used the --no-install-recommends switch.  I am also running swiftfox (presently writing this in said), but I see little performance difference.  Not sure what the benefit is at this point of using SF.

---

