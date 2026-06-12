---
title: "Problem while apt-get upgrade : Errors were encountered while processing:"
date: 2011-03-22
forum: General Help
---

### Post by maizuddin35 on 2011-03-22
I had some problem while apt-get upgrade 

here is the output :
```
sudo apt-get upgrade
[sudo] password for adibizuddin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  faenza-icon-theme
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0B/13.8MB of archives.
After this operation, 10.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  faenza-icon-theme
Install these packages without verification [y/N]? y
(Reading database ... 236821 files and directories currently installed.)
Preparing to replace faenza-icon-theme 0.8 (using .../faenza-icon-theme_0.9_i386.deb) ...
Leaving 'diversion of /usr/lib/rhythmbox/plugins/audioscrobbler/as-icon.png to /usr/lib/rhythmbox/plugins/audioscrobbler/as-icon.default.png by faenza-icon-theme'
Adding 'diversion of /usr/lib/rhythmbox/plugins/umusicstore/musicstore_icon.png to /usr/lib/rhythmbox/plugins/umusicstore/musicstore_icon.default.png by faenza-icon-theme'
Adding 'diversion of /usr/share/dockmanager/data/skype_away.svg to /usr/share/dockmanager/data/skype_away.default.svg by faenza-icon-theme'
Adding 'diversion of /usr/share/dockmanager/data/skype_dnd.svg to /usr/share/dockmanager/data/skype_dnd.default.svg by faenza-icon-theme'
Adding 'diversion of /usr/share/dockmanager/data/skype_invisible.svg to /usr/share/dockmanager/data/skype_invisible.default.svg by faenza-icon-theme'
Adding 'diversion of /usr/share/dockmanager/data/skype_na.svg to /usr/share/dockmanager/data/skype_na.default.svg by faenza-icon-theme'
Adding 'diversion of /usr/share/dockmanager/data/skype_offline.svg to /usr/share/dockmanager/data/skype_offline.default.svg by faenza-icon-theme'
Adding 'diversion of /usr/share/dockmanager/data/skype_online.svg to /usr/share/dockmanager/data/skype_online.default.svg by faenza-icon-theme'
Adding 'diversion of /usr/share/dockmanager/data/skype_skypeme.svg to /usr/share/dockmanager/data/skype_skypeme.default.svg by faenza-icon-theme'
Unpacking replacement faenza-icon-theme ...
dpkg: error processing /var/cache/apt/archives/faenza-icon-theme_0.9_i386.deb (--unpack):
 trying to overwrite '/usr/share/icons/Faenza-Dark/apps/22/covergloobus.png', which is also in package faenza-icons-mono 0.9
Removing 'diversion of /usr/lib/rhythmbox/plugins/audioscrobbler/as-icon.png to /usr/lib/rhythmbox/plugins/audioscrobbler/as-icon.default.png by faenza-icon-theme'
dpkg-divert: rename involves overwriting `/usr/lib/rhythmbox/plugins/audioscrobbler/as-icon.png' with
  different file `/usr/lib/rhythmbox/plugins/audioscrobbler/as-icon.default.png', not allowed
Removing 'diversion of /usr/lib/rhythmbox/plugins/umusicstore/musicstore_icon.png to /usr/lib/rhythmbox/plugins/umusicstore/musicstore_icon.default.png by faenza-icon-theme'
Removing 'diversion of /usr/share/dockmanager/data/skype_away.svg to /usr/share/dockmanager/data/skype_away.default.svg by faenza-icon-theme'
Removing 'diversion of /usr/share/dockmanager/data/skype_dnd.svg to /usr/share/dockmanager/data/skype_dnd.default.svg by faenza-icon-theme'
Removing 'diversion of /usr/share/dockmanager/data/skype_invisible.svg to /usr/share/dockmanager/data/skype_invisible.default.svg by faenza-icon-theme'
Removing 'diversion of /usr/share/dockmanager/data/skype_na.svg to /usr/share/dockmanager/data/skype_na.default.svg by faenza-icon-theme'
Removing 'diversion of /usr/share/dockmanager/data/skype_offline.svg to /usr/share/dockmanager/data/skype_offline.default.svg by faenza-icon-theme'
Removing 'diversion of /usr/share/dockmanager/data/skype_online.svg to /usr/share/dockmanager/data/skype_online.default.svg by faenza-icon-theme'
Removing 'diversion of /usr/share/dockmanager/data/skype_skypeme.svg to /usr/share/dockmanager/data/skype_skypeme.default.svg by faenza-icon-theme'
No diversion 'diversion of /guake-notification.png by faenza-icon-theme', none removed.
Errors were encountered while processing:
 /var/cache/apt/archives/faenza-icon-theme_0.9_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

it says , error were encounteredn while processing the faenza-icon-theme.
what should I do to fix this error?

thanks in advanced

---

### Post by maizuddin35 on 2011-03-22
I get this thing fix already , here it goes.;

```
 sudo dpkg -i --force-all /var/cache/apt/archives/faenza-icon-theme_0.9_i386.deb 
