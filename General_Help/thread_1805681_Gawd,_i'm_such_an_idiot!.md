---
title: ":/ Gawd, i'm such an idiot!"
date: 2011-07-16
forum: General Help
---

### Post by UltraNEO* on 2011-07-16
Anyone know how to downgrade Firefox? Last night I accidentally added the wrong app to the system, now it's installed and upgrade my browser to 6.0 beta. 

Ideally I'd prefer Firefox 5. 
Why? Cause then my plug-in would work. 

p.s. running 10.04.2 Lucid here..

cheers.

---

### Post by rickytikki on 2011-07-16
the easiest i think would t just completely remove fire fox and downlad the version u want. sudo apt-get remove firefox

---

### Post by UltraNEO* on 2011-07-16
> **rickytikki said:**
> the easiest i think would t just completely remove fire fox and downlad the version u want. sudo apt-get remove firefox

OK... What I do next?

I've downloaded the archive from here
[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/5.0/linux-i686/en-GB/firefox-5.0.tar.bz2](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/5.0/linux-i686/en-GB/firefox-5.0.tar.bz2)
 
Now, how do I install it? Sorry.. not so beefed up, on linux yet :( 
And normally I just install stuff via the software center..



BTW, I tried using the repositories:
```

$ sudo add-apt-repository ppa:ubuntu-mozilla-security/ppa 
$ sudo apt-get update 
$ sudo apt-get dist-upgrade
```


My terminal gave me this: 
> ultraneo@dfi-desktop:~$ sudo add-apt-repository ppa:ubuntu-mozilla-security/ppa
[sudo] password for ultraneo: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv AF316E81A155146718A6FBD7A6DCF7707EBC211F
gpg: requesting key 7EBC211F from hkp server keyserver.ubuntu.com
gpg: key 7EBC211F: "Launchpad PPA for Ubuntu Mozilla Security Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
ultraneo@dfi-desktop:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                     
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_GB
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                       
Get: 1 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]             
Ign [http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/) lucid/main Translation-en_GB
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg 
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_GB
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg              
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg
Ign [http://ppa.launchpad.net/tiheum/equinox/ubuntu/](http://ppa.launchpad.net/tiheum/equinox/ubuntu/) lucid/main Translation-en_GB
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg 
Ign [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/) lucid/main Translation-en_GB
Get: 2 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]             
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_GB
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg 
Ign [http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu/) lucid/main Translation-en_GB
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                           
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                           
Get: 3 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [14.0kB]               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages
Get: 4 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [581B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages
Fetched 15.2kB in 0s (42.3kB/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9BDB3D89CE49EC21
ultraneo@dfi-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by linuxmaniack on 2011-07-16
do  sudo apt-get remove firefox and then goto the Ubuntu software center, and install firefox 5, or open terminal, and do sudo apt-get install firefox. or if you want to install your downloaded file, right click on it open with, and select ubuntu software center. if using 10.04 or lower, install it with debian package installer (i think it is called that anyway)

---

### Post by cottfcfan on 2011-07-16
You don't need to download the archive.
Just add the firefox stable repo to your sources, and then install Firefox again.
```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```
```
sudo apt-get update && sudo apt-get install firefox
```
Done.

---

### Post by UltraNEO* on 2011-07-16
Just did what you suggested... 

Moved Firefox with "sudo apt-get remove firefox"

Term tells me:
> ultraneo@dfi-desktop:~$ sudo apt-get remove firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  firefox firefox-3.5
0 upgraded, 0 newly installed, 2 to remove and 2 not upgraded.
After this operation, 48.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: warning: files list file for package `kubuntu-firefox-installer' missing, assuming package has no files currently installed.
(Reading database ... 163344 files and directories currently installed.)
Removing firefox-3.5 ...
Removing firefox ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for python-support ...





> **cottfcfan said:**
> You don't need to download the archive.
Just add the firefox stable repo to your sources, and then install Firefox again.
```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```
```
sudo apt-get update && sudo apt-get install firefox
```
Done.


Then reinstalled it using your commands and guess what? I'm back with this :( 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=197616&stc=1&d=1310834549[/IMG]


What's going on???

---

### Post by UltraNEO* on 2011-07-16
Yep.. Image says Beta Channel but I don't have a beta channel..

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=197617&stc=1&d=1310835072[/IMG]

So where is it getting the beta updates from?

---

### Post by lovinglinux on 2011-07-16
I have an additional ppa repository for Firefox enabled, that is installing Firefox 6.0b. Open Software Sources and look for any mozilla ppa and disable them. Leave only the mozillateam *firefox-stable* ppa activated. Then update and reinstall firefox.

```
sudo apt-get update
sudo apt-get install --reinstall firefox

```

For future reference, see [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247")

---

### Post by UltraNEO* on 2011-07-16
Damn repository... lol 
Ubuntutweak is soo useful :)

> **lovinglinux said:**
> I have an additional ppa repository for Firefox enabled, that is installing Firefox 6.0b. Open Software Sources and look for any mozilla ppa and disable them. Leave only the mozillateam *firefox-stable* ppa activated. Then update and reinstall firefox.

```
sudo apt-get update
sudo apt-get install --reinstall firefox

```

For future reference, see [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247")



Dude.. I <3 U! :D 
Thank you very much!

Thanks to everyone else too :)

---

### Post by lovinglinux on 2011-07-16
> **UltraNEO* said:**
> Damn repository... lol 
Ubuntutweak is soo useful :)

Dude.. I <3 U! :D 
Thank you very much!

Thanks to everyone else too :)

You are welcome.

Indeed Ubuntutweak is useful, but it uses *mozilla-dail*y or *mozilla-security* ppa (don't remember exactly which one), which updates not only Firefox, but also Thunderbird. The recommended ppa for Firefox is the mozillateam *firefox-stable* and *firefox-next*, depending if you want stable releases only or betas.

---

