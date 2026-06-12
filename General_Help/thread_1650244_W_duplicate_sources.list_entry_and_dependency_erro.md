---
title: "W: duplicate sources.list entry and dependency errors"
date: 2010-12-21
forum: General Help
---

### Post by iosuna86 on 2010-12-21
I am running Ubuntu 10.10 and I get the following message after typing:

```
sudo apt-get update
``````
W: Duplicate sources.list entry http://packages.medibuntu.org/ maverick/free i386 Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_maverick_free_binary-i386_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org/ maverick/non-free i386 Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_maverick_non-free_binary-i386_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_maverick_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```Here is the content of my sources.list:


```
###### Ubuntu Main Repos
deb http://mirror.ousli.org/ubuntu/ maverick main restricted universe multiverse
deb-src http://mirror.ousli.org/ubuntu/ maverick main restricted universe multiverse

###### Ubuntu Update Repos
deb http://mirror.ousli.org/ubuntu/ maverick-security main restricted universe multiverse
deb http://mirror.ousli.org/ubuntu/ maverick-updates main restricted universe multiverse
deb-src http://mirror.ousli.org/ubuntu/ maverick-security main restricted universe multiverse
deb-src http://mirror.ousli.org/ubuntu/ maverick-updates main restricted universe multiverse

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### AWN (Avant Window Navigator) Testing Packages - http://awn-project.org/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BF810CD5
deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu maverick main

#### Medibuntu - http://www.medibuntu.org/ 
## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
deb http://packages.medibuntu.org/ maverick free non-free

#### Themes for GNOME and Ubuntu - https://edge.launchpad.net/~bisigi/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 881574DE
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu maverick main

#### Ubuntu Tweak - http://ubuntu-tweak.com/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb http://ppa.launchpad.net/tualatrix/ubuntu maverick main

#### VLC Media Player  - http://www.videolan.org/vlc/
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40130828
deb http://ppa.launchpad.net/c-korn/ppa/ubuntu maverick main

#### X Updates - https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu maverick main


####### 3rd Party Source Repos

#### AWN (Avant Window Navigator) Testing Packages (Source) - http://awn-project.org/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BF810CD5
deb-src http://ppa.launchpad.net/awn-testing/ppa/ubuntu maverick main

#### Medibuntu (Source) - http://www.medibuntu.org/ 
## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
deb-src http://packages.medibuntu.org/ maverick free non-free

#### Themes for GNOME and Ubuntu (Source) - https://edge.launchpad.net/~bisigi/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 881574DE
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu maverick main

#### Ubuntu Tweak (Source) - http://ubuntu-tweak.com/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb-src http://ppa.launchpad.net/tualatrix/ubuntu maverick main

#### VLC Media Player  (Source) - http://www.videolan.org/vlc/
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40130828
deb-src http://ppa.launchpad.net/c-korn/ppa/ubuntu maverick main

#### X Updates (Source) - https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu maverick main


deb http://archive.getdeb.net/ubuntu maverick-getdeb games
deb-src http://archive.getdeb.net/ubuntu maverick-getdeb games
```As far as I can tell, there aren't any duplicate entries. Also, when I run Update Manager from Administration, no error is reported.

I am running into problems installing FatRat. It says that libqt4 can't be installed and when I try to install libqt4-core and all the dependencies, there is an error. There are no broken packages... Does it have anything to do with this problem?

What should I do?

Thanks in advance.

EDIT: here is what I get while trying to install libqt4 from Synaptic:

"Could not mark all packages for installation or upgrade"
The following packages have (...) in the preferences.

```
libqt4-core:
  Depends: libqtcore4 (=4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is to be installed
  Depends: libqt4-network (=4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is to be installed
  Depends: libqt4-script (=4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is to be installed
  Depends: libqt4-xml (=4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is to be installed
  Depends: libqt4-dbus (=4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is to be installed
 Depends: libqt4-test but it is not going to be installed
```

---

### Post by plucky on 2010-12-21
Post output of ```
ls -l /etc/apt/sources.list.d/
``` is where PPA and Medibuntu repos install.

Good Luck

---

### Post by iosuna86 on 2010-12-21
Hey, thanks for the reply.

Here it is:

```
total 68
-rw-r--r-- 1 root root 174 2010-12-21 14:52 am-monkeyd-nautilus-elementary-ppa-maverick.list
-rw-r--r-- 1 root root 174 2010-12-21 14:52 am-monkeyd-nautilus-elementary-ppa-maverick.list.save
-rw-r--r-- 1 root root 140 2010-12-21 14:52 elementaryart-ppa-maverick.list
-rw-r--r-- 1 root root 140 2010-12-21 14:52 elementaryart-ppa-maverick.list.save
-rw-r--r-- 1 root root 144 2010-12-21 14:52 jd-team-jdownloader-maverick.list
-rw-r--r-- 1 root root 285 2010-12-21 14:52 medibuntu.list
-rw-r--r-- 1 root root 285 2010-12-21 14:52 medibuntu.list.save
-rw-r--r-- 1 root root 130 2010-12-21 14:52 team-xbmc-ppa-maverick.list
-rw-r--r-- 1 root root 130 2010-12-21 14:52 team-xbmc-ppa-maverick.list.save
-rw-r--r-- 1 root root 134 2010-12-21 14:52 tiheum-equinox-maverick.list
-rw-r--r-- 1 root root 134 2010-12-21 14:52 tiheum-equinox-maverick.list.save
-rw-r--r-- 1 root root 132 2010-12-21 14:52 tualatrix-ppa-maverick.list
-rw-r--r-- 1 root root 132 2010-12-21 14:52 tualatrix-ppa-maverick.list.save
-rw-r--r-- 1 root root  92 2010-12-21 14:52 ubuntu-tweak-stable.list
-rw-r--r-- 1 root root  92 2010-12-21 14:52 ubuntu-tweak-stable.list.save
-rw-r--r-- 1 root root 136 2010-12-21 14:52 ubuntu-wine-ppa-maverick.list
-rw-r--r-- 1 root root 136 2010-12-21 14:52 ubuntu-wine-ppa-maverick.list.save

```

---

### Post by plucky on 2010-12-21
> **iosuna86 said:**
> Hey, thanks for the reply.

Here it is:

```
total 68
-rw-r--r-- 1 root root 174 2010-12-21 14:52 am-monkeyd-nautilus-elementary-ppa-maverick.list
-rw-r--r-- 1 root root 174 2010-12-21 14:52 am-monkeyd-nautilus-elementary-ppa-maverick.list.save
-rw-r--r-- 1 root root 140 2010-12-21 14:52 elementaryart-ppa-maverick.list
-rw-r--r-- 1 root root 140 2010-12-21 14:52 elementaryart-ppa-maverick.list.save
-rw-r--r-- 1 root root 144 2010-12-21 14:52 jd-team-jdownloader-maverick.list
[color=red]-rw-r--r-- 1 root root 285 2010-12-21 14:52 medibuntu.list[/color]
-rw-r--r-- 1 root root 285 2010-12-21 14:52 medibuntu.list.save
-rw-r--r-- 1 root root 130 2010-12-21 14:52 team-xbmc-ppa-maverick.list
-rw-r--r-- 1 root root 130 2010-12-21 14:52 team-xbmc-ppa-maverick.list.save
-rw-r--r-- 1 root root 134 2010-12-21 14:52 tiheum-equinox-maverick.list
-rw-r--r-- 1 root root 134 2010-12-21 14:52 tiheum-equinox-maverick.list.save
[color=red]-rw-r--r-- 1 root root 132 2010-12-21 14:52 tualatrix-ppa-maverick.list[/color]
-rw-r--r-- 1 root root 132 2010-12-21 14:52 tualatrix-ppa-maverick.list.save
-rw-r--r-- 1 root root  92 2010-12-21 14:52 ubuntu-tweak-stable.list
-rw-r--r-- 1 root root  92 2010-12-21 14:52 ubuntu-tweak-stable.list.save
-rw-r--r-- 1 root root 136 2010-12-21 14:52 ubuntu-wine-ppa-maverick.list
-rw-r--r-- 1 root root 136 2010-12-21 14:52 ubuntu-wine-ppa-maverick.list.save

```

As shown above,you have those repositories twice is the reason you are getting the warning message.

The proper place to remove them is from the sources.list as they should be in the sources.list.d directory.

To edit the file ```
gksudo gedit /etc/apt/sources.list
``` and put a # in front of ```
deb http://packages.medibuntu.org/ maverick free non-free
deb http://ppa.launchpad.net/tualatrix/ubuntu maverick main

``` or delete them.
You might also have to do the **deb-src** lines as well.

Or open **Software Sources** and un-tick one of the two repositories.

Good Luck

---

### Post by iosuna86 on 2010-12-22
Hi!

I just did what you told me. I still get this:

```
W: Duplicate sources.list entry http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_maverick_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

I put the # to both repos but I still get that. 

When I comment the deb-src for tualatrix, no problem is reported.

But I still have one question. If I have commented both medibuntu repo and tualatrix repos, how am I going to get their updates?

Thanks for helping me out.

---

### Post by Elfy on 2010-12-22
> But I still have one question. If I have commented both medibuntu repo and tualatrix repos, how am I going to get their updates?Because you still have their specific source lists in source.list.d/

---

### Post by Verbeck on 2010-12-22
> **iosuna86 said:**
> 
But I still have one question. If I have commented both medibuntu repo and tualatrix repos, how am I going to get their updates?

you should still have them in /etc/apt/sources.list.d/