```

here is the result :

```
sudo dpkg -i --force-all /var/cache/apt/archives/faenza-icon-theme_0.9_i386.deb 
[sudo] password for adibizuddin: 
(Reading database ... 236821 files and directories currently installed.)
Preparing to replace faenza-icon-theme 0.8 (using .../faenza-icon-theme_0.9_i386.deb) ...
Leaving 'diversion of /usr/lib/rhythmbox/plugins/audioscrobbler/as-icon.png to /usr/lib/rhythmbox/plugins/audioscrobbler/as-icon.default.png by faenza-icon-theme'
Adding 'diversion of /usr/lib/rhythmbox/plugins/umusicstore/musicstore_icon.png to /usr/lib/rhythmbox/plugins/umusicstore/musicstore_icon.default.png by faenza-icon-theme'
Adding 'diversion of /usr/share/dockmanager/data/skype_away.svg to /usr/share/dockmanager/data/skype_away.default.svg by faenza-icon-theme'
Adding 'diversion of /usr/share/dockmanager/data/skype_dnd.svg to /usr/share/dockmanager/data/skype_dnd.default.svg by faenza-icon-theme'
Adding 'diversion of /usr/share/dockmanager/data/skype_invisible.svg to /usr/share/dockmanager/data/skype_invisible.default.svg by faenza-icon-theme'
Adding 'diversion of /usr/share/dockmanager/data/skype_na.svg to /usr/share/dockmanager/data/skype_na.default.svg by faenza-icon-theme'
Adding 'diversion of /usr/share/dockmanager/data/skype_offline.svg to /usr/share/dockmanager/data/skype_offline.default.svg by faenza-icon-theme'
Adding 'diversion of /usr/share/dockmanager/data/skype_online.svg to /usr/share/dockmanager/data/skype_online.default.svg by faenza-icon-theme'
Adding 'diversion of /usr/share/dockmanager/data/skype_skypeme.svg to /usr/share/dockmanager/data/skype_skypeme.default.svg by faenza-icon-theme'
Unpacking replacement faenza-icon-theme ...
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/icons/Faenza-Dark/apps/22/covergloobus.png', which is also in package faenza-icons-mono 0.9
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/icons/Faenza-Dark/apps/22/me-tv.png', which is also in package faenza-icons-mono 0.9
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/icons/Faenza/apps/22/me-tv.png', which is also in package faenza-icons-mono 0.9
Removing 'diversion of /usr/lib/rhythmbox/plugins/audioscrobbler/as-icon.png to /usr/lib/rhythmbox/plugins/audioscrobbler/as-icon.default.png by faenza-icon-theme'
dpkg-divert: rename involves overwriting `/usr/lib/rhythmbox/plugins/audioscrobbler/as-icon.png' with
  different file `/usr/lib/rhythmbox/plugins/audioscrobbler/as-icon.default.png', not allowed
Removing 'diversion of /usr/lib/rhythmbox/plugins/umusicstore/musicstore_icon.png to /usr/lib/rhythmbox/plugins/umusicstore/musicstore_icon.default.png by faenza-icon-theme'
dpkg-divert: rename involves overwriting `/usr/lib/rhythmbox/plugins/umusicstore/musicstore_icon.png' with
  different file `/usr/lib/rhythmbox/plugins/umusicstore/musicstore_icon.default.png', not allowed
