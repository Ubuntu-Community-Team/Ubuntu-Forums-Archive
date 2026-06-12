---
title: "synaptic package manager disappear"
date: 2012-06-21
forum: General Help
---

### Post by Narjess on 2012-06-21
Hi All,
I don't know what i did and suddenly i didn't find either the wireless icon in the label nor the synaptic package manager

please help ](*,)

---

### Post by ajgreeny on 2012-06-21
What version of ubuntu are you running?

In 12.04 (and I think 11.10) synaptic is not included in the default installation, so you may need to install it yourself with ```
sudo apt-get install synaptic
```
I'm not so sure about the wireless icon but see if nm-applet is running or installed with ```
ps aux | grep nm-applet
```or look in system-monitor.

---

### Post by Narjess on 2012-06-21
I am using ubuntu 10.10
the synaptic were there but I don't know where it desappears :(

---

### Post by rukiaEnix on 2012-06-21
Maybe trying to find it:

```

sudo find / -name synaptic

```

---

### Post by Narjess on 2012-06-21
Thank you very much for the reply 
but it still not working :frown:

---

### Post by rukiaEnix on 2012-06-21
What didn't work finding it or installing it with apt-get as ajgreeny told you?

---

### Post by Narjess on 2012-06-21
when trying to find it, it returns /var/lib/synaptic

and the installation doesn't work also,

is the problem clear ? when I open system -> administration I can't find the synaptic package manager 

excuse me for my bad english

---

### Post by rukiaEnix on 2012-06-21
What happens if you just type at the command line:

```

sudo synaptic

```or

```

sudo /var/lib/synaptic

```

---

### Post by ajgreeny on 2012-06-21
Try the command 
```
whereis synaptic
``` which should produce output of
```
synaptic: /usr/sbin/synaptic /usr/share/synaptic /usr/share/man/man8/synaptic.8.gz
```or similar.

Or command ```
which synaptic
``` which should give ```
/usr/sbin/synaptic
```

@ rukiaEnix.  Always use **gksu** or **gksudo** for a gui application not **sudo**, or you could possibly lock yourself out of the system.

@ OP  Try ```
gksudo synaptic
```

---

### Post by Narjess on 2012-06-21
narjess@narjess-Satellite-L505D:~$ sudo synaptic
[sudo] password for narjess: 
sudo: synaptic: command not found



narjess@narjess-Satellite-L505D:~$ sudo /var/lib/synaptic
sudo: /var/lib/synaptic: command not found

---

### Post by rukiaEnix on 2012-06-21
And what about trying the installation?... Does it also gives you an error?

---

### Post by Narjess on 2012-06-21
I tried the instructions; but it seems not giving solution :( 


narjess@narjess-Satellite-L505D:~$ whereis synaptic
synaptic:
narjess@narjess-Satellite-L505D:~$ synaptic: /usr/sbin/synaptic /usr/share/synaptic /usr/share/man/man8

/usr/bin/python: can't find '__main__.py' in '/usr/share/command-not-found'
narjess@narjess-Satellite-L505D:~$ 
narjess@narjess-Satellite-L505D:~$ which synaptic
narjess@narjess-Satellite-L505D:~$ /usr/sbin/synaptic
bash: /usr/sbin/synaptic: No such file or directory
narjess@narjess-Satellite-L505D:~$ /usr/sbin/synaptic
bash: /usr/sbin/synaptic: No such file or directory
narjess@narjess-Satellite-L505D:~$ gksudo synaptic

sorry for being late because I have to restart every time such I lost my connection in ubuntu also :( :(

---

### Post by rukiaEnix on 2012-06-21
....but what about:

```

sudo apt-get install synaptic

