---
title: "Backing up a specific server pakage."
date: 2010-05-16
forum: General Help
---

### Post by jerome1232 on 2010-05-16
So I was wondering how would I backup a specific package. Really all I want is the configuration files.

the package I'm talking about is mumble-server, could I say rsync all the files that were installed, then if I wanted to drop it in just copy those back over?

If I had to wipe the installation and reinstall, could I install that package again then drop my backup copy back over it?

Dpkg tells me these are the files it installed.

```
dpkg-query -L mumble-server
/.
/var
/var/log
/var/log/mumble-server
/usr
/usr/sbin
/usr/sbin/murmurd
/usr/bin
/usr/bin/murmur-user-wrapper
/usr/share
/usr/share/slice
/usr/share/slice/Murmur.ice
/usr/share/doc
/usr/share/doc/mumble-server
/usr/share/doc/mumble-server/NEWS.Debian.gz
/usr/share/doc/mumble-server/changelog.gz
/usr/share/doc/mumble-server/README
/usr/share/doc/mumble-server/Ice
/usr/share/doc/mumble-server/Ice/index.html
/usr/share/doc/mumble-server/Ice/_sindex.html
/usr/share/doc/mumble-server/Ice/Murmur.html
/usr/share/doc/mumble-server/Ice/Murmur
/usr/share/doc/mumble-server/Ice/Murmur/ACL.html
/usr/share/doc/mumble-server/Ice/Murmur/Ban.html
/usr/share/doc/mumble-server/Ice/Murmur/Channel.html
/usr/share/doc/mumble-server/Ice/Murmur/ChannelInfo.html
/usr/share/doc/mumble-server/Ice/Murmur/Group.html
/usr/share/doc/mumble-server/Ice/Murmur/InvalidCallbackException.html
/usr/share/doc/mumble-server/Ice/Murmur/InvalidChannelException.html
/usr/share/doc/mumble-server/Ice/Murmur/InvalidSecretException.html
/usr/share/doc/mumble-server/Ice/Murmur/InvalidServerException.html
/usr/share/doc/mumble-server/Ice/Murmur/InvalidSessionException.html
/usr/share/doc/mumble-server/Ice/Murmur/InvalidTextureException.html
/usr/share/doc/mumble-server/Ice/Murmur/InvalidUserException.html
/usr/share/doc/mumble-server/Ice/Murmur/LogEntry.html
/usr/share/doc/mumble-server/Ice/Murmur/Meta.html
/usr/share/doc/mumble-server/Ice/Murmur/MetaCallback.html
/usr/share/doc/mumble-server/Ice/Murmur/MurmurException.html
/usr/share/doc/mumble-server/Ice/Murmur/Server.html
/usr/share/doc/mumble-server/Ice/Murmur/ServerAuthenticator.html
/usr/share/doc/mumble-server/Ice/Murmur/ServerBootedException.html
/usr/share/doc/mumble-server/Ice/Murmur/ServerCallback.html
/usr/share/doc/mumble-server/Ice/Murmur/ServerContextCallback.html
/usr/share/doc/mumble-server/Ice/Murmur/ServerFailureException.html
/usr/share/doc/mumble-server/Ice/Murmur/ServerUpdatingAuthenticator.html
/usr/share/doc/mumble-server/Ice/Murmur/Tree.html
/usr/share/doc/mumble-server/Ice/Murmur/User.html
/usr/share/doc/mumble-server/Ice/Murmur/UserInfo.html
/usr/share/doc/mumble-server/README.Debian
/usr/share/doc/mumble-server/copyright
/usr/share/doc/mumble-server/examples
/usr/share/doc/mumble-server/examples/icedemo.php.gz
/usr/share/doc/mumble-server/examples/murmur.ini.gz
/usr/share/doc/mumble-server/examples/dbusauth.pl.gz
/usr/share/doc/mumble-server/changelog.Debian.gz
/usr/share/doc-base
/usr/share/doc-base/mumble-server
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/murmurd.1.gz
/usr/share/man/man1/murmur-user-wrapper.1.gz
/etc
/etc/dbus-1
/etc/dbus-1/system.d
/etc/dbus-1/system.d/mumble-server.conf
/etc/mumble-server.ini
/etc/default
/etc/default/mumble-server
/etc/init.d
/etc/init.d/mumble-server
/etc/logrotate.d
/etc/logrotate.d/mumble-server
```

---

### Post by dcstar on 2010-05-17
> **jerome1232 said:**
> So I was wondering how would I backup a specific package. Really all I want is the configuration files.

the package I'm talking about is mumble-server, could I say rsync all the files that were installed, then if I wanted to drop it in just copy those back over?

If I had to wipe the installation and reinstall, could I install that package again then drop my backup copy back over it?
.........

Unless you have changed any of the defaults, there is no need to backup anything.

If you have changed the relevant /etc/default file, back it up and restore it.

---

