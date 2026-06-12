---
title: "Make apt-cache more.. hm.. understandable"
date: 2011-09-27
forum: General Help
---

### Post by extruct on 2011-09-27
Hi, I would like to know if its possible to make "apt-cache search foo" be more understandable? Because when there are a lot of packages and long descriptions, its unclear to read and distinguish where are the names and where are the descriptions.

For example (excerpt for java search):
```

$ apt-cache search java
sapgui-package - utility to build SAP GUI related Debian packages
selfhtml - German HTML reference and tutorial
sun-javadb-client - Java DB client
sun-javadb-common - Java DB common files
sun-javadb-core - Java DB core
sun-javadb-demo - Java DB demo
sun-javadb-doc - Java DB documentation
sun-javadb-javadoc - Java DB javadoc
tightvnc-java - TightVNC java applet and command line program
tijmp - Profiler for Java to trace object and method timings
ubuntu-restricted-extras - Commonly used restricted packages for Ubuntu
vnc-java - VNC java applet and command line program
weirdx - X server in Java
xubuntu-restricted-extras - Commonly used restricted packages for Xubuntu
dbus - simple interprocess messaging system
eucalyptus-java-common - Elastic Utility Computing Architecture - Common Java package
icedtea-netx - NetX - implementation of the Java Network Launching Protocol (JNLP)
icedtea-plugin - web browser plugin based on OpenJDK and IcedTea to execute Java applets
libcups2-dev - Common UNIX Printing System(tm) - Development files CUPS library
libdbus-1-3 - simple interprocess messaging system
libreoffice-base - office productivity suite -- database
libreoffice-dev - office productivity suite -- SDK
libreoffice-dev-doc - office productivity suite -- SDK documentation
libreoffice-gcj - office productivity suite -- Java libraries for GIJ
libreoffice-java-common - office productivity suite -- arch-independent Java support files
libreoffice-officebean - office productivity suite -- Java bean
openjdk-6-dbg - Java runtime based on OpenJDK (debugging symbols)
openjdk-6-demo - Java runtime based on OpenJDK (demos and examples)
openjdk-6-doc - OpenJDK Development Kit (JDK) documentation
openjdk-6-jdk - OpenJDK Development Kit (JDK)
openjdk-6-jre - OpenJDK Java runtime, using Hotspot JIT
openjdk-6-jre-headless - OpenJDK Java runtime, using Hotspot JIT (headless)
openjdk-6-jre-lib - OpenJDK Java runtime (architecture independent libraries)
openjdk-6-source - OpenJDK Development Kit (JDK) source files
openoffice.org-gcj - office productivity suite -- Java libraries for GIJ
tzdata-java - time zone and daylight-saving time data for use by java runtimes
icedtea6-plugin - web browser plugin to execute Java applets (dependency package)
libreoffice - office productivity suite
libsvn-java - Java bindings for Subversion
mozilla-plugin-vlc - multimedia plugin for web browsers based on VLC
openoffice.org-java-common - office productivity suite -- arch-independent Java support files
openoffice.org-officebean - office productivity suite -- Java bean
php5-fpm - server-side, HTML-embedded scripting language (FPM-CGI binary)
plasma-scriptengine-webkit - Web and Mac OS X dashboard widget support for Plasma
uex - UltraEdit is a text, hex, and programming language editor
jonas-5.2 - Java Open Application Server 5.2
sun-java6-plugin - Java(TM) Plug-in, Java SE 6

```
Can you understand something from here? (And its only a small part of the all results)

Are there some front ends or improvements to the apt-cache to make it more usable, more clear?

Using GUI synaptic package manager or other GUI tools provided by Ubuntu, is not an option, sometimes I need to search for packages fast and most of the time I use terminal.

Thanks a lot!

---

### Post by nothingspecial on 2011-09-27
The -n flag will search names only.

That's still a lot of packages if you search for "java" though.

---

### Post by extruct on 2011-09-27
The problem is not the search in name or search in name+description, but the problem is in the display of the results.
Result displayed in a confusing way. Sometimes the description scrolls to the next line (yes I know I can expand my terminal, that's not the solution) which makes it hard to see a distinguish between packages.

Take a look at pacman (or its frontend yaourt) search from Arch Linux
[IMG]http://xabbott.files.wordpress.com/2007/02/yaourt.png?w=700[/IMG]
Now compare it to apt-cache
```

$ apt-cache search wesnoth
wesnoth - fantasy turn-based strategy game - complete suite (metapackage)
wesnoth-1.8 - fantasy turn-based strategy game - complete suite (branch 1.8)
wesnoth-1.8-aoi - "An Orcish Incursion" official campaign for Wesnoth (branch 1.8)
wesnoth-1.8-core - fantasy turn-based strategy game (branch 1.8)
wesnoth-1.8-data - data files for Wesnoth (branch 1.8)
wesnoth-1.8-dbg - fantasy turn-based strategy game (debugging symbols for branch 1.8)
wesnoth-1.8-did - "Descent Into Darkness" official campaign for Wesnoth (branch 1.8)
wesnoth-1.8-dm - "Delfador's Memoirs" official campaign for Wesnoth (branch 1.8)
wesnoth-1.8-ei - "The Eastern Invasion" official campaign for Wesnoth (branch 1.8)
wesnoth-1.8-httt - "Heir to the Throne" official campaign for Wesnoth (branch 1.8)
wesnoth-1.8-l - "Liberty" official campaign for Wesnoth (branch 1.8)
wesnoth-1.8-low - "Legend of Wesmere" official campaign for Wesnoth (branch 1.8)
wesnoth-1.8-music - music files for Wesnoth (branch 1.8)
wesnoth-1.8-nr - "Northern Rebirth" official campaign for Wesnoth (branch 1.8)
wesnoth-1.8-server - multiplayer network server for Wesnoth (branch 1.8)
wesnoth-1.8-sof - "The Sceptre of Fire" official campaign for Wesnoth (branch 1.8)
wesnoth-1.8-sotbe - "Son of the Black-Eye" official campaign for Wesnoth (branch 1.8)
wesnoth-1.8-thot - "The Hammer of Thursagan" official campaign for Wesnoth (branch 1.8)
wesnoth-1.8-tools - tools for campaign developers for Wesnoth (branch 1.8)
wesnoth-1.8-trow - "The Rise of Wesnoth" official campaign for Wesnoth (branch 1.8)
wesnoth-1.8-tsg - "The South Guard" official campaign for Wesnoth (branch 1.8)
wesnoth-1.8-ttb - "A Tale of Two Brothers" official campaign for Wesnoth (branch 1.8)
wesnoth-1.8-utbs - "Under the Burning Suns" official campaign for Wesnoth (branch 1.8)
wesnoth-all - fantasy turn-based strategy game - complete suite (transitional package)
wesnoth-core - fantasy turn-based strategy game (metapackage)
wesnoth-editor - map editor for Wesnoth (transitional package)
wesnoth-music - music files for Wesnoth (metapackage)

```
(You can't see the description breaking to next line here on forum, but in my terminal its unreadable).

See what I mean?

---

### Post by CatKiller on 2011-09-27
Have you tried aptitude instead?

---

### Post by lordbux on 2011-09-27
> **CatKiller said:**
> Have you tried aptitude instead?

try 
```
aptitude search <package>
```

is more arranged and better presented :P

---

