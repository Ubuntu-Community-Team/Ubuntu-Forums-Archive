---
title: "Mediatomb hangs on startup"
date: 2011-02-19
forum: General Help
---

### Post by dgray_from_dc on 2011-02-19
I have a HTPC / media server setup running on an ASUS based AMD64 Phenom X3 machine.  I've run Mediatomb a million times on a Dell Core2 Duo and have never had any major problems.  However, on this machine, when I start Mediatomb, manually or in daemon mode it hangs after the configuration check.

```
user@hostname:~$ mediatomb

MediaTomb UPnP Server version 0.12.0 - http://mediatomb.cc/

===============================================================================
Copyright 2005-2008 Gena Batsyan, Sergey Bostandzhyan, Leonhard Wimmer.
MediaTomb is free software, covered by the GNU General Public License version 2

2011-02-19 08:49:50    INFO: Loading configuration from: /home/dontrel/.mediatomb/config.xml
2011-02-19 08:49:50    INFO: Checking configuration...
2011-02-19 08:49:50    INFO: Setting filesystem import charset to UTF-8
2011-02-19 08:49:50    INFO: Setting metadata import charset to UTF-8
2011-02-19 08:49:50    INFO: Setting playlist charset to UTF-8
2011-02-19 08:49:50    INFO: Configuration check succeeded.

```

I can't stop it with ctrl-C.  I can see the process from the system monitor and cannot kill the process.  It's just stuck.  I configured for autostart, got no results, and got this from the last /var/log/mediatomb.log entry:


```
2011-02-19 08:39:49    INFO: Loading configuration from: /etc/mediatomb/config.xml
2011-02-19 08:39:49    INFO: Checking configuration...
2011-02-19 08:39:49    INFO: Setting filesystem import charset to ANSI_X3.4-1968
2011-02-19 08:39:49    INFO: Setting metadata import charset to ANSI_X3.4-1968
2011-02-19 08:39:49    INFO: Setting playlist charset to ANSI_X3.4-1968
2011-02-19 08:39:49    INFO: Configuration check succeeded.
2011-02-19 08:39:49    INFO: Initialized port: 49152
2011-02-19 08:39:49    INFO: Server bound to: 192.168.2.4
2011-02-19 08:39:50    INFO: MediaTomb Web UI can be reached by following this link:
2011-02-19 08:39:50    INFO: http://192.168.2.4:49152/


```

I see no problems yet have no results.  Any thoughts?

---

