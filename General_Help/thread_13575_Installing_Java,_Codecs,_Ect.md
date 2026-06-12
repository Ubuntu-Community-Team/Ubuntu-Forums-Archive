---
title: "Installing Java, Codecs, Ect"
date: 2005-02-01
forum: General Help
---

### Post by impel on 2005-02-01
Hey guys, I'm trying to install Java, Codecs and some other apps via the starter guide and im having some trouble.

I managed to get java installed on the system and it shows

jason@house:~ $ java -version
java version "1.5.0_01"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_01-b08)
Java HotSpot(TM) Client VM (build 1.5.0_01-b08, mixed mode, sharing)

but i cant get the plugin to work in firefox.

none of the commands on the howto of installing multimedia codecs work. 

jason@house:~ $ sudo apt-get install gstreamer0.8-plugins
Password:
Reading Package Lists... Done
Building Dependency Tree... Done
Package gstreamer0.8-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.8-plugins has no installation candidate
jason@house:~ $ sudo apt-get install w32codecs
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package w32codecs

---

### Post by impel on 2005-02-01
also i get this message when i try to update

jason@house:~ $ sudo apt-get upgrade
Reading Package Lists... Done
Building Dependency Tree... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
  sun-j2sdk1.5: Depends: sun-j2sdk1.5debian but it is not installable
E: Unmet dependencies. Try using -f.

---

### Post by poofyhairguy on 2005-02-01
[QUOTE=impel]Hey guys, I'm trying to install Java, Codecs and some other apps via the starter guide and im having some trouble.

I managed to get java installed on the system and it shows

jason@house:~ $ java -version
java version "1.5.0_01"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_01-b08)
Java HotSpot(TM) Client VM (build 1.5.0_01-b08, mixed mode, sharing)

but i cant get the plugin to work in firefox.

none of the commands on the howto of installing multimedia codecs work. 

jason@house:~ $ sudo apt-get install gstreamer0.8-plugins
Password:
Reading Package Lists... Done
Building Dependency Tree... Done
Package gstreamer0.8-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.8-plugins has no installation candidate
jason@house:~ $ sudo apt-get install w32codecs
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package w32codecs[/QUOTE]


Well....you need to enable java for firefox and add another repo with the codecs in it.

This guide will get you up and running:

[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by impel on 2005-02-01
thats what im using. it didnt make it work with firefox.


$ sudo ln -s /usr/java/jre1.5.0_01/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla/plugins/
$ sudo ln -s /usr/java/jre1.5.0_01/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins/

i see the file copied over into the plugins folder, but not working

---

### Post by keyshawn on 2005-02-09
[QUOTE=impel]thats what im using. it didnt make it work with firefox.


$ sudo ln -s /usr/java/jre1.5.0_01/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla/plugins/
$ sudo ln -s /usr/java/jre1.5.0_01/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins/

i see the file copied over into the plugins folder, but not working[/QUOTE]

it's possible that an older one from version 1.5.0 [or even 142] may already be there, and you have to force it to overwrite it. 

You can do this by adding -f 
to the commands that you used previously.

---

### Post by Buffalo Soldier on 2005-02-09
[QUOTE=impel]jason@house:~ $ sudo apt-get install gstreamer0.8-plugins
Password:
Reading Package Lists... Done
Building Dependency Tree... Done
Package gstreamer0.8-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.8-plugins has no installation candidate
jason@house:~ $ sudo apt-get install w32codecs
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package w32codecs[/QUOTE]
It looks like you did not add the extra repository. The instruction is available at [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

