---
title: "how to uninstall a stubun program"
date: 2010-01-19
forum: General Help
---

### Post by johnh10000 on 2010-01-19
hi, i foolishly tried to install campcaster again.  after I had installed postgresql 8.4,  it seems itonly like 8.1 8.2 or 8.3  and has messed thing up.

Any ideas on how to get this sorted!

```

root@tux:~/Downloads/camp# /usr/share/mc/extfs/deb run /root/Downloads/camp/campcaster-studio_1.4.0-3beta3_i386.deb INSTALL
Installing /root/Downloads/camp/campcaster-studio_1.4.0-3beta3_i386.deb
(Reading database ... 241579 files and directories currently installed.)
Preparing to replace campcaster-studio 1.4.0-3beta3 (using .../campcaster-studio_1.4.0-3beta3_i386.deb) ...
Unpacking replacement campcaster-studio ...
dpkg: dependency problems prevent configuration of campcaster-studio:
 campcaster-studio depends on campcaster-station (= 1.4.0-3beta3); however:
  Package campcaster-station is not configured yet.
dpkg: error processing campcaster-studio (--install):
 dependency problems - leaving unconfigured
Processing triggers for menu ...
Errors were encountered while processing:
 campcaster-studio
root@tux:~/Downloads/camp# /usr/share/mc/extfs/deb run /root/Downloads/camp/campcaster-station_1.4.0-3beta3_i386.deb INSTALL
Installing /root/Downloads/camp/campcaster-station_1.4.0-3beta3_i386.deb
(Reading database ... 241579 files and directories currently installed.)
Preparing to replace campcaster-station 1.4.0-3beta3 (using .../campcaster-station_1.4.0-3beta3_i386.deb) ...
no postgresql 8.1, 8.2 or 8.3 found
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
no postgresql 8.1, 8.2 or 8.3 found
dpkg: error processing /root/Downloads/camp/campcaster-station_1.4.0-3beta3_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 1
no postgresql 8.1, 8.2 or 8.3 found
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /root/Downloads/camp/campcaster-station_1.4.0-3beta3_i386.deb
root@tux:~/Downloads/camp# /usr/share/mc/extfs/deb run /root/Downloads/camp/campcaster-station_1.4.0-3beta3_i386.deb INSTALL
Installing /root/Downloads/camp/campcaster-station_1.4.0-3beta3_i386.deb
(Reading database ... 241579 files and directories currently installed.)
Preparing to replace campcaster-station 1.4.0-3beta3 (using .../campcaster-station_1.4.0-3beta3_i386.deb) ...
no postgresql 8.1, 8.2 or 8.3 found
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
no postgresql 8.1, 8.2 or 8.3 found
dpkg: error processing /root/Downloads/camp/campcaster-station_1.4.0-3beta3_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 1
no postgresql 8.1, 8.2 or 8.3 found
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /root/Downloads/camp/campcaster-station_1.4.0-3beta3_i386.deb

root@tux:~/Downloads/camp# 
root@tux:~/Downloads/camp# 
root@tux:~/Downloads/camp# 
root@tux:~/Downloads/camp# apt-get remove postgresql-8.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package campcaster-station needs to be reinstalled, but I can't find an archive for it.
root@tux:~/Downloads/camp# apt-get install postgresql-8.3
Reading package lists... Done
Building dependency tree        
Reading state information... Done
E: The package campcaster-station needs to be reinstalled, but I can't find an archive for it.
root@tux:~/Downloads/camp# 

```

---

### Post by mcduck on 2010-01-19
HAve you tried removing it with dpkg? Or removing all the offending packages at the same time to avoid dependency problems?

```
sudo dpkg -r campcaster-station postgresql-8.4
```

Also placing all the related packages into /var/cache/apt/archives might help a lot if you try to do this kind of stuff with apt. Apt will try to handle the dependencies but that's a bit hard if the actual packages are not anywhere it can find them (meaning wither the repositories, or the cache directory).

---

### Post by johnh10000 on 2010-01-19
> **mcduck said:**
> HAve you tried removing it with dpkg? Or removing all the offending packages at the same time to avoid dependency problems?

```
sudo dpkg -r campcaster-station postgresql-8.4
```

Also placing all the related packages into /var/cache/apt/archives might help a lot if you try to do this kind of stuff with apt. Apt will try to handle the dependencies but that's a bit hard if the actual packages are not anywhere it can find them (meaning wither the repositories, or the cache directory).

yes I thought of that, and indeed put all of them in apt-cache directory.  Still no joy.  I have even tried to install postressql 8.3 , no joy

```

root@tux:~# dpkg -l camp*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  campcaster-lib 1.4.0-3beta3   A radio program automation and support tool.
iFR campcaster-sta 1.4.0-3beta3   A radio program automation and support tool.
iU  campcaster-stu 1.4.0-3beta3   A radio program automation and support tool.
root@tux:~# apt-get install xfce4-appfinder
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package campcaster-station needs to be reinstalled, but I can't find an archive for it.
root@tux:~# apt-get install beagle
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package campcaster-station needs to be reinstalled, but I can't find an archive for it.
root@tux:~# sudo dpkg -r campcaster-station
dpkg: error processing campcaster-station (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 campcaster-station
root@tux:~# sudo dpkg -r campcaster-station postgresql-8.4
dpkg: error processing campcaster-station (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 241578 files and directories currently installed.)
Removing postgresql-8.4 ...
 * Stopping PostgreSQL 8.4 database server                               [ OK ] 
Errors were encountered while processing:
 campcaster-station
root@tux:~# 

```

sorry about time taken to reply.  asked for eamil notification, and none happend :(  a minor problem.

---

