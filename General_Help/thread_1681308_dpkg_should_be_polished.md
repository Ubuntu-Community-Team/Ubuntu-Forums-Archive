---
title: "dpkg should be polished?"
date: 2011-02-04
forum: General Help
---

### Post by HotForLinux on 2011-02-04
```
**$dpkg -l php-pear php-pear**
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                  Version               Description
+++-=====================-=====================-==========================================================
ii  php-pear              5.2.4-2ubuntu5.14     PEAR - PHP Extension and Application Repository
No packages found matching php-pear.
```

and.... more...

```
**$ dpkg -l php-pear php-pear php-pear php-pear**
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                            Version                         Description
+++-===============================-===============================-==============================================================================
ii  php-pear                        5.2.4-2ubuntu5.14               PEAR - PHP Extension and Application Repository
No packages found matching php-pear.
No packages found matching php-pear.
No packages found matching php-pear.
```



Hahaha....  That's funny!

---

### Post by sdennie on 2011-02-04
I didn't even know dpkg -l accepted arguments.  I've always done "dpkg -l | grep foo".  But, I have a feeling your extra package names are not considered search arguments and are instead considered .deb files that should be operated on.  It's not surprising that you'd get those messages if that .deb doesn't exist.

---

### Post by HotForLinux on 2011-02-04
> **sdennie said:**
> I didn't even know dpkg -l accepted arguments.  I've always done "dpkg -l | grep foo".  But, I have a feeling your extra package names are not considered search arguments and are instead considered .deb files that should be operated on.  It's not surprising that you'd get those messages if that .deb doesn't exist.

C'mon!
Foo? ... that's very little
It is used with arguments hundreads of times in this forum to explain many important things about packages 


```
**$ dpkg -l axiom-databases mythtv-database alsa-utils acpi-support nmap gimp**
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                        Version                     Description
+++-===========================-===========================-======================================================================
ii  acpi-support                0.109-0hardy2               a collection of useful events for acpi
ii  alsa-utils                  1.0.15-3ubuntu2             ALSA utilities
ii  gimp                        2.4.5-1ubuntu2.1            The GNU Image Manipulation Program
ii  nmap                        4.53-3                      The Network Mapper
No packages found matching axiom-databases.
No packages found matching mythtv-database.
```

```
 **$ dpkg -l '*nautilus*'**
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                        Version                     Description
+++-===========================-===========================-======================================================================
ii  libnautilus-burn4           2.22.1-0ubuntu1             Nautilus Burn Library - runtime version
ii  libnautilus-extension1      1:2.22.5.1-0ubuntu3         libraries for nautilus components - runtime version
un  libnautilus2-2              <none>                      (no description available)
un  libnautilus2-dev            <none>                      (no description available)
ii  nautilus                    1:2.22.5.1-0ubuntu3         file manager and graphical shell for GNOME
ii  nautilus-cd-burner          2.22.1-0ubuntu1             CD Burning front-end for Nautilus
ii  nautilus-data               1:2.22.5.1-0ubuntu3         data files for nautilus
un  nautilus-extensions-2.0     <none>                      (no description available)
ii  nautilus-open-terminal      0.8-1ubuntu3                nautilus plugin for opening terminals in arbitrary local paths
ii  nautilus-sendto             0.13.2-0ubuntu3             integrates Evolution and Pidgin into the Nautilus file manager
ii  nautilus-share              0.7.2-0ubuntu5.1            Nautilus extension to share folder using Samba
un  python-nautilus             <none>                      (no description available)

```


Don't you think it needs to be polished??
This is ridiculous:

```
**$ dpkg -l '*-alsa' '*-alsa' '*-alsa' '*-alsa'**
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                        Version                     Description
+++-===========================-===========================-======================================================================
ii  bluetooth-alsa              0.5cvs20070908-1            Bluetooth audio for Linux
ii  gstreamer0.10-alsa          0.10.18-3                   GStreamer plugin for ALSA
un  libarts-alsa                <none>                      (no description available)
ii  libpt-1.10.10-plugins-alsa  1.10.10-1ubuntu6            Portable Windows Library Audio Plugin for the ALSA Interface
ii  libpt-plugins-alsa          1.10.10-0ubuntu2.1          Portable Windows Library Audio Plugin for the ALSA Interface
ii  libsdl1.2debian-alsa        1.2.13-1ubuntu1             Simple DirectMedia Layer (with X11 and ALSA options)
ii  libsox-fmt-alsa             14.0.0-5                    SoX alsa format I/O library
un  libwine-alsa                <none>                      (no description available)
un  vlc-plugin-alsa             <none>                      (no description available)
ii  xmms2-plugin-alsa           0.2DrJekyll-4ubuntu4        XMMS2 - ALSA output
[B][COLOR="Red"]No packages found matching *-alsa.
No packages found matching *-alsa.
No packages found matching *-alsa.[/COLOR][/B]

```[COLOR="red"] **!!**[/COLOR]


```
$ dpkg -l nmap alsa nmap alsa gimp nmap
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                        Version                     Description
+++-===========================-===========================-======================================================================
un  alsa                        <none>                      (no description available)
ii  gimp                        2.4.5-1ubuntu2.1            The GNU Image Manipulation Program
ii  nmap                        4.53-3                      The Network Mapper
[B][COLOR="Red"]No packages found matching nmap.
No packages found matching alsa.
No packages found matching nmap.[/COLOR][/B]

```

Ridiculous!

---

