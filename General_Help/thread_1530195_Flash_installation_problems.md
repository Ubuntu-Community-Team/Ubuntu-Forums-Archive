---
title: "Flash installation problems"
date: 2010-07-13
forum: General Help
---

### Post by ashen on 2010-07-13
Hi,

I am currently having problems trying to install the flashplugin-nonfree using apt-get.

I get the following error message:

```
Setting up flashplugin-installer (10.1.53.64ubuntu0.10.04.3) ...
Downloading...
--2010-07-13 14:15:19--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.53.64.orig.tar.gz
Resolving archive.canonical.com... 91.189.88.33
Connecting to archive.canonical.com|91.189.88.33|:80... failed: Connection refused.
download failed
The Flash plugin is NOT installed.
```

Any ideas what is going wrong?  I'm behind a proxy server - could the download be timing out??

Thanks,

Alex

---

### Post by Johnny B on 2010-07-13
you could try going to system > administration > software sources and changing the download server.

---

### Post by Directive 4 on 2010-07-13
if you use firefox, a good thing to try would be 

flash-aid

a plugin for buntu 

it will solve all problems, 

(with flash!)

---

### Post by philinux on 2010-07-13
> **ashen said:**
> Hi,

I am currently having problems trying to install the flashplugin-nonfree using apt-get.

I get the following error message:

```
Setting up flashplugin-installer (10.1.53.64ubuntu0.10.04.3) ...
Downloading...
--2010-07-13 14:15:19--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.53.64.orig.tar.gz
Resolving archive.canonical.com... 91.189.88.33
Connecting to archive.canonical.com|91.189.88.33|:80... failed: Connection refused.
download failed
The Flash plugin is NOT installed.
```

Any ideas what is going wrong?  I'm behind a proxy server - could the download be timing out??

Thanks,

Alex

System>Prefs>Network Proxy.

---

### Post by ashen on 2010-07-13
> **philinux said:**
> System>Prefs>Network Proxy.

Thanks - I should have said: I need the network proxy to connect to the Internet in my org. 

> **Johnny B said:**
> you could try going to system > administration > software sources and changing the download server.

Cheers, I'll try using the UK server and see if that makes a difference!

Thanks,

Alex

---

### Post by deesto on 2010-09-23
Sorry to dredge this back up, but I'm having the same problem:
```
$ sudo apt-get -y install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  flashplugin-installer
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer flashplugin-nonfree
0 upgraded, 2 newly installed, 0 to remove and 6 not upgraded.
Need to get 0B/22.0kB of archives.
After this operation, 233kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-installer.
(Reading database ... 168319 files and directories currently installed.)
Unpacking flashplugin-installer (from .../flashplugin-installer_10.1.85.3ubuntu0.10.04.1_amd64.deb) ...
Selecting previously deselected package flashplugin-nonfree.
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.1.85.3ubuntu0.10.04.1_amd64.deb) ...
Setting up flashplugin-installer (10.1.85.3ubuntu0.10.04.1) ...
Downloading...
--2010-09-23 10:14:16--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.85.3.orig.tar.gz
Resolving archive.canonical.com... 91.189.88.33
Connecting to archive.canonical.com|91.189.88.33|:80... failed: Connection refused.
download failed
The Flash plugin is NOT installed.

Setting up flashplugin-nonfree (10.1.85.3ubuntu0.10.04.1) ...
$

```
> **philinux said:**
> System>Prefs>Network Proxy.I've already got that set, and most apt* commands work properly as a result, but I am surprised to say that this still fails.
> **Directive 4 said:**
> if you use firefox, a good thing to try would be 
flash-aid
a plugin for buntu 
it will solve all problems, 
(with flash!)I'm not convinced that this is the case: I get the same error using FLASH-AID, as the plug-in simply runs a shell script with call-outs to the same commands as apt* uses.  At any rate, in my case, I see the same "connection refused" error in the terminal output.
> **Johnny B said:**
> you could try going to system > administration > software sources and changing the download server.Sorry: change this to what?  I can access the given URL via Firefox, wget, etc., so I don't think changing the URL will help (but perhaps it would?).  I've also confirmed that my proxy is set in /etc/apt/apt.conf, so I'm quite puzzled as to why apt-get normally works through the proxy but fails in this case.

---

### Post by pedro_orange on 2010-09-23
That is certainly a strange error, when I open a browser I can go to [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.85.3.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.85.3.orig.tar.gz)

Can you go to this link in your browser? 
If you can, just install it from the tarball.
If not, step back - can you resolve archive.canonical.com etc?

I doubt this will help, but have you tried installing the meta-package 'ubuntu-restricted-extras' instead of just explictly flashplugin-nonfree? It might do something else that may cause it to work.

---

### Post by Vaphell on 2010-09-23
isn't flashplugin-nonfree 32bit? simply get 64bit version from adobe site [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) and put libflashplayer.so to /usr/lib/mozilla/plugins
granted, this is a manual method that skips repos entirely but it has never failed me

---