Removing 'diversion of /usr/share/dockmanager/data/skype_away.svg to /usr/share/dockmanager/data/skype_away.default.svg by faenza-icon-theme'
dpkg-divert: rename involves overwriting `/usr/share/dockmanager/data/skype_away.svg' with
  different file `/usr/share/dockmanager/data/skype_away.default.svg', not allowed
Removing 'diversion of /usr/share/dockmanager/data/skype_dnd.svg to /usr/share/dockmanager/data/skype_dnd.default.svg by faenza-icon-theme'
dpkg-divert: rename involves overwriting `/usr/share/dockmanager/data/skype_dnd.svg' with
  different file `/usr/share/dockmanager/data/skype_dnd.default.svg', not allowed
Removing 'diversion of /usr/share/dockmanager/data/skype_invisible.svg to /usr/share/dockmanager/data/skype_invisible.default.svg by faenza-icon-theme'
dpkg-divert: rename involves overwriting `/usr/share/dockmanager/data/skype_invisible.svg' with
  different file `/usr/share/dockmanager/data/skype_invisible.default.svg', not allowed
Removing 'diversion of /usr/share/dockmanager/data/skype_na.svg to /usr/share/dockmanager/data/skype_na.default.svg by faenza-icon-theme'
dpkg-divert: rename involves overwriting `/usr/share/dockmanager/data/skype_na.svg' with
  different file `/usr/share/dockmanager/data/skype_na.default.svg', not allowed
Removing 'diversion of /usr/share/dockmanager/data/skype_offline.svg to /usr/share/dockmanager/data/skype_offline.default.svg by faenza-icon-theme'
dpkg-divert: rename involves overwriting `/usr/share/dockmanager/data/skype_offline.svg' with
  different file `/usr/share/dockmanager/data/skype_offline.default.svg', not allowed
Removing 'diversion of /usr/share/dockmanager/data/skype_online.svg to /usr/share/dockmanager/data/skype_online.default.svg by faenza-icon-theme'
dpkg-divert: rename involves overwriting `/usr/share/dockmanager/data/skype_online.svg' with
  different file `/usr/share/dockmanager/data/skype_online.default.svg', not allowed
Removing 'diversion of /usr/share/dockmanager/data/skype_skypeme.svg to /usr/share/dockmanager/data/skype_skypeme.default.svg by faenza-icon-theme'
dpkg-divert: rename involves overwriting `/usr/share/dockmanager/data/skype_skypeme.svg' with
  different file `/usr/share/dockmanager/data/skype_skypeme.default.svg', not allowed
dpkg: warning: subprocess old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
Removing 'diversion of /usr/lib/rhythmbox/plugins/audioscrobbler/as-icon.png to /usr/lib/rhythmbox/plugins/audioscrobbler/as-icon.default.png by faenza-icon-theme'
dpkg-divert: rename involves overwriting `/usr/lib/rhythmbox/plugins/audioscrobbler/as-icon.png' with
  different file `/usr/lib/rhythmbox/plugins/audioscrobbler/as-icon.default.png', not allowed
Removing 'diversion of /usr/lib/rhythmbox/plugins/umusicstore/musicstore_icon.png to /usr/lib/rhythmbox/plugins/umusicstore/musicstore_icon.default.png by faenza-icon-theme'
dpkg-divert: rename involves overwriting `/usr/lib/rhythmbox/plugins/umusicstore/musicstore_icon.png' with
  different file `/usr/lib/rhythmbox/plugins/umusicstore/musicstore_icon.default.png', not allowed
Removing 'diversion of /usr/share/dockmanager/data/skype_away.svg to /usr/share/dockmanager/data/skype_away.default.svg by faenza-icon-theme'
dpkg-divert: rename involves overwriting `/usr/share/dockmanager/data/skype_away.svg' with
  different file `/usr/share/dockmanager/data/skype_away.default.svg', not allowed
Removing 'diversion of /usr/share/dockmanager/data/skype_dnd.svg to /usr/share/dockmanager/data/skype_dnd.default.svg by faenza-icon-theme'
dpkg-divert: rename involves overwriting `/usr/share/dockmanager/data/skype_dnd.svg' with
  different file `/usr/share/dockmanager/data/skype_dnd.default.svg', not allowed
