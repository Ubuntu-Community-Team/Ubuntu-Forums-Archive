---
title: "Azureus Problem..."
date: 2006-04-01
forum: General Help
---

### Post by gtkourounis on 2006-04-01
I have installed everything correctly, java and azureus but the azureus doesnt seem to want to update and that also doesnt allow me to dowload anything of it. The poblem that is give is....



>    Downloading: [[http://torrents.aelitis.com:88/torrents/azplugins_2.0.jar.torrent:](http://torrents.aelitis.com:88/torrents/azplugins_2.0.jar.torrent:) torrent,[http://azureus.sourceforge.net/plugins/azplugins_2.0.jar]](http://azureus.sourceforge.net/plugins/azplugins_2.0.jar])
      Downloading: azplugins_2.0.jar
Torrent download complete
Installing plugin azplugins, version 2.0
Version 2.0 of plugin 'azplugins' failed to install - /opt/azureus/plugins/azplugins/azplugins_2.0.jar (Permission denied)

how do i make it permitable so that the installer can actually work?

if you could help that would be amazing,

thanx in advance.

---

### Post by localzuk on 2006-04-01
Run azureus as root in order to allow it to update (sudo azureus). Else give the azureus directory more permissions (chmod a+rw /where/azureus/is) - this is insecure and their are better methods (create a new group, change the group of all the azureus files to be this group, add your user to the group and give group write permissions on all files in the azureus directory).

It has downloaded something - the message you post states that it successfully downloaded azplugins_2.0.jar.

---

### Post by Barrakketh on 2006-04-01
I recommend downloading the tarball from the Azureus site, creating a ~/bin directory, and untarring it there. Create a shortcut and you're golden.  I prefer that as opposed letting Azureus drop files all over my system.

---

### Post by localzuk on 2006-04-01
Azureus doesn't drop files all over your system - there isn't a native package for it to do this. The only method I have seen for it to be installed is by using the tarball. (Automatix downloads it and installs it into /opt/ which is fairly standard).

---

### Post by Myndmelder on 2006-04-01
[QUOTE=localzuk]create a new group, change the group of all the azureus files to be this group, add your user to the group and give group write permissions on all files in the azureus directory[/QUOTE]

How do you do that?

doing sudo azureus didn't quite work, since one you close azureus and reopen it without sudo some of the plugins no longer work... Especially SafePeer (mini PeerGuardian).

---

