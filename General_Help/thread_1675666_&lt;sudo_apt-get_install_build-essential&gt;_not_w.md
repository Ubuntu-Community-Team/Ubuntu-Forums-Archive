---
title: "&lt;sudo apt-get install build-essential&gt; not working"
date: 2011-01-25
forum: General Help
---

### Post by layers on 2011-01-25
I tried running hplips, but it goes upt to one command and stops. When I tried running that command by itself in terminal this is what i get:
```
ibo@ibo-laptop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up firefox-4.0-core (4.0~b10~hg20110120r60909+nobinonly-0ubuntu1~umd1~lucid) ...
update-alternatives: error: alternative path /usr/bin/firefox-4.0 doesn't exist.
dpkg: error processing firefox-4.0-core (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 firefox-4.0-core
E: Sub-process /usr/bin/dpkg returned an error code (1)
ibo@ibo-laptop:~$ 
```

Has anyone encountered this problem before?

---

### Post by yetiman64 on 2011-01-25
Actually build-essential is fine (and the newest version).

> build-essential is already the newest version.You have a problem with firefox4.0-core

> update-alternatives: error: alternative path /usr/bin/firefox-4.0 doesn't exist.Firefox4.0-core should install correctly when firefox4.0 is installed.

Sounds like hplips is failing at that point, because the first time **anything** needs installing it will hit the unresolved firefox4 error in dpkg, as already noted the package build-essential is already installed and the newest version.

You could try
```
sudo apt-get -f install
```to fix the firefox 4 problem.

---

### Post by layers on 2011-01-25
mhm, I did install firefox-4.0, and i'm using it happily, and whatever i try to install, i hit a rock.

```
ibo@ibo-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up firefox-4.0-core (4.0~b10~hg20110120r60909+nobinonly-0ubuntu1~umd1~lucid) ...
update-alternatives: error: alternative path /usr/bin/firefox-4.0 doesn't exist.
dpkg: error processing firefox-4.0-core (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 firefox-4.0-core
E: Sub-process /usr/bin/dpkg returned an error code (1)
ibo@ibo-laptop:~$
```

but i put the firefox folder in /opt/
was i supposed to put it in home?

---

### Post by yetiman64 on 2011-01-25
I suspect putting firefox 4 in /opt is the culprit. You could try locating the executable firefox-4.0 in /opt and note its location (full path).

