---
title: "apt-get update errors"
date: 2012-04-19
forum: General Help
---

### Post by meanmrmustard on 2012-04-19
I'm getting a couple errors during updating.

I've used [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/) to generate a new sources.list, which is now giving yet another error:
```
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) natty/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty/free i386 Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_natty_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty/non-free i386 Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_natty_non-free_binary-i386_Packages)
```

Here is the present sources.list [http://paste2.org/p/1985830](http://paste2.org/p/1985830) 

You will notice that "i386" does not appear in the list at all, let alone in the lines apt-get is complaining about.



As you can see "canonical" appears once in the list, here:

###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu natty partner](http://archive.canonical.com/ubuntu natty partner)

and medibuntu, four times, here:

## Run this command: sudo apt-get update && sudo apt-get install [COLOR="red"]medibuntu[/COLOR]-keyring && sudo apt-get update 
deb [http://packages](http://packages).[COLOR="Red"]medibuntu[/COLOR].org/ natty free non-free # [COLOR="red"]Medibuntu[/COLOR] - [http://www](http://www).[COLOR="red"]medibuntu[/COLOR].org/

So I don't understand where the "duplicates" are coming from.

In addition I'm also getting multiple gpg errors like these:
```
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security Release: Unknown error executing gpgv
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release: Unknown error executing gpgv
W: GPG error: [http://deb.opera.com](http://deb.opera.com) lenny Release: Unknown error executing gpgv
W: GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: Unknown error executing gpgv
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release: Unknown error executing gpgv
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release: Unknown error executing gpgv
```

In one thread - [http://www.unix.com/ubuntu/123074-cant-update-use-package-manager-gpg-error.html](http://www.unix.com/ubuntu/123074-cant-update-use-package-manager-gpg-error.html). 
They removed and re-installed ubuntu-keyring but the problem remained.

Another user resolved the issue running:
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update

I executed these but the error remains.

Another user found that running "gpgv" at the command line returned:
gpgv: symbol lookup error: /usr/local/lib/libreadline.so.6: undefined symbol: PC
I got the same result.

They first tried re-installing the file and eventually resolved the issue by manually building libreadline.so.6.
This seemed to me that it shouldn't be unnecessary (but what do I know...) so I thought I'd look into it.

Looking at the contents of /usr/local/lib, I find:

libhistory.a     libhistory.so.6.2  libreadline.so.6    python2.6
libhistory.so    libreadline.a      libreadline.so.6.2  python2.7
libhistory.so.6  libreadline.so     libtermcap.a

I've never looked at this directory before and now I'm wondering if the .so, .so.6 and .so.6.2 versions might be part of the problem, or are they each necessary... and is there maybe something missing?.. and what I should do next.

I'll throw this in in case it might be relevant.
I just found another user getting the same error trying to run r-base
(edited post):
"...> error: /usr/local/lib/libreadline.so.6: undefined symbol: PC
>That .so file is in /usr/local/lib and did not come from an Ubuntu package.
(reply)
Yes.  Not sure where this came from, but make sure that libreadline 
6.1-1 is installed via apt or synaptic.  You may also have other 
versions of libreadline.so or libreadline.so.6 linked to this somewhere else on the system, so make sure nothing links to this file.

---

### Post by IWantFroyo on 2012-04-19
Have you tried switching your software repos?

Go to the Software Center, and select Edit->Software Sources. There should be a button to find the fastest source for you, or you can set it yourself to a close place.

---

### Post by meanmrmustard on 2012-04-19
> **IWantFroyo said:**
> Have you tried switching your software repos?

Go to the Software Center, and select Edit->Software Sources. There should be a button to find the fastest source for you, or you can set it yourself to a close place.

I just tried a couple different ones but the GPG and duplicates errors remain.

Another that I didn't mention is also still showing up.
Most, but not all, of those are Translation-en, TranslationIndex, Translation-en_US and Packages/DiffIndex.
eg.
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release 
and 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease
Actually these two are the only ones besides the four previously listed.

---

### Post by Cheesemill on 2012-04-19
Check for files in the /etc/apt/sources.list.d/ directory.
Apt-get parses all of the files in there for software sources as well as in the /etc/apt/sources.list file.

---

### Post by meanmrmustard on 2012-04-19
> **Cheesemill said:**
> Check for files in the /etc/apt/sources.list.d/ directory.
Apt-get parses all of the files in there for software sources as well as in the /etc/apt/sources.list file.

Interesting... it has at least one that I don't find in the sources.list.  :confused:

Edit:
There are no dupes there.

---

### Post by cortman on 2012-04-19
You can fix your GPG errors by following [these instructions.]("http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/")
I think it would be easier for all of us to troubleshoot sources.list if you would post the FULL sources.list file contents in [CODE] tags.

---

### Post by meanmrmustard on 2012-04-19
> **cortman said:**
> You can fix your GPG errors by following [these instructions.]("http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/")
I think it would be easier for all of us to troubleshoot sources.list if you would post the FULL sources.list file contents in ```
 tags.

I ran the commands but there's no change on updating.
I supplied a link in the first post to the full sources list.
Is this insufficient?


[CODE]
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://archive.ubuntu.com/ubuntu natty main restricted universe multiverse

###### Ubuntu Update Repos
deb http://archive.ubuntu.com/ubuntu natty-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu natty-updates main restricted universe multiverse

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu natty partner

###### Ubuntu Extras Repo
deb http://extras.ubuntu.com/ubuntu natty main

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys     1024R/BB901940
deb http://ppa.launchpad.net/audacity-team/daily/ubuntu natty main # Audacity - http://audacity.sourceforge.net/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E5E17B5
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu natty main # Chromium Project - http://code.google.com/chromium/

## Run this command: sudo apt-get update && sudo apt-get install faenza-icon-theme && sudo apt-get install equinox-theme    
deb http://ppa.launchpad.net/tiheum/equinox/ubuntu natty main # Equinox - https://launchpad.net/~tiheum/+archive/equinox

## Run this command: wget -q -O - http://repo.palatinus.cz/repo.key | sudo apt-key add -
deb http://repo.palatinus.cz/stable / # Esmska - http://code.google.com/p/esmska/

## Run this command: http://www.fbreader.org/desktop/debian/geometer.fbreader.org.asc -O- | sudo apt-key add -
deb http://www.fbreader.org/desktop/debian stable main # FBReader - http://www.fbreader.org/desktop/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F2A61FE5
deb http://ppa.launchpad.net/flacon/ppa/ubuntu natty main # Flacon - http://kde-apps.org/content/show.php?content=113388

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5BE6AD9A
deb http://ppa.launchpad.net/gcstar/gcstar-dev/ubuntu natty main # GCstar - http://www.gcstar.org/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 72D340A3
deb http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu natty main # Gwibber (Daily) - https://launchpad.net/gwibber

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 816950D8
deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu natty main # HandBrake Releases - http://handbrake.fr/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu natty main # LibreOffice 3.3 - http://www.documentfoundation.org/download/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 412F055D
deb http://ppa.launchpad.net/liferea/liferea-unstable/ubuntu natty main # Liferea Unstable - http://liferea.sourceforge.net/

## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
deb http://packages.medibuntu.org/ natty free non-free # Medibuntu - http://www.medibuntu.org/

## Run this command: sudo wget -O - http://apt.mucommander.com/apt.key | sudo apt-key add - 
deb http://apt.mucommander.com stable main non-free contrib # muCommander - http://www.mucommander.com/

## Run this command: sudo wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
deb http://deb.opera.com/opera/ lenny non-free # Opera - http://www.opera.com/

## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4BB9F05F
deb http://ppa.launchpad.net/jcfp/ppa/ubuntu natty main # SABnzbd - http://sabnzbd.org/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1BD3A65C
deb http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu natty main # Terminator - http://www.tenshu.net/terminator/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 881574DE
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu natty main # Themes for GNOME and Ubuntu - https://edge.launchpad.net/~bisigi/+archive/ppa

## Run this command: gpg --keyserver subkeys.pgp.net --recv 886DDD89 && gpg --export --armor 94C09C7F  | sudo apt-key add -
deb http://deb.torproject.org/torproject.org lucid main # Tor: anonymity online - http://www.torproject.org/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb http://ppa.launchpad.net/tualatrix/ubuntu natty main # Ubuntu Tweak - http://ubuntu-tweak.com/

## Run this command: wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
deb http://download.virtualbox.org/virtualbox/debian natty contrib # VirtualBox - http://www.virtualbox.org

## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40130828
deb http://ppa.launchpad.net/c-korn/ppa/ubuntu maverick main # VLC Media Player  - http://www.videolan.org/vlc/

## Run this command: wget http://www.webmin.com/jcameron-key.asc -O- | sudo apt-key add -
deb http://download.webmin.com/download/repository sarge contrib # Webmin - http://www.webmin.com

## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu natty main # Wine - https://launchpad.net/~ubuntu-wine/+archive/ppa/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu natty main # X Updates - https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/
#Fixes
#run launchpad-getkeys as root to replace missing gpg keys
# run fix404 as root to fix 404 errors
```

---

### Post by cortman on 2012-04-19
Sorry- I missed the link. Even so, my work web filter blocked it for whatever reason.

Have you tried

```
sudo rm -r /var/lib/apt/lists/*
```

Then update?

---

### Post by meanmrmustard on 2012-04-19
> **cortman said:**
> Sorry- I missed the link. Even so, my work web filter blocked it for whatever reason.

Have you tried

```
sudo rm -r /var/lib/apt/lists/*
```

Then update?

Tried it, still getting the GPG errors.

One person with this error even removed and re-installed GPG, but no joy there either.

---

