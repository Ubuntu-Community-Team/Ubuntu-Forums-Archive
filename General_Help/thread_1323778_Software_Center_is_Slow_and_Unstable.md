---
title: "Software Center is Slow and Unstable"
date: 2009-11-12
forum: General Help
---

### Post by Topher88 on 2009-11-12
I've just fresh installed Karmic, and I'm trying to use Software Center to download and play some games, and every time, the installation takes about five or ten minutes, and then tells me that the "package operation failed," even though the game appears in applications>games and seems to work just fine...  It also appears in Software Center afterwards as a program that I have downloaded.  The same thing happens when I try to uninstall - it takes forever and then tells me that it failed, even though it appears to have gotten rid of the software and shows it as downloadable in the SC.

I've changed Software Sources to a closer mirror to help the download speeds, but it appears to have had no effect.  Any idea what the deal is??

Thanks.

---

### Post by Topher88 on 2009-11-12
Also, I don't know if this is any correlation at all, but I've noticed that with practically every* sudo apt-get install *command I use, I get the message *E: Sub-process /usr/bin/dpkg returned an error code (1)* at the end of whatever is installing.

---

### Post by Topher88 on 2009-11-12
Now that I think about it, I've noticed that installation via the terminal is also quite slower than normal, and also gives me an error message EVEN THOUGH it seems to install have installed the program anyway...  Just like in Software Center.  Here is what the download process of Deluge looks like.

Please look through this and tell me if there is anything abnormal going on (other than just the error message at the end) and if so, what I need to do differently to get my downloads to work correctly.  Thanks!

```

chris@chris-laptop:~$ sudo apt-get install deluge
[sudo] password for chris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  deluge-common deluge-core python-chardet
The following NEW packages will be installed:
  deluge deluge-common deluge-core python-chardet
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 1,965kB of archives.
After this operation, 8,049kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ubuntu.osuosl.org karmic/universe python-chardet 1.0.1-1.1 [172kB]
Get:2 http://ubuntu.osuosl.org karmic/universe deluge-core 1.1.9+dfsg-1 [1,345kB]
Get:3 http://ubuntu.osuosl.org karmic/universe deluge-common 1.1.9+dfsg-1 [189kB]
Get:4 http://ubuntu.osuosl.org karmic/universe deluge 1.1.9+dfsg-1 [259kB]     
Fetched 1,965kB in 16s (120kB/s)                                               
Selecting previously deselected package python-chardet.
(Reading database ... 119700 files and directories currently installed.)
Unpacking python-chardet (from .../python-chardet_1.0.1-1.1_all.deb) ...
Selecting previously deselected package deluge-core.
Unpacking deluge-core (from .../deluge-core_1.1.9+dfsg-1_all.deb) ...
Selecting previously deselected package deluge-common.
Unpacking deluge-common (from .../deluge-common_1.1.9+dfsg-1_all.deb) ...
Selecting previously deselected package deluge.
Unpacking deluge (from .../deluge_1.1.9+dfsg-1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Setting up ttf-mscorefonts-installer (3.0) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2009-11-12 01:56:07--  http://downloads.sourceforge.net/corefonts/andale32.exe
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-11-12 01:56:17--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving switch.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net [following]
--2009-11-12 01:56:19--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-11-12 01:56:29--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving mesh.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `mesh.dl.sourceforge.net'
--2009-11-12 01:56:39--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving dfn.dl.sourceforge.net... 194.95.236.6
Connecting to dfn.dl.sourceforge.net|194.95.236.6|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net [following]
--2009-11-12 01:56:41--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-11-12 01:56:51--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving heanet.dl.sourceforge.net... 193.1.193.66, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net [following]
--2009-11-12 01:56:52--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-11-12 01:57:02--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving jaist.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `jaist.dl.sourceforge.net'
--2009-11-12 01:57:12--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net [following]
--2009-11-12 01:57:13--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-11-12 01:57:23--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving ufpr.dl.sourceforge.net... 200.17.202.1, 200.236.31.1
Connecting to ufpr.dl.sourceforge.net|200.17.202.1|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net [following]
--2009-11-12 01:57:26--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-11-12 01:57:36--  http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internode.dl.sourceforge.net... 150.101.135.12
Connecting to internode.dl.sourceforge.net|150.101.135.12|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net [following]
--2009-11-12 01:57:37--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-11-12 01:57:47--  http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving voxel.dl.sourceforge.net... 208.122.28.18, 208.122.28.27, 208.122.28.11, ...
Connecting to voxel.dl.sourceforge.net|208.122.28.18|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=voxel.dl.sourceforge.net [following]
--2009-11-12 01:57:49--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=voxel.dl.sourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-11-12 01:57:59--  http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving kent.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `kent.dl.sourceforge.net'
--2009-11-12 01:58:09--  http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internap.dl.sourceforge.net... 74.201.0.131
Connecting to internap.dl.sourceforge.net|74.201.0.131|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=internap.dl.sourceforge.net [following]
--2009-11-12 01:58:10--  http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=internap.dl.sourceforge.net
Resolving prdownloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `prdownloads.sourceforge.net'
sha256sum: andale32.exe: No such file or directory
andale32.exe: FAILED open or read
sha256sum: WARNING: 1 of 1 listed file could not be read
Checksum mismatch for andale32.exe, aborting!
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-chardet (1.0.1-1.1) ...

Setting up deluge-core (1.1.9+dfsg-1) ...

Setting up deluge-common (1.1.9+dfsg-1) ...

Setting up deluge (1.1.9+dfsg-1) ...

Processing triggers for python-support ...
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by P4man on 2009-11-12
Its a DNS issue resolving sourceforge.
 Have a look here for workarounds :

[https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/431217](https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/431217)

---

### Post by Topher88 on 2009-11-12
> **P4man said:**
> Its a DNS issue resolving sourceforge.
 Have a look here for workarounds :

[https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/431217](https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/431217)

I applied the solution in post #21, and it seemed to be going pretty quickly in SC until it got to 68%, and  then it hung for about five minutes.  However, it ended up downloading without giving me any error messages, even though it did take a while.  I don't know if that is a huge concern or not, but I will toy around with terminal installs and synaptics as well to see if any other problems persist.  If there still are significant problems, I'll try some of the other suggestions in the thread that you've provided.

Thanks for the info!

UPDATE:  Just ran a terminal install, and everything seems to be working properly - no long hangups, and no error message at the end.  I don't know why Software Center still takes a while, but I guess that as long as it's actually getting the job done without an error message, it's not a huge deal.  I guess it's safe to say that this issue is resolved.

Again, thanks!!!  :-)

---

### Post by P4man on 2009-11-12
perhaps try another mirror in system > adminstation> software sources. If you go to other, let it pick the best one for you.

---

### Post by ubeautu on 2010-02-24
> **P4man said:**
> perhaps try another mirror in system > adminstation> software sources. If you go to other, let it pick the best one for you.

Yes this is the solution that will help. The problem is most likely that we have not tested for the best mirror in our area. Doing the test can make the world of difference in download speed. My downloads moved from 12kbs to 225kbs when I made this simple adjustment.

To do the test, just select 'other' in the 'download from' section of software sources.

---

