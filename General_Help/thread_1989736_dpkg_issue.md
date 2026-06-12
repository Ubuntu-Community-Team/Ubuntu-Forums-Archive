---
title: "dpkg issue"
date: 2012-05-28
forum: General Help
---

### Post by soiled skivvies on 2012-05-28
Here's the situation.  1 desktop. 1 laptop. completely unrelated hardware and completely unrelated repositories.  I disabled ALL but the system default..even deleted the keys for the third party when this happened.

I booted the desktop for the first time in a month. Out of nowhere, it's telling me my packages are broken with unmet dependencies.  The laptop did it the same day at the same time.

I follow a guide, it gets worse.

Someone tells me to alter a file, add a folder, (un)comment a line in gedit, run a terminal command, and it gets worse.

Folders and/or files people say exist never have since the date of install. Files people say to rename or move to see if it makes a new one, and the system makes a new one, but an exact clone of the old one...and the problem stays.

I reinstalled the system by completely wiping out the old one which caused me to lose everything because the systems are both so screwed, I can't even access my backups without it freezing. After a complete reinstall, the package system was broken again...in the exact same way as before.

Keep in mind both computers are 11.10 Ubuntu with Punity installed and have completely unrelated repositories besides the factory defaults, but have the exact same issue.  It doesn't even mention which ones are broken. Don't ask for Synaptic...That one dropped a deuce all over the errors and won't even load anymore.

I'm getting input/output errors from dpkg out the Wazoo.  Error codes 1 and 2. I can't even begin to explain the jibberish it was spewing at me.  Don't say Synaptic might help by doing one at a time, because when I try...it says it's going to remove EVERY system package except the one I want to fix which will effectively wipe the system clean. It's making my system suicidal!  Yes, it says over 3000 some packages are broken, and most of them don't even work. They just try to run and then my processor and ram max out making my mouse work once every minute for only a second.  Somehow, with all the errors, it booted.  It's now telling me my swap space is non-existent or not ready, but gparted gladly says it's there (can work on that later DPKG FIRST!).

I want my dpkg working.  Thread links - tried all, failed/worsened issue.  Bug report - researched, tried, failed/worsened issue. Error logs - people say they're in certain folders ...which never existed.

Is there an independent *.deb replacement dpkg file or something I can download and manually try? 

sudo apt-get -f install ..1 hour of no response and an almost frozen system, errors...
sudo apt-get update ..works perfectly fine
Trying to install something ..tells me to go shove it

This issue can be duplicated.  Revert back to 11.10 and wait for it to ask you to upgrade.  DPKG didn't break until both systems wanted to upgrade to 12.04 and I told it no.  Nothing was wrong until I clicked "NO", then bam..it hit almost instantly.  
 
How I always get hit with a completely different system than what everyone else downloads from the same link off ubuntu.com is beyond my comprehension.

---

### Post by dniMretsaM on 2012-05-28
Post the actual errors you are getting, please.

---

### Post by soiled skivvies on 2012-05-28
xx@xx-AO722:~$ sudo dpkg --configure -a
[sudo] password for xx: 
dpkg: error: reading package info file '/var/lib/dpkg/status': Input/output error


xx@xx-AO722:~$ sudo apt-get update
**(Abridged terminal output but only default repos here.)**
Fetched 20.0 MB in 31s (645 kB/s) 
Reading package lists... 98%  **>>>(It got stuck here for 13 minutes)**
Reading package lists... Done
xx@xx-AO722:~$


xx@xx-AO722:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
**    (Here it listed a bunch of packages)**
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
**   (Here it listed basically every package in the system inluding x11, xdg, xserver, etc.)**
Suggested packages:
**   (Here it listed packages I already have of the same version like mesa-utils, everything python, Java, avahi, apparmor, dchp, etc)**
Recommended packages:
  xml-core libcompress-zlib-perl libdigest-sha-perl ntfsprogs
The following packages will be REMOVED:
  warzone2100-dbg
