---
title: "gmail &amp; Evolution resolving imap"
date: 2012-02-29
forum: General Help
---

### Post by Jonners59 on 2012-02-29
My Evolution client keeps refusing to run properly.  Sometines it is OK, then suddenly at next system boot it stops and refuses to work.  And does so time and time again.

It appears to load up alright, but I always know when it is going to fail as the activity tray at the foot of the app window states "resolving imap" instead of "updating" or "checking for new messages".....  And the app becomes un responsive.   In system monitor it states the app is "sleeping".

After a time I get a message say something like the app is not responding or failed do you want to force quit.

Any help please?

---

### Post by dcstar on 2012-03-01
> **Jonners59 said:**
> My Evolution client keeps refusing to run properly.  Sometimes it is OK, then suddenly at next system boot it stops and refuses to work.  And does so time and time again.

It appears to load up alright, but I always know when it is going to fail as the activity tray at the foot of the app window states "**resolving** imap" .........

That means your network/Internet connection is not working correctly. The program cannot resolve the names to IP addresses through DNS.

When it happens check that you can open websites etc., if you can't then you don't have an Evolution problem, you have a networking problem.

---

### Post by Jonners59 on 2012-03-02
> **dcstar said:**
> That means your network/Internet connection is not working correctly. The program cannot resolve the names to IP addresses through DNS.

When it happens check that you can open websites etc., if you can't then you don't have an Evolution problem, you have a networking problem.

I have been using Evolution for about 2 years now.  This happens suddenly.  Everything else works.  This is NOT a network problem at all.

It also seems to be isolated to calendar and contacts, as I can make it work by shutting down the network, then starting Evolution.  Allowing it to settle and then starting the network.  eMail NORMALLY starts working again for a few days.  Calendar and contacts always fail.

Any other ideas, please?

---

### Post by Jonners59 on 2012-03-10
Please any advise:

I have checked my settings against another computer I have and they are the same.
It works for a short spell then stops.
Currently it stops as soon as network is available.  If I disconnect my network it works fine, as soon as I reconnect it just stops.

I have run the following cmd
```
lsb_release -a; uname -a; dpkg -l | grep evolution; echo; ping -c 4 imap.gmail.com
```
and get
[HTML]LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:cxx-3.0-amd64:cxx-3.0-noarch:cxx-3.1-amd64:cxx-3.1-noarch:cxx-3.2-amd64:cxx-3.2-noarch:cxx-4.0-amd64:cxx-4.0-noarch:desktop-3.1-amd64:desktop-3.1-noarch:desktop-3.2-amd64:desktop-3.2-noarch:desktop-4.0-amd64:desktop-4.0-noarch:graphics-2.0-amd64:graphics-2.0-noarch:graphics-3.0-amd64:graphics-3.0-noarch:graphics-3.1-amd64:graphics-3.1-noarch:graphics-3.2-amd64:graphics-3.2-noarch:graphics-4.0-amd64:graphics-4.0-noarch:printing-3.2-amd64:printing-3.2-noarch:printing-4.0-amd64:printing-4.0-noarch:qt4-3.1-amd64:qt4-3.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 11.10
Release:    11.10
Codename:    oneiric
Linux baronipc 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:48:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
ii  evolution                                       3.2.2-0ubuntu0.1                        groupware suite with mail client and organizer
ii  evolution-common                                3.2.2-0ubuntu0.1                        architecture independent files for Evolution
ii  evolution-data-server                           3.2.2-0ubuntu1~oneiric                  evolution database backend server
ii  evolution-data-server-common                    3.2.2-0ubuntu1~oneiric                  architecture independent files for Evolution Data Server
ii  evolution-data-server-dbg                       3.2.2-0ubuntu1~oneiric                  evolution database backend server with debugging symbols
ii  evolution-plugins                               3.2.2-0ubuntu0.1                        standard plugins for Evolution
ii  evolution-webcal                                2.32.0-1build1                          webcal: URL handler for GNOME and Evolution
ii  libebackend-1.2-1                               3.2.2-0ubuntu1~oneiric                  Utility library for evolution data servers
ii  libebook1.2-12                                  3.2.2-0ubuntu1~oneiric                  Client library for evolution address books
ii  libecal1.2-10                                   3.2.2-0ubuntu1~oneiric                  Client library for evolution calendars
ii  libedata-book-1.2-11                            3.2.2-0ubuntu1~oneiric                  Backend library for evolution address books
ii  libedata-cal-1.2-13                             3.2.2-0ubuntu1~oneiric                  Backend library for evolution calendars
ii  libedataserver1.2-15                            3.2.2-0ubuntu1~oneiric                  Utility library for evolution data servers
ii  libedataserverui-3.0-1                          3.2.2-0ubuntu1~oneiric                  GUI utility library for evolution data servers
ii  libevolution                                    3.2.2-0ubuntu0.1                        evolution libraries
ii  python-evolution                                2.32.0-0ubuntu6                         Python bindings for the evolution libraries

PING gmail-imap.l.google.com (173.194.70.109) 56(84) bytes of data.
64 bytes from fa-in-f109.1e100.net (173.194.70.109): icmp_req=1 ttl=48 time=27.3 ms
64 bytes from fa-in-f109.1e100.net (173.194.70.109): icmp_req=2 ttl=48 time=26.2 ms
64 bytes from fa-in-f109.1e100.net (173.194.70.109): icmp_req=3 ttl=48 time=26.3 ms
64 bytes from fa-in-f109.1e100.net (173.194.70.109): icmp_req=4 ttl=48 time=40.4 ms

--- gmail-imap.l.google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 7090ms
rtt min/avg/max/mdev = 26.232/30.105/40.412/5.969 ms[/HTML]

There is nothing wrong with my connection - I couldn't access this thread if there was.

---

### Post by Jonners59 on 2012-03-12
The problem was that I was using IMAP+, not simple IMAP.....

---