Removing 'diversion of /usr/share/dockmanager/data/skype_invisible.svg to /usr/share/dockmanager/data/skype_invisible.default.svg by faenza-icon-theme'
dpkg-divert: rename involves overwriting `/usr/share/dockmanager/data/skype_invisible.svg' with
  different file `/usr/share/dockmanager/data/skype_invisible.default.svg', not allowed
Removing 'diversion of /usr/share/dockmanager/data/skype_na.svg to /usr/share/dockmanager/data/skype_na.default.svg by faenza-icon-theme'
dpkg-divert: rename involves overwriting `/usr/share/dockmanager/data/skype_na.svg' with
  different file `/usr/share/dockmanager/data/skype_na.default.svg', not allowed
Removing 'diversion of /usr/share/dockmanager/data/skype_offline.svg to /usr/share/dockmanager/data/skype_offline.default.svg by faenza-icon-theme'
dpkg-divert: rename involves overwriting `/usr/share/dockmanager/data/skype_offline.svg' with
  different file `/usr/share/dockmanager/data/skype_offline.default.svg', not allowed
Removing 'diversion of /usr/share/dockmanager/data/skype_online.svg to /usr/share/dockmanager/data/skype_online.default.svg by faenza-icon-theme'
dpkg-divert: rename involves overwriting `/usr/share/dockmanager/data/skype_online.svg' with
  different file `/usr/share/dockmanager/data/skype_online.default.svg', not allowed
Removing 'diversion of /usr/share/dockmanager/data/skype_skypeme.svg to /usr/share/dockmanager/data/skype_skypeme.default.svg by faenza-icon-theme'
dpkg-divert: rename involves overwriting `/usr/share/dockmanager/data/skype_skypeme.svg' with
  different file `/usr/share/dockmanager/data/skype_skypeme.default.svg', not allowed
No diversion 'diversion of /guake-notification.png by faenza-icon-theme', none removed.
dpkg: ... it looks like that went OK.
Setting up faenza-icon-theme (0.9) ...

```

here i just need to reinstall back manually and with force, so that it can be fix back :)

---

### Post by arqbrulo on 2011-03-23
Thanks! That helped me out.

---

### Post by maqtanim on 2011-03-25
Thanks a lot! It worked like a charm for me! :)

---

### Post by bookcrazy on 2011-04-04
When I entered

```
 sudo dpkg -i --force-all /var/cache/apt/archives/faenza-icon-theme_0.9_i386.deb