---

### Post by iosuna86 on 2010-12-22
Thanks forestpiskie[[COLOR=#D40000]****[/COLOR]]("http://ubuntuforums.org/member.php?u=610428") and Verbeck.

Sorry for my ignorance, but that brings another question. If there is a sources.list.d, why do we have to have the repos in the sources.list file?

It may be a dumb question, but I am kinda new to Ubuntu.

Thanks.

---

### Post by plucky on 2010-12-22
> **iosuna86 said:**
> Thanks forestpiskie[[COLOR=#D40000]****[/COLOR]]("http://ubuntuforums.org/member.php?u=610428") and Verbeck.

Sorry for my ignorance, but that brings another question. If there is a sources.list.d, why do we have to have the repos in the sources.list file?

It may be a dumb question, but I am kinda new to Ubuntu.

Thanks.

The Repositories in the sources.list should be the ones maintained by Canonical,the ones in sources.list.d are maintained by third parties.
i.e PPA's and Google.

Good Luck

---

### Post by iosuna86 on 2010-12-22
> **plucky said:**
> The Repositories in the sources.list should be the ones maintained by Canonical,the ones in sources.list.d are maintained by third parties.
i.e PPA's and Google.

Good Luck

Hi again!

So then, the Ubuntu Sources List Generator ([http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)) that I thought it was pretty good to use, is pretty much useless. It has more than Canonical repositories (it has google, ubuntu-tweak,...)

So whenever I want to add repos, I need to do it thru the terminal or thru Software Sources, right?

Should I edit my sources.list to the default one (link?)? Or, could you guys provide me with a reasonable sources.list (or a link to it)?

Thanks again!

EDIT: Also, what about this?

"Could not mark all packages for installation or upgrade"
The following packages have (...) in the preferences.
```
libqt4-core: 
Depends: libqtcore4 (=4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is to be installed
Depends: libqt4-network (=4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is to be installed
Depends: libqt4-script (=4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is to be installed
Depends: libqt4-xml (=4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is to be installed
Depends: libqt4-dbus (=4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is to be installed
Depends: libqt4-test but it is not going to be installed
```

Does it have anything to do with the mess I have for a sources.list?

---

### Post by plucky on 2010-12-22
> So then, the Ubuntu Sources List Generator ([http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)) that I thought it was pretty good to use, is pretty much useless. It has more than Canonical repositories (it has google, ubuntu-tweak,...)

That resource was never designed to be used for adding third party repositories. Use Software Sources.

> EDIT: Also, what about this?

"Could not mark all packages for installation or upgrade"
The following packages have (...) in the preferences.

Have you reloaded the index files with ```
sudo apt-get update
```?

If that doesn't work,try changing the server to the **Main Server**, reload the index files and try again.


Good Luck

---

### Post by iosuna86 on 2010-12-22
plucky

I did sudo apt-get update and I get this again (this is getting frustrating):

```
W: Duplicate sources.list entry http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_maverick_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```It's funny because I didn't found any problems before after commenting the deb lines I was told. They appear unchecked in Software Sources too! 

Why does the update still try to fetch those entries?

Is this related to the libqt4 thing?

Thanks for your time.

EDIT: by the way, which sources.list do you recommend me to have? can you provide me with a link? Thanks.

---

### Post by iosuna86 on 2010-12-22
Nevermind what I have just said. I forgot to see that I had two Ubuntu Tweak repos checked. My bad.

However, I still don't understand what's issue behind this:

```
sudo apt-get install fatrat
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 fatrat : Depends: libqt4-help (>= 4:4.5.3) but it is not going to be installed
          Depends: libqt4-svg (>= 4:4.5.3) but it is not going to be installed
          Depends: libqt4-sql-sqlite but it is not going to be installed
E: Broken packages
```


```
sudo apt-get install libqt4-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libqt4-core : Depends: libqtcore4 (= 4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is to be installed
               Depends: libqt4-network (= 4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is to be installed
               Depends: libqt4-script (= 4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is to be installed
               Depends: libqt4-xml (= 4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is to be installed
               Depends: libqt4-dbus (= 4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is to be installed
               Depends: libqt4-test (= 4:4.7.0-0ubuntu4) but it is not going to be installed
E: Broken packages

```

---

### Post by Verbeck on 2010-12-22
could you try
*sudo apt-get install -f*

---

### Post by iosuna86 on 2010-12-22
> **Verbeck said:**
> could you try
*sudo apt-get install -f*

*sudo apt-get install -f fatrat*

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 fatrat : Depends: libqt4-help (>= 4:4.5.3) but it is not going to be installed
          Depends: libqt4-svg (>= 4:4.5.3) but it is not going to be installed
          Depends: libqt4-sql-sqlite but it is not going to be installed
E: Broken packages
```

Same thing...

---

