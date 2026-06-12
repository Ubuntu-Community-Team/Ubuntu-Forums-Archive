---
title: "Vidalia/Tor on Ubuntu or Debian, problem with installing."
date: 2011-03-11
forum: General Help
---

### Post by noveevon on 2011-03-11
Hi,

i tried installing the package here as listed for maverick( [https://www.torproject.org/docs/debian-vidalia.html.en](https://www.torproject.org/docs/debian-vidalia.html.en) ) , but it said the following:

>                            Errors were encountered while processing:
 tor
 tor-geoipdb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@dopy:/home/billy# apt-get install vidalia
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  iceweasel-torbutton
The following NEW packages will be installed:
  vidalia
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/2,657kB of archives.
After this operation, 5,624kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package vidalia.
(Reading database ... 216810 files and directories currently installed.)
Unpacking vidalia (from .../vidalia_0.2.9-1_amd64.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up tor (0.2.1.30-1~maverick+1) ...
Raising maximum number of filedescriptors (ulimit -n) to 32768.
Starting tor daemon: tor...
Mar 11 10:55:33.899 [notice] Tor v0.2.1.30. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux x86_64)
Mar 11 10:55:33.901 [notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Mar 11 10:55:33.901 [notice] Opening Socks listener on 127.0.0.1:9050
Mar 11 10:55:33.901 [warn] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Mar 11 10:55:33.901 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
Mar 11 10:55:33.901 [err] Reading config failed--see warnings above.
invoke-rc.d: initscript tor, action "start" failed.
dpkg: error processing tor (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of tor-geoipdb:
 tor-geoipdb depends on tor (>= 0.2.1.30-1~maverick+1); however:
  Package tor is not configured yet.
dpkg: error processing tor-geoipdb (--configure):
 dependency problems - leaving unconfigured
Setting up vidalia (0.2.9-1) ...
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 tor
 tor-geoipdb
E: Sub-process /usr/bin/dpkg returned an error code (1)
 anyone know what i need to do?



PS: i also tried using the Torbutton for firefox ( [https://www.torproject.org/torbutton/index.html.en](https://www.torproject.org/torbutton/index.html.en)  ) , but that blocks my internet access...the only one that seem to work is the bundle you download but do not install, however i dont want to rely on that all the time as its very unpractical..

---