Then in /usr/bin create a link to the Firefox 4 executable in /opt (I don't know the full path - just working from your posts). I don't know for sure if it will work but is worth a try.

For example, to create the link use a terminal,
```
sudo ln -s /path/to/firefox/folder/firefox-4.0 /usr/bin/firefox-4.0
``` alter the path "/path/to/firefox/folder/" as needed by your install, it will start with at least /opt.

Then re-run 
```
sudo apt-get -f install
```Hope this works.

Edit: An afterthought, also check in /usr/local/bin for the firefox-4.0 executable, and let us know where you find it, it may not necessarily be in /opt after all.

---

### Post by layers on 2011-01-26
i'm sorry what would be the first command specifically?



```
ibo@ibo-laptop:~$ ls /opt/firefox
application.ini             libfreebl3.chk    libxpcom.so
blocklist.xml               libfreebl3.so     libxul.so
chrome                      libmozalloc.so    mozilla-xremote-client
chrome.manifest             libmozsqlite3.so  omni.jar
components                  libnspr4.so       platform.ini
crashreporter               libnss3.so        plugin-container
crashreporter.ini           libnssckbi.so     README.txt
crashreporter-override.ini  libnssdbm3.chk    removed-files
defaults                    libnssdbm3.so     run-mozilla.sh
dependentlibs.list          libnssutil3.so    searchplugins
dictionaries                libplc4.so        Throbber-small.gif
extensions                  libplds4.so       update.locale
firefox                     libsmime3.so      updater
firefox-512-noshadow.png    libsoftokn3.chk   updater.ini
firefox-bin                 libsoftokn3.so
icons                       libssl3.so
ibo@ibo-laptop:~$
```

---

### Post by yetiman64 on 2011-01-26
Please check my edit in my last post, the executable firefox-4.0 may be in /usr/local/bin as you installed to a non standard installation directory. 

It is necessary to link the firefox-4.0 executable to the location dpkg looks at to repair any further installation problems. The idea is to get dpkg to see firefox-4.0 (even seeing a link to it should work).

It doesn't appear to be in /opt/firefox.

---

### Post by layers on 2011-01-26
wait a second there: by installation, you don't mean downloading "firefox-4.0b9.tar.bz2", extracting it and using the "firefox" in that folder to run it, do you?

---

### Post by yetiman64 on 2011-01-26
> **layers said:**
> wait a second there: by installation, you don't mean downloading "firefox-4.0b9.tar.bz2", extracting it and using the "firefox" in that folder to run it, do you?

No, I believe you've already done that and put in /opt. That is, I assumed you had installed firefox 4 from source. Is this right?

How did you install firefox4-core? Did you put it in separately or was it supplied with firefox4.

Firefox4-core is, I believe, configured to look at /usr/bin/ for the alternatives set-up, but because of a non standard installation cannot see it and is causing the installation problems.

Hope this makes a bit more sense.

---

### Post by layers on 2011-01-26
hahaha, no...

posted above, is the folder that i got extracting the archive. literally. and i don't know why i don't use capitals anymore. no source, or building. you can download the archive from [http://www.mozilla.com/en-US/firefox/beta/](http://www.mozilla.com/en-US/firefox/beta/)


ps: i wanna go to bed now

---

### Post by yetiman64 on 2011-01-26
> hahaha, no...

posted above, is the folder that i got extracting the archive.  literally. and i don't know why i don't use capitals anymore. no source,  or building. you can download the archive from [http://www.mozilla.com/en-US/firefox/beta/](http://www.mozilla.com/en-US/firefox/beta/)


ps: i wanna go to bed nowOk, I understand the situation better now, will look into it some more while you have a sleep, goodnight :).

One rather large **EDIT**: (rather than double post ;))

Hopefully listing the steps I took to install ff4 may jog your memory as to exactly how you did your install. The strange thing about your question, is that even with ff4 fully installed here, a check in Synaptic reveals NO installation of firefox-4.0 or firefox-4.0-core (the problem in your installation). 

This leads me to thinking you may have a PPA active for Firefox 4. Could you please check in System > Administration > Software Sources for such a PPA (in the "Other Software" tab) and let us know what your situation is ?

My final idea is that it may still be fixable with a simple link, try out,
```
sudo ln -s /opt/firefox/firefox /usr/bin/firefox-4.0
```This should fix dpkg's complaint about alternatives etc (or possible spit out even more errors - I can't test it here without firefox-4.0-core present).

Then re-run,
```
sudo apt-get -f install
```My Installation of FF4 beta.
> 1. Downloaded firefox 4 from the link you provided.

2. Made a directory in /usr/lib to put it next to the standard install, which is currently /usr/lib/firefox-3.6.13 on lucid. I could of just as easily created one in /opt like yours (I prefer to mimic the system for fault finding/learning reasons etc).

