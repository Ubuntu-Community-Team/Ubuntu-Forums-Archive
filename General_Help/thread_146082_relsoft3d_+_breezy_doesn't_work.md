---
title: "relsoft3d + breezy doesn't work?"
date: 2006-03-17
forum: General Help
---

### Post by roeleboel on 2006-03-17
Hello,

I tried today to install realsoft3d but it doesn't work.

First it didn't find libXm.so.3, it wasn't in /usr/lib but in /usr/X11R6/lib so I made a symbolic link:

ln -s /usr/X11R6/lib/libXm.so.3 /usr/lib/libXm.so.3

That was fixed, but when I tried to fire up realsoft3d now I get this error:

libaviplay-0.7.so.0: kan gedeeld objektbestand niet openen: Onbekend bestand of map
libnvidia-tls.so.1: kan TLS-gegevens niet verwerken
Xlib:  extension "DOUBLE-BUFFER" missing on display ":0.0".
/usr/bin/realsoft3d: line 52: 11149 Segmentatie fout        $INSTALLDIR/bin/Realsoft3D -noguiload -db $tmpres -file "$INSTALLDIR/startup.r3d" -plugins "$INSTALLDIR/plugins" $*

It is in dutch, but what there is written is this:

libaviplay-0.7.so.0: Unknown file or directory
libnvidia-tls.so.1: can't handle TLS-data

The rest You can understand.

I don't really understand this error, it's a little bit "vague" for me.
Can somebody help me to get this to work?

Thanks.

FYI: I have an nvidia card with the Ubuntu nvidia-glx package installed.

---

### Post by capalbo on 2006-04-24
Here are a couple of things I did to make realsoft3D work in Ubuntu/Kubuntu 5.10:

In the file /etc/X11/xorg.conf, in the Section "Module" I added a line:
     Load     "dbe"
That adds the double buffer extensions.

I made a new file, /etc/ld.so.conf and put these lines in it:
/usr/X11R6/lib
/usr/lib

That tells the loader where to find the linked libs, I believe.  I had to restart KDE for these changes to take effect.  (While there's probably some better way to apply these changes, I didn't know how, so, honestly, I just rebooted.)

The program looked for somelib.so.5 and I had somelib.so.6 installed.  I found the other one in Adept and installed it.  (This was also on the Linux Forum DVD, if that's where you got realsoft3D.)

I found openMotif libs in Adept as well, and installed them.  (I think this was also on the DVD)

I found the aviplay package in Adept and installed it.

I think that's pretty much it.  Hope this helps!

---