### Post by deesto on 2010-09-23
> **pedro_orange said:**
> That is certainly a strange error, when I open a browser I can go to [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.85.3.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.85.3.orig.tar.gz)

Can you go to this link in your browser?Yes, no problem with Firefox and that link. Firefox network is set to "use system proxy settings".
> If you can, just install it from the tarball.Yes, I could do that, but I would much rather keep it controlled by the overall system packaging system.
> If not, step back - can you resolve archive.canonical.com etc?Yes.
> I doubt this will help, but have you tried installing the meta-package 'ubuntu-restricted-extras' instead of just explictly flashplugin-nonfree? It might do something else that may cause it to work.Thanks for that ... I didn't have that package installed, and I've just installed it (didn't help) ... but I am now surprised again to see that when it got to the fonts portion of the package, many connection attempts to package hosts resulted in "... failed: Connection refused."  Don't know what the heck is going on, but this seems to be much less Flash related and more proxy and connection related at this point.

> **Vaphell said:**
> isn't flashplugin-nonfree 32bit? simply get 64bit version from adobe site [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) and put libflashplayer.so to /usr/lib/mozilla/plugins
granted, this is a manual method that skips repos entirely but it has never failed meRight.  See above: I could do this, and will do it eventually if needed, but I'd rather not branch out from the repository packages unless absolutely necessary.

Also, I don't recall where, but I'd read recently that even though Adobe still makes the 64-bit package available, they are dropping support for it and shouldn't be relied upon for a consistent package.  Could be an outright lie, but if not, it's certainly something to consider.

---

### Post by Vaphell on 2010-09-23
they don't make the 64bit package available, they actually updated it recently, like less than 2 weeks ago. Also i tried to use that more secure 32bit version with a wrapper before that recent release, but i gave up after 2 days - it was buggy and horrible. Navigation problems, unresponsiveness, Z axis glitches - you name it.
If you really want to install 64bit through the repos, find a PPA offering automated flash installation.
[http://www.omgubuntu.co.uk/2010/09/install-64bit-flash-from-a-ppa-or-deb/](http://www.omgubuntu.co.uk/2010/09/install-64bit-flash-from-a-ppa-or-deb/)

---

### Post by pedro_orange on 2010-09-23
I don't think the issue is just to do with the installation of flash, it's more the fact that apt is behaving strangely. 
What happens when you do a:

```
sudo apt-get update
```

And then try to run another apt-get install of flash? Perhaps it might be worth changing the mirror for apt.

---

### Post by ieBrazil on 2010-09-23
Hi.
I'm not really into this Ubuntu things alread... so helpe me in this basic thing: where/how do I go to "/usr/lib/mozilla/plugins" in order to put the ....so pluging?

Tnx!


> **Vaphell said:**
> isn't flashplugin-nonfree 32bit? simply get 64bit version from adobe site [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) and put libflashplayer.so to /usr/lib/mozilla/plugins
granted, this is a manual method that skips repos entirely but it has never failed me

[CENTER][/CENTER]

---

### Post by Vaphell on 2010-09-23
terminal way:
```

cd path/to/directory/with/downloaded/libflashplayer/
sudo cp libflashplayer.so /usr/lib/mozilla/plugins
```
gui way:
```
gksu nautilus
```
this opens file browser with superpowers, copy and paste that .so file into the /usr/lib/mozilla/plugins dir (to find usr, go to the very top of the directory tree '/'), close the window afterwards
do not, i repeat, do not use this superwindow all the time out of convenience so you can skip those pesky password prompts and boring permissions. One bad move and your system can be ruined, system won't question admin's actions, even the dumbest ones.

method above is system wide and all users are affected. Alternatively you can put that plugin into the ~/.mozilla/plugins dir (press ctrl+h in your home directory to unhide .mozilla) and firefox should detect it - no admin privileges required, but only your account would use it

after the operation check if it was successful, in firefox address bar about:****plugins, plugin should be listed there if detected
and/or in terminal **sudo updatedb && locate libflashplayer** to see if there are no multiple conflicting copies

---

### Post by deesto on 2010-09-24
I ended up installing Flash via the remote tarball.  Also, for whatever reason, I needed to add my proxy info to /etc/wgetrc in order for some package calls to work ... maybe the apt* system also uses wget in some cases?  At any rate, Alex (the OP) may want to try that and see if it resolves his proxy issue.

---

### Post by ashen on 2010-09-24
Thanks to everyone for their help!

In the end I installed the flash 64bit beta (the one they released before discontinuing) and made sure I have flash block set up only to show content from trusted sites like bbc iplayer.

I wasn't aware they had restarted 64bit linux flash though - i'll set it up from the ppa on 

[http://www.omgubuntu.co.uk/2010/09/install-64bit-flash-from-a-ppa-or-deb/](http://www.omgubuntu.co.uk/2010/09/install-64bit-flash-from-a-ppa-or-deb/)

@deesto when I get back to my work machine I'll investigate that - it was definitely a proxy issue ...

Thanks all,

Alex

---