```
sudo mkdir /usr/lib/firefox-4.0beta
```IMPORTANT: For you to use any code here substitute /opt/firefox (your install) for /usr/lib/firefox-4.0beta (my install)- this is the only real difference in the install proceedures apart from user profiles (not using them shouldn't have any bearing on the original problem).

3. To extract the files to /usr/lib/firefox-4.0beta requires root access. In a terminal I put,

```
gksu file-roller ~/Downloads/firefox-4.0b10.tar.bz2
```4. In the Archive Manager window I opened the firefox folder, highlighted the entire contents and dragged and dropped them into the folder I made earlier, /usr/lib/firefox-4.0beta, (you won't need a root file browser window as the Archive Manager is opened as root already). The Archive Manager window was then shut.

5. As /usr/lib is not in the system path I created a link to /usr/lib/firefox-4.0beta/firefox in /usr/bin and called it firefox-4.0 (I'm hoping this will fix your original problem re alternatives etc).

```
sudo ln -s /usr/lib/firefox-4.0beta/firefox /usr/bin/firefox-4.0
```6. In my case I separate ff3 and ff4 from interfering with each other by the use of profiles. To check this out you can use, (not entirely necessary),

```
firefox --no-remote -P
```7. I created a desktop launcher for the new firefox and its profile, the exec line looks like,

[QUOTE]Exec=firefox-4.0 --no-remote -P "FFx4-beta" %u  This tells the system to use firefox-4.0 with the profile "FFx4-beta" (I created this myself) when the launcher is used.


All working very nicely here, I definitely like the new idea of incorporating the Navigation toolbar into every tab, good idea that.

BTW: Thanks for the download link to FF4 beta.[/QUOTE]

---

### Post by layers on 2011-01-26
great success, yeti. i unchecked it from sources and ran the link command and it installed.

thanks again.

and just a last question:
when it comes to broken dependencies, what exactly does it mean and what is the "proper" way of fixing them?
```
ibo@ibo-laptop:~/Downloads$ sudo apt-get install --assume-yes libcups2-dev
[sudo] password for ibo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libcups2-dev: Depends: libcups2 (= 1.4.3-1) but 1.4.3-1ubuntu1.2 is to be installed
E: Broken packages
ibo@ibo-laptop:~/Downloads$ 
```

---

### Post by yetiman64 on 2011-01-27
Firstly I should confirm what version of Ubuntu you are using, I believe you are on Lucid as a result of,
> Setting up firefox-4.0-core (4.0~b10~hg20110120r60909+nobinonly-0ubuntu1~umd1~**lucid**)from your first post. **Is this right ?** Also could you please post the name of the PPA so I can do some checking with regards to libcups2 versions etc ? 

> ...and just a last question:
when it comes to broken dependencies, what exactly does it mean and what is the "proper" way of fixing them?...Most of the time a package will depend on the installation of another package/s or even a particular version of another package/s to work correctly and will often refuse to install or even "break" the installer until those dependency issues are resolved by either removing or installing packages (very carefully, I might add, unless you really like re-installing).

"Dependency hell" can be avoided by sticking to the official repos for your software, because all the problems are ironed out by the Developers at Canonical (OK will admit updates sometimes give a bit of grief to users - Synaptic and it's tools have saved my hide from reinstalls a few times now as a result of them).

Having just said that, you are outside the standard install using a PPA for firefox and it appears to be causing conflicts in package versions etc. BTW the current fault is a dev package (libcups2-dev) which is only for developing other packages against libcups2.

**Questions:** Why are you installing it?   Is it a requirement of the original package you were working on installing (hplips) ? 

As a guide the version of libcups2 on this (relatively standard) install, is 1.4.3-1ubuntu**1.3**, you have version 1.4.3-1ubuntu**1.2** to be installed on your machine and libcups2-dev is wanting version = 1.4.3-1. This is a bit strange.

As a quick test I just installed libcups2-dev without a problem with Synaptic. I suspect the PPA has altered your version of libcups2 and as a result you now cannot install libcups2-dev as needed (Note: this is really only largely guesswork as to the variation in version numbers - I am no expert on this by any means).

My solution would be to **first do a full update and see if that package is updated**, **if not, then I would purge the PPA** with the ppa-purge package,

```
sudo apt-get install ppa-purge
``````
man ppa-purge
```for how to use it. 
Just make sure the ppa is enabled in Softwere Sources IF you choose to use this.

By the sounds of your previous posts you really don't need the ppa, as you said you downloaded and extracted firefox4 manually anyway. 

> posted above, is the folder that i got extracting the archive.Revert your system back to standard with ppa-purge and retry installing libcups2-dev again (if it is really necessary for hplips for example).

The major advantage of using a PPA is the automatic updating to newer packages, the downside being dependency hell when anything goes wrong. You can manually install firefox4 as per post #10, and then update manually when the program informs you of updates being available (I just used this process below to go from beta10 to beta11).

To manually update firefox 4

1. Download the latest build for your hardware/system. 

I won't post the link, as I am downloading the nightly builds for use on a 64 bit platform. The original link you posted can be treated in the same way though (I could only see an i686 version there so had to switch to the nightly build download site- to get my flash and java addons etc working).

2. Shut down firefox 4, and then delete the complete contents of its installation folder, leaving the actual folder itself (be VERY carefull here)

```
sudo rm -r /usr/lib/firefox-4.0beta/*
```Note the * is what specifies to delete all contents and the -r recursively removes the subdirectories. 
ONCE AGAIN - adjust this command to suit your install (sudo rm -r /opt/firefox/*). 
IF you leave off the * and inadvertently remove the firefox folder, you can reinstall it from the Archive by dragging and dropping the firefox folder to the install location instead of just the contents like I do (I do it this way as a result of customizing the folder name to firefox-4.0beta).  

3. Use the commands and actions in Post #10 to reinstall the new tar.bz2 contents to the now empty folder.

4. Fire up firefox and all should be Ok.

---

