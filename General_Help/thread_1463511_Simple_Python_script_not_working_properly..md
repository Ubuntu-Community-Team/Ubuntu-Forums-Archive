---
title: "Simple Python script not working properly."
date: 2010-04-27
forum: General Help
---

### Post by anthony62490 on 2010-04-27
Trying to learn python. Going well, but I have run into a minor speed bump. I wrote a simple program to see if Python was set up correctly. Wouldn't you know it, the thing pops open and then closes again. I put raw input fields there to stop the program, but they didn't work. The program is:

```
x = raw_input("Please input your name: ")
print "Hello " + x + ". Good to meet you."
raw_input("Press Enter to exit")
```

And as for python, I have installed the following packages. The program was made in IDLE using Python2.6 I just started learning python a few days ago, so this may be a really small mistake.

```
idle		
idle-python2.6
python		
python-4suite-doc
python-4suite-xml
python-apport	
python-apt	
python-aptdaemon
python-aptdaemon-gtk
python-avahi	
python-brlapi	
python-bugbuddy	
python-cairo	
python-central	
python-chardet	
python-configglue
python-couchdb	
python-crypto	
python-cups	
python-cupshelpers
python-daap	
python-dbus	
python-debian	
python-desktopcouch
python-desktopcouch-records
python-eggtrayicon
python-evince	
python-evolution
python-feedparser
python-fstab	
python-gconf	
python-gda	
python-gdbm	
python-gdl	
python-gksu2	
python-glade2	
python-gmenu	
python-gnome2	
python-gnome2-desktop
python-gnome2-extras
python-gnomeapplet
python-gnomecanvas
python-gnomedesktop
python-gnomekeyring
python-gnomeprint
python-gnupginterface
python-gobject	
python-gpod	
python-gst0.10	
python-gtk2	
python-gtkhtml2	
python-gtkmozembed
python-gtksourceview
python-gtksourceview2
python-gtkspell	
python-gtop	
python-httplib2	
python-ibus	
python-imaging	
python-launchpad-integration
python-launchpadlib
python-lazr-restfulclient
python-lazr-uri	
python-libxml2	
python-louis	
python-lxml	
python-mediaprofiles
python-metacity	
python-minimal	
python-musicbrainz2
python-mutagen	
python-nautilusburn
python-newt	
python-notify	
python-numpy	
python-oauth	
python-openssl	
python-pam	
python-papyon	
python-pkg-resources
python-problem-report
python-protobuf	
python-pyatspi	
python-pyinotify
python-pyorbit	
python-rdflib	
python-renderpm	
python-reportlab
python-reportlab-accel
python-rsvg	
python-serial	
python-sexy	
python-simplejson
python-smbc	
python-software-properties
python-speechd	
python-support	
python-telepathy
python-tk	
python-totem-plparser
python-tunepimp	
python-twisted-bin
python-twisted-core
python-twisted-names
python-twisted-web
python-ubuntuone-client
python-ubuntuone-storageprotocol
python-uniconvertor
python-uno	
python-utidylib	
python-virtkey	
python-vte	
python-wadllib	
python-webkit	
python-wnck	
python-xapian	
python-xdg	
python-xkit	
python-zope.interface
python2.5	
python2.5-minimal
python2.6	
python2.6-minimal
```

---

### Post by splatterdash on 2010-04-27
> Wouldn't you know it, the thing pops open and then closes again. I put  raw input fields there to stop the program, but they didn't work.

Did you run it by clicking on the file in Nautilus then choosing execute? Or Did you do this in bash:

```
python yourscript.py
```

If you did the first one, don't forget to include:

```
#!/usr/bin/python
```

as the first line of your script.

---