The following NEW packages will be installed:
**    (Here this list was basically the same as "suggested packages", except these ones definitely already existed. Most of them work.  It had mostly libxxxx packages)**
The following packages will be upgraded:
  desktopcouch libxml2 telepathy-mission-control-5
3 upgraded, 775 newly installed, 1 to remove and 2 not upgraded.  **(Was over 3000. I swapped the file in /var/lib/dpkg/status to the same with "-old" suffix)**
Need to get 318 MB/503 MB of archives.
After this operation, 1,544 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
**(Then these lines went by smoothly)**
Get:1 [http://us.archive.ubuntu.com/blahblah](http://us.archive.ubuntu.com/blahblah)
**(And so on to the last one.)**
Get:379 [http://LAST](http://LAST) ONE
Fetched 318 MB in 5min 25s (977 kB/s)                                          
E: Could not perform immediate configuration on 'multiarch-support'. Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)
xx@xx-AO722:~$ 

**Now that last line is a new one! **

---

### Post by matt_symes on 2012-05-28
Hi

Open a terminal and type

```
sudo apt-get -f install -o APT::Immediate-Configure=0
```

Enter your password. It will not be echoed to the screen. Hopefully that will fix your problem.

Kind regards

---

### Post by soiled skivvies on 2012-05-29
xx@xx-AO722:~$ sudo apt-get -f install -o APT::Immediate-Configure=0
[sudo] password for xx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
**(same type of package listings..MUCH longer lists..just pasted ahead.)**
The following packages will be upgraded:
  desktopcouch libxml2 telepathy-mission-control-5
3 upgraded, 775 newly installed, 1 to remove and 2 not upgraded.
Need to get 0 B/503 MB of archives.
After this operation, 1,544 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Couldn't configure pre-depend multiarch-support for libgcc1, probably a dependency cycle.
xx@xx-AO722:~$

---

### Post by matt_symes on 2012-05-29
Hi

Try installing multiarch-support using dpkg. 

You may have to check the name of the deb file below as i do not have it on my system (i cleaned the cache). Use tab comletion to help

```
sudo dpkg -i /var/cache/apt/archives/multiarch-support_2.15-0ubuntu10.deb
```

Then type

```
sudo apt-get -f install
```

Kind regards

---

### Post by soiled skivvies on 2012-05-29
xx@xx-AO722:~$ sudo dpkg -i /var/cache/apt/archives/multiarch-support_2.15-0ubuntu10.deb
[sudo] password for xx: 
dpkg: error: reading package info file '/var/lib/dpkg/status': Input/output error


EDIT:  The filename on mine was multiarch-support_2.13-20ubuntu5.1_amd64.deb, but I received the same error

---

### Post by matt_symes on 2012-05-29
Hi

Out of interest, what is the output of...

```
ls -l /var/lib/dpkg/status
```

...on the damaged file ?

You have already used the backup status file ?

```
sudo mv /var/lib/dpkg/status{,.bk}
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

If you can, consider backing up the drive at this point.

Run a SMART test on the drive from a LiveCD/USB and if the SMART status returns a healthy disk, run fsck on the partition from a LiveCD/USB and see if that helps in any way.

You need to check if the drive is failing or if it's a filing system problem.

Kind regards

---

### Post by matt_symes on 2012-05-29
. Duplicate post

---

### Post by soiled skivvies on 2012-05-29
xx@xx-AO722:~$ ls -l /var/lib/dpkg/status
-rw-r--r-- 1 root root 1952131 2012-05-26 12:05 /var/lib/dpkg/status
xx@xx-AO722:~$

---

### Post by matt_symes on 2012-05-29
Hi

> **soiled skivvies said:**
> xx@xx-AO722:~$ ls -l /var/lib/dpkg/status
-rw-r--r-- 1 root root 1952131 2012-05-26 12:05 /var/lib/dpkg/status
xx@xx-AO722:~$

That looks alright. See my last post as i have edited it greatly.

As you have an inode you may be able to delete that file using debugfs but test the disk first.

Kind regards

---

### Post by soiled skivvies on 2012-05-29
I have no clue what you are talking about...

EDIT:  But SMART is working fine.  Think it would have something to do with the fact booting up gives me a ton of errors and tells me I don't have a SWAP partition and then tries to make/mount one when the gparted says it's there and just fine?

P.S. I only know how to view the command line during boot by pushing the right arrow key.  I don't know how to copy & paste it, but the errors are extreme...and it doesn't explain why my desktop decided to do the exact same thing at the exact same time with absolutely no errors during boot and only minimal cheesey ones I usually ignore the last 4 years through upgrades and all...


After the first edit and following your other post exactly, I finally got it to error in a different way and started to narrow down the problem....Those commands were just the short way of going back to the original from the "-old."  Yes, I was trying to use the backup also. I've tried both but this error is new. It actually says something instead of "shove it."

Fetched 387 MB in 5min 57s (1,082 kB/s)                                        
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: error: parsing file '/var/lib/dpkg/status' near line 23764 package 'libmono-i18n4.0-cil':
 EOF during value of field `Description' (missing final newline)
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by matt_symes on 2012-05-29
Hi

I know you said SMART was working but i just wanted to make sure. Can you boot into a live CD, open a terminal and type

```
sudo apt-get install smartmontools
```

```
sudo smartctl -t long /dev/sda
```

This assumes your drive is called sda. This will take a while to run.

```
sudo smartctl -a /dev/sda
```

This will produce a log file that you can post back here. I always worry on input/output errors.

Next if we can look at your status file. Boot into your standard install and please post the output of

```
cat -n /var/lib/dpkg/status | grep -A15 -B5 23764
```

Kind regards

---

### Post by soiled skivvies on 2012-05-29
OK, first thing is first. I tried to save that log file in 13 different places and everything was a read only file system for some reason when I know it's not.  It was the live boot I used. Did it exactly the way you said. Going to have to paste it from the live boot.  I'll edit this when I get there.

Now, as for the other command:

xx@xx-AO722:~$ cat -n /var/lib/dpkg/status | grep -A15 -B5 23764
 23759    Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
 23760    Architecture: all
 23761    Source: mono
 23762    Version: 2.10.5-1
 23763    Depends: libmono-corlib4.0-cil (>= 2.10.1), mono-runtime (>= 2.10.5), mono-runtime (<< 2.10.6)
 23764    Description: Mono I18N base library (for CLI 4.0)
 23765     Mono is a

---

### Post by matt_symes on 2012-05-30
Hi

> **soiled skivvies said:**
> OK, first thing is first. I tried to save that log file in 13 different places and everything was a read only file system for some reason when I know it's not.  It was the live boot I used. Did it exactly the way you said. Going to have to paste it from the live boot.  I'll edit this when I get there.

Read only file system ? I am beginning to wonder if you have hard drive problems or a very corrupted install. Without being at yiur keyboard it's hard to tell.

> 
Now, as for the other command:

xx@xx-AO722:~$ cat -n /var/lib/dpkg/status | grep -A15 -B5 23764
 23759    Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
 23760    Architecture: all
 23761    Source: mono
 23762    Version: 2.10.5-1
 23763    Depends: libmono-corlib4.0-cil (>= 2.10.1), mono-runtime (>= 2.10.5), mono-runtime (<< 2.10.6)
 23764    Description: Mono I18N base library (for CLI 4.0)
 23765     Mono is a

Was that all of it ? There should have been 20 lines (A15, B5). If that was all of it then this could be the problem with your sources.list file.

You can open the the and edit it manually if you want to.

```
gksudo gedit /var/lib/dpkg/status
```

Scroll down to line 23764 and remove the lines surrounding it (in the section that references that mono package). The section should be surrounded with a blank line above and below.

I am wondering if these problems you are having with the package manager are not due to a failing hard drive or corrupt install.

I would back my any data straight away. You can then run fsck on the drive from a LiveCD.

If you can, post back the SMART results. You should be able to copy and paste the text from the terminal into your next post.

Kind regards

---

### Post by soiled skivvies on 2012-05-30
sources.list from the command you gave me is empty.  I tried to copy and paste the codeyou gave me but I don't know how to type outside that box it makes it show on the forums when someone puts a code in.

i ran sudo gedit /var/lib/dpkg/status  and found the exact line and completely deleted that section you mentioned.

Then I ran sudo apt-get -f install and this is where it got strange.

**Most of it worked. It also said a bunch of stuff didn't even exist.  Here are some sample lines. I couldn't scroll back far enough...**
[B]READ FOR BOLD PRINT NOTES.
This IS in order as seen, but I passed be a bunch of the "Setting up XXXX" lines.[/B]

Setting up libnm-gtk0 (0.9.1.90-0ubuntu6) ...
Setting up libnspr4-0d (4.8.7-0ubuntu3) ...
Setting up libnss-mdns (0.10-3.1ubuntu1) ...
First installation detected...
Checking NSS setup...
Setting up libntfs10 (2.0.0-1ubuntu4) ...
Setting up libofa0 (0.9.3-3.1) ...
Setting up libopencore-amrnb0 (0.1.2-1) ...
Setting up libopenobex1 (1.5-2build1) ...
Setting up liborbit2 (1:2.14.19-0ubuntu3) ...

**Here's some more:**

Setting up librhythmbox-core4 (2.90.1~20110908-0ubuntu1.3) ...
Setting up librsvg2-common (2.34.1-2) ...
/var/lib/dpkg/info/librsvg2-common:amd64.postinst: 15: cannot create /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0//gdk-pixbuf-query-loaders/loaders.cache: Directory nonexistent
Setting up libschroedinger-1.0-0 (1.0.10-2.1) ...
Setting up libservlet2.5-java (6.0.32-5ubuntu1.2) ...
Setting up libsidplay1 (1.36.59-5) ...

Setting up libtaglib2.0-cil (2.0.3.7+dfsg-1build1) ...
* Installing 2 assemblies from libtaglib2.0-cil into Mono
Setting up libtelepathy-farsight0 (0.0.19-1) ...
Setting up libtextcat-data (2.2-9ubuntu2) ...


Setting up light-themes (0.1.8.25) ...
dpkg: dependency problems prevent configuration of lmodern:
 lmodern depends on tex-common (>= 1.18); however:
  Package tex-common is not configured yet.
dpkg: error processing lmodern (--configure):
 dependency problems - leaving unconfigured
Setting up make (3.81-8.1ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              Setting up media-player-info (15-1) ...
Setting up min12xxw (0.0.9-3ubuntu3) ...
Setting up mono-4.0-gac (2.10.5-1) ...
Setting up nautilus (1:3.2.1-0ubuntu4.2) ...
Setting up network-manager (0.9.1.90-0ubuntu5.1) ...

Setting up notification-daemon (0.7.1-4) ...
notification-daemon: no process found  **  (I GET NOTIFICATIONS STILL!!!)**
Setting up nux-tools (1.16.0-0ubuntu1.1) ...

Setting up t1-xfree86-nonfree (4.2.1-3) ...
dpkg: dependency problems prevent configuration of texlive-common:
 texlive-common depends on tex-common (>= 2.0); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already** (**CONFUSED**)**
                                                              dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 texlive-latex-base depends on texlive-common (>= 2009-1); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base-doc:
 texlive-latex-base-doc depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 texlive-latex-base-doc depends on texlive-common (>= 2009-1); however:No apport report written because MaxReports is reached already
**(SHOULD I CARE SINCE I DON'T KNOW WHAT TEXLIVE IS???)**
  Package texlive-common is not configured yet.
dpkg: error processing texlive-latex-base-doc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up totem-common (3.0.1-0ubuntu7.1) ...
Setting up tsconf (1.0-9) ...

Setting up unattended-upgrades (0.73ubuntu1) ...
update-rc.d: warning: unattended-upgrades start runlevel arguments (2 3 4 5) do not match LSB Default-Start values (none)
update-rc.d: warning: unattended-upgrades stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (0 6)
Checking for running unattended-upgrades: 
Setting up unity-2d-launcher (4.12.0-0ubuntu1.1) ...

**A ton of lines that look like this:**

Replacing debian:AddTrust_Low-Value_Services_Root.pem
Replacing debian:SwissSign_Platinum_CA_-_G2.pem
Replacing debian:NetLock_Arany_=Class_Gold=_F&#337;tanúsítvány.pem

**Here's where I started to smile. Haven't seen this in a while:**

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place  **(THE SMILE LINE!)**
Processing triggers for initramfs-tools ...

**Here's the very end:**

Errors were encountered while processing:
 foomatic-filters
 foomatic-db-engine
 rsyslog
 tex-common
 cm-super-minimal
 cm-super-x11
 libpaper1
 cups
 lmodern
 texlive-common
 texlive-latex-base
 texlive-latex-base-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)
xx@xx-AO722:~$ 


The packages it said it had errors processing....should I even care??? Printers + Linux = behind the times. I can honestly care less about CUPS or whatever foomatic is...

The circle with the line through it is no longer appearing up by the clock saying I have errors in my package system. It went away almost the second I ran sudo apt-get -f install.

EDIT:  I'm scared to reboot now.  I got TONS of errors I can't scroll up high enough to get back to saying it wasn't setting up a tons of important packages weren't even install or configured so it was ignoring them.

---

### Post by matt_symes on 2012-05-30
Hi

sources.list was a typo. I glad you realised i was refering to....

```
gksudo gedit /var/lib/dpkg/status
```

:)

Make a backup copy of your new status file first as it looks like we may be making progress.

```
sudo cp /var/lib/dpkg/status{,.1}
```

To get a condensed version of the errors type

```
sudo apt-get update
```

or 

```
sudo apt-get install -f
```

verbatin from the terminal back into here. Which ever one errors post back. 

Kind regards

---

### Post by soiled skivvies on 2012-05-30
xx@xx-AO722:~$ sudo cp /var/lib/dpkg/status{,.1}
[sudo] password for xx: 
xx@xx-AO722:~$ sudo apt-get update -qq
xx@xx-AO722:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-coherence gtk2-engines-smooth libgsf-1-common erlang-crypto
  unetbootin-translations python-avahi erlang-xmerl warzone2100-data
  openarena-081-textures python-couchdb libgtkmm-2.4-1c2a python-louie
  python-nevow libsctp1 libboost-python1.46.1 libalgorithm-diff-xs-perl
  python-twisted-conch lksctp-tools libmozjs185-1.0 python-axiom
  python-epsilon couchdb-bin erlang-runtime-tools ruby1.8 ure-dbg
  libsdl-image1.2 python-clientform openarena-server gnome-themes-selected
  libreadline5 openarena-081-maps warzone2100-music erlang-mnesia libgsf-1-114
  openarena-081-players-mature erlang-public-key python-tagpy pgf
  openarena-081-misc python-desktopcouch-records python-configobj
  ttf-tamil-fonts desktopcouch erlang-inets gnome-themes-more openarena-data
  python-m2crypto gromit erlang-ssl libalgorithm-diff-perl libruby1.8 libg3d0
  uno-libs3-dbg openarena-081-players python-desktopcouch-application
  python-beautifulsoup python-pysqlite2 libreoffice-l10n-en-gb python-pyasn1
  openarena-085-data erlang-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
12 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up foomatic-filters (4.0.9-1ubuntu2) ...
dpkg: error processing foomatic-filters (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of foomatic-db-engine:
 foomatic-db-engine depends on foomatic-filters (>= 4.0); however:
  Package foomatic-filters is not configured yet.
dpkg: error processing foomatic-db-engine (--configure):
 dependency problems - leaving unconfigured
Setting up libpaper1 (1.1.24+nmu1) ...
No apport report written because the error message indicates its a followup error from a previous failure. 
                          dpkg: error processing libpaper1 (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of cups:
 cups depends on libpaper1; however:
  Package libpaper1 is not configured yet.
dpkg: error processing cups (--configure):
 dependency problems - leaving unconfigured
Setting up rsyslog (5.8.1-1ubuntu2) ...
No apport report written because MaxReports is reached already
                                                              dpkg: error processing rsyslog (--configure):
 subprocess installed post-installation script returned error exit status 10
No apport report written because MaxReports is reached already
                                                              Setting up tex-common (2.10) ...
dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 10
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of cm-super-minimal:
 cm-super-minimal depends on tex-common (>= 1.18); however:
  Package tex-common is not configured yet.
dpkg: error processing cm-super-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cm-super-x11:
 cm-super-x11 depends on cm-super-minimal; however:
  Package cm-super-minimal is not configured yet.
No apport report written because MaxReports is reached already
                                                              dpkg: error processing cm-super-x11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lmodern:
 lmodern depends on tex-common (>= 1.18); however:
  Package tex-common is not configured yet.
dpkg: error processing lmodern (--configure):No apport report written because MaxReports is reached already
                           No apport report written because MaxReports is reached already

 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-common:
 texlive-common depends on tex-common (>= 2.0); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 texlive-latex-base depends on texlive-common (>= 2009-1); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-latex-base-doc:
 texlive-latex-base-doc depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 texlive-latex-base-doc depends on texlive-common (>= 2009-1); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-latex-base-doc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 foomatic-filters
 foomatic-db-engine
 libpaper1
 cups
 rsyslog
 tex-common
 cm-super-minimal
 cm-super-x11
 lmodern
 texlive-common
 texlive-latex-base
 texlive-latex-base-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)
xx@xx-AO722:~$ 

I'm sure you're aware of the "-qq" appended to apt-get update to only show if any errors. Same results without suffix as usual. This time it's no longer hesitating before it finishes. Maybe it's my slow craptop.   What's a "foomatic" and a "texlive"  Could I just purge them from the system and move on with my life?  I'm going to remove mono and everything about it unless I'm not supposed to. I was going to practice some coding with different languages and see which one(s) I want to try, but working the night shift doesn't make it easy so Mono can go away just like the real disease of the same name for all I care :P.  I thank you for your time and patience to this point and I plan on applying all this new knowledge to my desktop (Her name is Honkey Kong.) inside joke...

---

### Post by matt_symes on 2012-05-31
Hi

The first thing i would do is to remove all the packages that are not dependencies of other packages.

Open a terminal and type

```
sudo apt-get autoremove
```

The rest of the errors are caused by dependency problems caused by the packages foomatic-filters, libpaper1, tex-common and rsyslog that are not being configured correctly.

To be honest, i am not sure what error code 10 is.

These are the packages that need to be fixed.

You could try purging the packages.

```
sudo dpkg -P foomatic-filters libpaper1 tex-common rsyslog
```

and cleaning the cache

```
sudo apt-get clean
```

and then trying to fix it again

```
sudo apt-get install -f
```

You can try to download them (foomatic-filters libpaper1 tex-common rsyslog) from

```
http://packages.ubuntu.com/
```

and install them using 

```
sudo dpkg -i <package_name1> <package_name2>
```

and then 

```
sudo apt-get install -f
```

This below may also help (but i doubt it as it is having trouble configurng them at the moment.)

```
sudo dpkg --configure foomatic-filters libpaper1 tex-common rsyslog
```

You could also just purge them.

It looks like you have had a number of crashes since your installation. Delete any existing crash files.

```
sudo rm /var/crash/*
```

I would also check your sources files just to make sure there are no problems there (although i suspect they may be fine).

Post back the results of...

```
cat /etc/apt/sources.list /etc/apt/sources.list.d/*
```

Kind regards

---

### Post by soiled skivvies on 2012-05-31
xx@xx-AO722:~$ cat /etc/apt/sources.list /etc/apt/sources.list.d/*
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric main restricted #Added by software-properties

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse #Added by software-properties

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
# deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) oneiric main
# deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) oneiric main
# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb apps
# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb apps
# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb games
# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb games
xx@xx-AO722:~$


sudo apt-get -f install ..or..  sudo apt-get install -f   still won't work right, but I seem to be on the right track now that Synaptic is working. I kept the terminal errors open to scroll indefinitely.  Going page by page, package by package, clicking either reinstall or completely remove.  Each time I click apply, the error list giving me errors that look like this:

dpkg: warning: files list file for package `unity-greeter' missing, assuming package has no files currently installed.

are now slowly disappearing.   This may take a while, but now update manager won't leave me alone. Every time I fix one package, it wants to update another. We shall see when this is over.  I'm going to need more coffee for this...

---

### Post by matt_symes on 2012-05-31
Hi

As expected, your source look fine.

Keep at it. I think you're making progress. It seems you have had a very corrupted packing system.

The "file list file" files are stored in ```
/var/lib/dpkg/info
```

They end in a .list extension and contain information about the files each package installs on your PC.

I believe it is these files that are read by

```
dpkg -L <package_name>
```

Please keep us informed.

Kind regards

---

### Post by soiled skivvies on 2012-06-05
It's absolutely hopeless now.  You did a fantastic job helping me fix my package system and I cannot thank you enough.  Both the desktop and laptop wanted to run update manager and they each had their own individually different updates, with only one in common.  The update was "Ubuntu-Common."  They both wanted to reboot, only to find they both did a full reboot into massive kernel panic. The recovery (which you have to be a genius to use anyways) is also in panic mode.  Neither system works at all anymore.  This is why I ignore updates with the prefix "Ubuntu-", because all they do is crash computers.  I believe the desktop wanted to update the ATI drivers to a newer version of the same ones, which, I cannot do because all they do is crash my desktop.  I forgot and just let it update.  The laptop didn't panic until I booted into Windows partition and shut it down normally because I had boot errors about it being in hibernation.  Now to watch this finish typing since it can't keep up and post it...

On the lighter side, thank you once again Matt_Symes for all your assistance. I saved this thread in Wordpad for future reference.  Now to use the tool for Windows to access my work, music, and everything else and start from scratch. I better stop because a 4kb Windows update that took 30 minutes to download and install is saying it's going to reboot me 60 seconds from now without any options. 

Maybe this time network sharing might actually work for the first time in 5 years.  

I apologize for venting, but I can't afford backup hard drives and I think I lost almost everything, including my firefox sync key...I'm screwed beyond all screwed.  UbuntuOne has my pictures backup, thankfully.

---

### Post by matt_symes on 2012-06-05
Hi

Don't worry about venting. We've all done it :D

Technology is great when it works but a nightmare when it doesn't. I always say "use what works for you" and, if Windows is stable for you, then use that. It's only a hunk of silicon and metal after all. 

I wish you good luck.

Kind regards

---

### Post by soiled skivvies on 2012-06-05
Oh no I'm not using it permanently. Never will! It made a half usable workspace so I can do something at least to figure this out.  I'm actually on the laptop with repaired packages and no updates to install.

[B]How I did that: 

Used GRUB, selected the most recent 3.0.0_19 (or something like that.) kernel, and it worked fine. The only difference in kernel names were the _19 and the _20.  The _20 is the broken one.  How do I get rid of _20 so maybe I can try it again?  Ubuntu Tweak says it's not there, but GRUB wants to use it as default...[/B]

This is why I love Ubuntu and Linux in general. There's ALWAYS options.  Other systems, there's ALWAYS expensive repairs and absolutely useless recovery partitions. I bought the laptop to have a laptop. The OS was just a plastic toy in the Cracker Jack box. I learned to deal with Unity, even though I'm not a fan. I will never learn to deal with Windows.

P.S. Don't ever use the Sharper Image generic mp3 player on your system. If the OS hibernates, it WILL cause irreversible kernel panics, even if you shutdown and reboot. 

Desktop is 11.10 installed. Didn't update, and started a flawless, almost error free upgrade to 12.04.  It's fixing dependency problems as it goes ("file x has dependency problems...but removing anyway as you requested.")  I love you all and I love Ubuntu!

---

