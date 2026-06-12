---
title: "need help fixing my repositories"
date: 2010-09-28
forum: General Help
---

### Post by sendblink23 on 2010-09-28
Well a bit earlier today I was trying to install the latest VLC following steps from this link:

[http://www.ubuntugeek.com/install-vlc-1-1-2-in-ubuntu-10-049-10.html](http://www.ubuntugeek.com/install-vlc-1-1-2-in-ubuntu-10-049-10.html)

it instructed:
```
sudo add-apt-repository ppa:gnome-media-player-development/development

sudo apt-get update
```

But after the sudo apt-get update

I started getting errors at the end.. here is my log after running it:
```
sendblink23@sendblink23-Ubuntu:~$ sudo apt-get update
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://ppa.launchpad.net lucid Release.gpg
Ign http://ppa.launchpad.net/c-korn/vlc/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg
Ign http://ppa.launchpad.net/gnome-media-player-development/development/ubuntu/ lucid/main Translation-en_US
Ign http://ppa.launchpad.net lucid Release
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-security Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release
Hit http://ppa.launchpad.net lucid Release
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release
Hit http://us.archive.ubuntu.com lucid-updates Release
Ign http://ppa.launchpad.net lucid/main Packages                     
Hit http://us.archive.ubuntu.com lucid-security Release
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Ign http://ppa.launchpad.net lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Err http://ppa.launchpad.net lucid/main Packages
  404  Not Found
Hit http://us.archive.ubuntu.com lucid-security/main Packages
Hit http://us.archive.ubuntu.com lucid-security/restricted Packages
Hit http://us.archive.ubuntu.com lucid-security/main Sources
Hit http://us.archive.ubuntu.com lucid-security/restricted Sources
Hit http://us.archive.ubuntu.com lucid-security/universe Packages
Hit http://us.archive.ubuntu.com lucid-security/universe Sources
Hit http://us.archive.ubuntu.com lucid-security/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-security/multiverse Sources
W: Failed to fetch http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

So I didn't go forward & read comments(noticed everybody had the same error) and then at the end of the comments found the correct PPA to install the lastest VLC(Already its installed) 

Now... I want to fix those errors I get at the end on "apt-get update"

I assumed I only needed to purge the PPA I first installed.. I followed this site: [http://www.webupd8.org/2009/12/remove-ppa-repositories-via-command.html](http://www.webupd8.org/2009/12/remove-ppa-repositories-via-command.html)

I first installed the purge app at the end... then I ran on terminal:
```
sudo ppa-purge ppa:gnome-media-player-development/development
```
not sure if that is the way it was meant to be done... :/

This is the log:
```
sendblink23@sendblink23-Ubuntu:~$ sudo ppa-purge ppa:gnome-media-player-development/development
PPA to be removed: gnome-media-player-development development
Package revert list generated:
 libvlc5/lucid libvlccore4/lucid mozilla-plugin-vlc/lucid vlc/lucid 
vlc-data/lucid vlc-nox/lucid vlc-plugin-pulse/lucid

Disabling gnome-media-player-development PPA from 
/etc/apt/sources.list.d/gnome-media-player-development-development-lucid.list
Running apt-get update
W: Failed to fetch http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
Warning:  apt-get update failed for some reason
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Selected version 1.1.4-1~lffl~lucid~ppa1 (LffL Lucid:10.04/lucid) for libvlc5
libvlc5 is already the newest version.
libvlc5 set to manually installed.
Selected version 1.1.4-1~lffl~lucid~ppa1 (LffL Lucid:10.04/lucid) for libvlccore4
libvlccore4 is already the newest version.
libvlccore4 set to manually installed.
Selected version 1.1.4-1~lffl~lucid~ppa1 (LffL Lucid:10.04/lucid) for mozilla-plugin-vlc
mozilla-plugin-vlc is already the newest version.
Selected version 1.1.4-1~lffl~lucid~ppa1 (LffL Lucid:10.04/lucid) for vlc
vlc is already the newest version.
Selected version 1.1.4-1~lffl~lucid~ppa1 (LffL Lucid:10.04/lucid) for vlc-data
vlc-data is already the newest version.
vlc-data set to manually installed.
Selected version 1.1.4-1~lffl~lucid~ppa1 (LffL Lucid:10.04/lucid) for vlc-nox
vlc-nox is already the newest version.
vlc-nox set to manually installed.
Selected version 1.1.4-1~lffl~lucid~ppa1 (LffL Lucid:10.04/lucid) for vlc-plugin-pulse
vlc-plugin-pulse is already the newest version.
vlc-plugin-pulse set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
PPA purged successfully
```

I'm guessing it tried to purged the PPA... but it didn't work... the error still exist on "sudo apt-get update"...  any way of fixing or manually eliminating those bad errors?

Current "get update":
```
sendblink23@sendblink23-Ubuntu:~$ sudo apt-get update
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://ppa.launchpad.net lucid Release.gpg
Ign http://ppa.launchpad.net/c-korn/vlc/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Ign http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu/ lucid/main Translation-en_US
Ign http://ppa.launchpad.net lucid Release
Hit http://us.archive.ubuntu.com lucid-security Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://ppa.launchpad.net lucid Release
Hit http://us.archive.ubuntu.com lucid-security Release              
Ign http://ppa.launchpad.net lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://ppa.launchpad.net lucid/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-security/main Packages
Hit http://us.archive.ubuntu.com lucid-security/restricted Packages
Hit http://us.archive.ubuntu.com lucid-security/main Sources
Hit http://us.archive.ubuntu.com lucid-security/restricted Sources
Hit http://us.archive.ubuntu.com lucid-security/universe Packages
Err http://ppa.launchpad.net lucid/main Packages
  404  Not Found
Hit http://us.archive.ubuntu.com lucid-security/universe Sources
Hit http://us.archive.ubuntu.com lucid-security/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-security/multiverse Sources
W: Failed to fetch http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

any ideas on how to fix it?

---

### Post by Soul-Sing on 2010-09-28
That ppa from c-korn isn't a good source for updating vlc anymore.
could you remove the source from software sources? (system: administration: etc)
maybe this ppa will do: [https://edge.launchpad.net/~n-muench/+archive/vlc?field.series_filter=lucid](https://edge.launchpad.net/~n-muench/+archive/vlc?field.series_filter=lucid)

---

### Post by sendblink23 on 2010-09-28
> **leoquant said:**
> That ppa from c-korn isn't a good source for updating vlc anymore.
could you remove the source from software sources? (system: administration: etc)
maybe this ppa will do: [https://edge.launchpad.net/~n-muench/+archive/vlc?field.series_filter=lucid](https://edge.launchpad.net/~n-muench/+archive/vlc?field.series_filter=lucid)

Thanks.. no clue why I forgot to check System > Administration > Software Sources :P that certainly fixed it I removed the c-korn PPA there - reloaded and no errors :)

Don't worry I posted in the middle that I did already find the correct PPA for the latest VLC ;)
> So I didn't go forward & read comments(noticed everybody had the same error) and then at the end of the comments found the correct PPA to install the lastest VLC(Already its installed)

Thank you for mentioning S > A > etc... to fix the PPA error ;)

---

