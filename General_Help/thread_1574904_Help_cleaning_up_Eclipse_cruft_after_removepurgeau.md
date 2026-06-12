---
title: "Help cleaning up Eclipse cruft after remove/purge/autoremove"
date: 2010-09-14
forum: General Help
---

### Post by Kurtosis on 2010-09-14
I've been trying to completely remove Eclipse from my system and have tried all of the following:

```
sudo aptitude purge eclipse
sudo aptitude autoremove eclipse
sudo dpkg purge eclipse
```

However, running "locate eclipse" afterward shows they all leave eclipse files and directories scattered through the system.  A subset (most of the others are in subdirectories of other applications like Mozilla and Opera):

```
/usr/bin/eclipse
/usr/lib/eclipse
/usr/share/eclipse
/usr/share/app-install/desktop/eclipse.desktop
/usr/share/applications/eclipse.desktop
/usr/share/apport/package-hooks/source_eclipse.py
/usr/share/apps/ksgmltools2/docbook/xsl/params/eclipse.autolabel.xml
/usr/share/apps/ksgmltools2/docbook/xsl/params/eclipse.plugin.id.xml
/usr/share/apps/ksgmltools2/docbook/xsl/params/eclipse.plugin.name.xml
/usr/share/apps/ksgmltools2/docbook/xsl/params/eclipse.plugin.provider.xml
/usr/share/doc/eclipse
/usr/share/doc/eclipse-jdt
/usr/share/doc/eclipse-pde
/usr/share/doc/eclipse-platform
/usr/share/doc/eclipse-platform-data
/usr/share/doc/eclipse-plugin-cvs
/usr/share/doc/eclipse-rcp
/usr/share/doc/docbook-xsl-doc-html/doc/html/eclipse.autolabel.html
/usr/share/doc/docbook-xsl-doc-html/doc/html/eclipse.plugin.id.html
/usr/share/doc/docbook-xsl-doc-html/doc/html/eclipse.plugin.name.html
/usr/share/doc/docbook-xsl-doc-html/doc/html/eclipse.plugin.provider.html
/usr/share/doc/docbook-xsl-doc-html/doc/html/eclipse_help.html
/usr/share/icons/hicolor/16x16/apps/eclipse.png
/usr/share/icons/hicolor/32x32/apps/eclipse.png
/usr/share/icons/hicolor/48x48/apps/eclipse.png
/usr/share/java/eclipse-ecj.jar
/usr/share/java/org.eclipse.osgi.jar
/usr/share/java/org.eclipse.osgi.services.jar
/usr/share/java/org.eclipse.osgi.services.source.jar
/usr/share/java/org.eclipse.osgi.services.source_3.2.0.v20090520-1800.jar
/usr/share/java/org.eclipse.osgi.services_3.2.0.v20090520-1800.jar
/usr/share/java/org.eclipse.osgi.source.jar
/usr/share/java/org.eclipse.osgi.source_3.5.2.R35x_v20100126.jar
/usr/share/java/org.eclipse.osgi.util.jar
/usr/share/java/org.eclipse.osgi.util.source.jar
/usr/share/java/org.eclipse.osgi.util.source_3.2.0.v20090520-1800.jar
/usr/share/java/org.eclipse.osgi.util_3.2.0.v20090520-1800.jar
/usr/share/java/org.eclipse.osgi_3.5.2.R35x_v20100126.jar
/usr/share/kde4/apps/ksgmltools2/docbook/xsl/params/eclipse.autolabel.xml
/usr/share/kde4/apps/ksgmltools2/docbook/xsl/params/eclipse.plugin.id.xml
/usr/share/kde4/apps/ksgmltools2/docbook/xsl/params/eclipse.plugin.name.xml
/usr/share/kde4/apps/ksgmltools2/docbook/xsl/params/eclipse.plugin.provider.xml
/usr/share/man/man1/eclipse.1.gz
/usr/share/pixmaps/eclipse.png
/usr/share/xml/docbook/stylesheet/docbook-xsl/eclipse
/usr/share/xml/docbook/stylesheet/docbook-xsl/eclipse/eclipse.xsl

```

Anyone know why most of this isn't getting removed?  Is it possible to remove Eclipse in such a way that all this stuff goes away too, without doing it manually?

---

### Post by asmoore82 on 2010-09-14
`locate` uses index-based searching which is much faster than a live search -
but in return for the speed, you pay the price of possibly stale results.

There is a cronjob that updates the locate index daily at "/etc/cron.daily/mlocate"

You could call this update by hand and then try your locate command again:
```
sudo /etc/cron.daily/mlocate
locate eclipse
```

-OR-

You could do a slower live search with the `find` command:
```
sudo find / -iname "*eclipse*"
```

---

### Post by Kurtosis on 2010-09-15
Thanks, I forgot about that.  But I tried both, and the result didn't change much.  Only the eclipse files in /var/lib/dpkg/info/ disappeared, the rest were still there.

Note to self:  never install Eclipse from the repository again.

---

### Post by asmoore82 on 2010-09-24
I've never installed eclipse and I have some of those files too...

Big "Duh!" on me... you can also just ask the package manager which package owns the files:
```
dpkg-query --search eclipse
```
^this search command searches for files - not packages

The culprits for me seems to be "app-install-data" and "docbook-xsl"
"app-install-data" sounds important!

---

### Post by Kurtosis on 2010-09-26
Perfect. That's exactly what I was looking for.  Thanks for remembering and coming back and posting it.  Much appreciated.

---