```

---

### Post by Narjess on 2012-06-21
it gives me a message ending with :

N: Ignoring file 'apt-build' in directory '/etc/apt/sources.list.d/' as it has no filename extension
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by rukiaEnix on 2012-06-21
...you have to first update apt-get, also you should check your repos

---

### Post by Narjess on 2012-06-21
repos ? how ?:confused:
and for the update should I type : sudo apt-get update ?

---

### Post by rukiaEnix on 2012-06-21
Yes, you should type that.

You need to update first so apt-get can get the list of packages that it can install.

---

### Post by Narjess on 2012-06-21
the updqte gives me thoses long errors :


Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick Release.gpg
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates Release.gpg
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg
  Could not resolve 'archive.canonical.com'
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en
  Could not resolve 'archive.canonical.com'
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US
  Could not resolve 'archive.canonical.com'
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg
  Could not resolve 'extras.ubuntu.com'
Err [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en
  Could not resolve 'extras.ubuntu.com'
Err [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US
  Could not resolve 'extras.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg
  Could not resolve 'ppa.launchpad.net'
Err [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/) maverick/main Translation-en
  Could not resolve 'ppa.launchpad.net'
Err [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/) maverick/main Translation-en_US
  Could not resolve 'ppa.launchpad.net'
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg
  Could not resolve 'ppa.launchpad.net'
Err [http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu/](http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu/) maverick/main Translation-en
  Could not resolve 'ppa.launchpad.net'
Err [http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu/](http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu/) maverick/main Translation-en_US
  Could not resolve 'ppa.launchpad.net'
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://hinrg.cs.jhu.edu](http://hinrg.cs.jhu.edu) maverick Release.gpg
  Could not resolve 'hinrg.cs.jhu.edu'
Err [http://hinrg.cs.jhu.edu/tinyos/](http://hinrg.cs.jhu.edu/tinyos/) maverick/main Translation-en
  Could not resolve 'hinrg.cs.jhu.edu'
Err [http://hinrg.cs.jhu.edu/tinyos/](http://hinrg.cs.jhu.edu/tinyos/) maverick/main Translation-en_US
  Could not resolve 'hinrg.cs.jhu.edu'
Ign file: apt-build Release.gpg
Ign file:/var/cache/apt-build/repository/ apt-build/main Translation-en
Ign file:/var/cache/apt-build/repository/ apt-build/main Translation-en_US
Get:1 file: apt-build Release [89B]
Ign file: apt-build/main i386 Packages
Ign file: apt-build/main i386 Packages
Reading package lists... Done
N: Ignoring file 'apt-build' in directory '/etc/apt/sources.list.d/' as it has no filename extension
W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://fr.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Could not resolve 'fr.archive.ubuntu.com'

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Could not resolve 'fr.archive.ubuntu.com'

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Could not resolve 'fr.archive.ubuntu.com'

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2)  Could not resolve 'fr.archive.ubuntu.com'

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_US.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'fr.archive.ubuntu.com'

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2)  Could not resolve 'fr.archive.ubuntu.com'

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_US.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'fr.archive.ubuntu.com'

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2)  Could not resolve 'fr.archive.ubuntu.com'

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_US.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_US.bz2)  Could not resolve 'fr.archive.ubuntu.com'

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg](http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg)  Could not resolve 'fr.archive.ubuntu.com'

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2)  Could not resolve 'fr.archive.ubuntu.com'

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'fr.archive.ubuntu.com'

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2)  Could not resolve 'fr.archive.ubuntu.com'

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'fr.archive.ubuntu.com'

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2)  Could not resolve 'fr.archive.ubuntu.com'

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'fr.archive.ubuntu.com'

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2)  Could not resolve 'fr.archive.ubuntu.com'

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'fr.archive.ubuntu.com'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg](http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg)  Could not resolve 'archive.canonical.com'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2](http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2)  Could not resolve 'archive.canonical.com'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en_US.bz2)  Could not resolve 'archive.canonical.com'

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Could not resolve 'extras.ubuntu.com'

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Could not resolve 'extras.ubuntu.com'

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Could not resolve 'extras.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/dists/maverick/Release.gpg)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://hinrg.cs.jhu.edu/tinyos/dists/maverick/Release.gpg](http://hinrg.cs.jhu.edu/tinyos/dists/maverick/Release.gpg)  Could not resolve 'hinrg.cs.jhu.edu'

W: Failed to fetch [http://hinrg.cs.jhu.edu/tinyos/dists/maverick/main/i18n/Translation-en.bz2](http://hinrg.cs.jhu.edu/tinyos/dists/maverick/main/i18n/Translation-en.bz2)  Could not resolve 'hinrg.cs.jhu.edu'

W: Failed to fetch [http://hinrg.cs.jhu.edu/tinyos/dists/maverick/main/i18n/Translation-en_US.bz2](http://hinrg.cs.jhu.edu/tinyos/dists/maverick/main/i18n/Translation-en_US.bz2)  Could not resolve 'hinrg.cs.jhu.edu'

W: Failed to fetch [http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu/dists/maverick/Release.gpg)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Could not resolve 'ppa.launchpad.net'

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by rukiaEnix on 2012-06-21
This question maybe stupid but, do you have Internet connection?

also try other Ubuntu repos

---

### Post by Narjess on 2012-06-21
No ! not stupid at all
i have not internet connection as i said from the beginning i lost my icon for wireless connection in the panel

it seems that it is me the stupid but i am very new and i have no idea about all of that

---

### Post by jmfal on 2012-06-21
Click on the gear> top right next to your name

Click system settings

Click on network

get connected to internet

---

### Post by jmfal on 2012-06-21
10.10 is at End Of Life
You  are not going to be able to get updates for Maverick

How are you on the forum if you don't have an internet connection?????????

---

### Post by Narjess on 2012-06-22
Hi,

Thank you for the reply :)

I am swapping between ubuntu and windows for having connection :(

I didn't find what do you recommended me :confused:

I will join a screenshot :

---

### Post by jmfal on 2012-06-22
It's going to be hard to get advice for you wireless problems when the title of your thread only mentions "synaptic."
As I said before 10.10 is end of life and is no longer getting updates from ubuntu, you should upgrade to 11.04  and you will be good till 12.10 is released, then 11.04 will be at end of life.
I would try to be hard wired (ethernet cable)when upgrading to cut down the chances of loosing your connection.
If you want to do this, here is a link, click on "read the release notes" in the first line then scroll down to "from 10.10 to 11.04 " click on "NattyUpgrades" and follow instructions:

[http://www.ubuntu.com/download/desktop/upgrade](http://www.ubuntu.com/download/desktop/upgrade)

Here is a link to see if your wireless card is supported:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Here is a link to help you set up your wireless:

[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

---

### Post by rukiaEnix on 2012-06-22
I agree with jmal you should upgrade your Ubuntu or you'll have trouble updating your repos. 

But also you may have a problem with Internet connection.

What does this command give you:

```

ifconfig

```

---

### Post by Narjess on 2012-06-23
Hi 
if config gives me :


narjess@narjess-Satellite-L505D:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)



I don't prefer to upgrade my ubuntu as I will work with TinyOs and Tossim simulator and I found problems when I installed ubuntu 12.04

Thank you any way

---

### Post by rukiaEnix on 2012-06-23
Well, all the problem is that you don't have Internet connection.

If you are having problems with your wireless why don't you try using wired connection? So you can download Synaptic

---