```

I got this:


```
dpkg: error processing /var/cache/apt/archives/faenza-icon-theme_0.9_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/faenza-icon-theme_0.9_i386.deb
```

Any ideas?

---

### Post by bookcrazy on 2011-04-12
OK, so I have tried and tried and I am still getting this:


```
:~$ sudo apt-get upgrade
Get:1 http://ppa.launchpad.net/tiheum/equinox/ubuntu/ lucid/main faenza-icon-theme 0.9-ubuntu2 [13.9MB]
Fetched 13.9MB in 5min 46s (40.0kB/s)                                                                                                                                   
(Reading database ... 170151 files and directories currently installed.)
Preparing to replace faenza-icon-theme 0.8 (using .../faenza-icon-theme_0.9-ubuntu2_i386.deb) ...
Adding `diversion of /usr/lib/rhythmbox/plugins/audioscrobbler/as-icon.png to /usr/lib/rhythmbox/plugins/audioscrobbler/as-icon.default.png by faenza-icon-theme'
Adding `diversion of /usr/lib/rhythmbox/plugins/umusicstore/musicstore_icon.png to /usr/lib/rhythmbox/plugins/umusicstore/musicstore_icon.default.png by faenza-icon-theme'
Adding `diversion of /usr/share/dockmanager/data/skype_away.svg to /usr/share/dockmanager/data/skype_away.default.svg by faenza-icon-theme'
Adding `diversion of /usr/share/dockmanager/data/skype_dnd.svg to /usr/share/dockmanager/data/skype_dnd.default.svg by faenza-icon-theme'
Adding `diversion of /usr/share/dockmanager/data/skype_invisible.svg to /usr/share/dockmanager/data/skype_invisible.default.svg by faenza-icon-theme'
Adding `diversion of /usr/share/dockmanager/data/skype_na.svg to /usr/share/dockmanager/data/skype_na.default.svg by faenza-icon-theme'
Adding `diversion of /usr/share/dockmanager/data/skype_offline.svg to /usr/share/dockmanager/data/skype_offline.default.svg by faenza-icon-theme'
Adding `diversion of /usr/share/dockmanager/data/skype_online.svg to /usr/share/dockmanager/data/skype_online.default.svg by faenza-icon-theme'
Adding `diversion of /usr/share/dockmanager/data/skype_skypeme.svg to /usr/share/dockmanager/data/skype_skypeme.default.svg by faenza-icon-theme'
Unpacking replacement faenza-icon-theme ...
dpkg: error processing /var/cache/apt/archives/faenza-icon-theme_0.9-ubuntu2_i386.deb (--unpack):
 trying to overwrite '/usr/share/icons/Faenza-Dark/apps/22/me-tv.png', which is also in package faenza-icons-mono 0:0.9
Removing `diversion of /usr/lib/rhythmbox/plugins/audioscrobbler/as-icon.png to /usr/lib/rhythmbox/plugins/audioscrobbler/as-icon.default.png by faenza-icon-theme'
Removing `diversion of /usr/lib/rhythmbox/plugins/umusicstore/musicstore_icon.png to /usr/lib/rhythmbox/plugins/umusicstore/musicstore_icon.default.png by faenza-icon-theme'
Removing `diversion of /usr/share/dockmanager/data/skype_away.svg to /usr/share/dockmanager/data/skype_away.default.svg by faenza-icon-theme'
Removing `diversion of /usr/share/dockmanager/data/skype_dnd.svg to /usr/share/dockmanager/data/skype_dnd.default.svg by faenza-icon-theme'
Removing `diversion of /usr/share/dockmanager/data/skype_invisible.svg to /usr/share/dockmanager/data/skype_invisible.default.svg by faenza-icon-theme'
Removing `diversion of /usr/share/dockmanager/data/skype_na.svg to /usr/share/dockmanager/data/skype_na.default.svg by faenza-icon-theme'
Removing `diversion of /usr/share/dockmanager/data/skype_offline.svg to /usr/share/dockmanager/data/skype_offline.default.svg by faenza-icon-theme'
Removing `diversion of /usr/share/dockmanager/data/skype_online.svg to /usr/share/dockmanager/data/skype_online.default.svg by faenza-icon-theme'
Removing `diversion of /usr/share/dockmanager/data/skype_skypeme.svg to /usr/share/dockmanager/data/skype_skypeme.default.svg by faenza-icon-theme'
No diversion `diversion of /guake-notification.png by faenza-icon-theme', none removed
Errors were encountered while processing:
 /var/cache/apt/archives/faenza-icon-theme_0.9-ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

When I entered

```
 sudo dpkg -i --force-all /var/cache/apt/archives/faenza-icon-theme_0.9_i386.deb
```

I got

```
dpkg: error processing /var/cache/apt/archives/faenza-icon-theme_0.9_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/faenza-icon-theme_0.9_i386.deb
```

Can anyone tell me what I'm doing wrong / not doing right?

Cheers

---

### Post by Krytarik on 2011-04-12
> **bookcrazy said:**
> 
```
Errors were encountered while processing:
 [COLOR=Blue]**/var/cache/apt/archives/faenza-icon-theme_0.9[COLOR=Red]-ubuntu2[/COLOR]_i386.deb**[/COLOR]
E: Sub-process /usr/bin/dpkg returned an error code (1)
```When I entered

```
 sudo dpkg -i --force-all /var/cache/apt/archives/faenza-icon-theme_0.9_i386.deb
```I got

```
dpkg: error processing /var/cache/apt/archives/faenza-icon-theme_0.9_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/faenza-icon-theme_0.9_i386.deb
```Can anyone tell me what I'm doing wrong / not doing right?

In your case it is:
```
sudo dpkg -i --force-all /var/cache/apt/archives/faenza-icon-theme_0.9-ubuntu2_i386.deb
```Greetings.

---

### Post by bookcrazy on 2011-04-14
> **Krytarik said:**
> In your case it is:
```
sudo dpkg -i --force-all /var/cache/apt/archives/faenza-icon-theme_0.9-ubuntu2_i386.deb
```Greetings.

Thanks a million! It worked like a charm.:D

---

