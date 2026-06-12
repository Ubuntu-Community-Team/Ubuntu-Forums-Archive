---
title: "HELP i need help !!!!!!"
date: 2011-03-04
forum: General Help
---

### Post by sesipdo on 2011-03-04
need some help here this is my 4 time posting this to 3 different sites and no responses .!!!!


_____________________


 				[IMG]http://ubuntuforums.org/images/icons/icon6.gif[/IMG] 				**An unhandlable error occured Ubuntu 32 bit** 			
 			 			 		   		 		 		i was  installing wine for ubuntu and i think my laptop went to sleep in the  process and now when i go to install any other program i get this  message 


----------------------
There seems to be a programming error in aptdaemon, the software that  allows you to install/remove software and to perform other package  management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

-------- ERRORS -------------------

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 936, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the  ttf-mscorefonts-installer package. This might mean you need to manually  fix this package.
------------------------------------------:sad:

---

### Post by patchwork on 2011-03-04
First, try to fix any errors in installation of packages...
```
sudo apt-get install -f
```

Next, ensure all packages are properly configured:
```
sudo dpkg --configure -a
```

If this alone does not resolve the problem, consider that the package listed in the error is part of the ubuntu-restricted-extras package.  This is not installed by default, and must be added if you have not done so already.

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by sesipdo on 2011-03-04
thank you for reply and when i did the first command it gave me this thing > and i hit enter and space and right enter and nothing makes it go on .....

---

### Post by patchwork on 2011-03-04
Hit Tab to select OK and then press Enter.

---

### Post by sesipdo on 2011-03-04
u would think after all my years of dos and windows i would have known  that one :P 


and update manage has opened up .. so should i update ubuntu ?




_________


shawn@shawn-pc-pc:~$ sudo apt-get install -f
[sudo] password for shawn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ttf-mscorefonts-installer
The following packages will be upgraded:
  ttf-mscorefonts-installer
1 upgraded, 0 newly installed, 0 to remove and 266 not upgraded.
1 not fully installed or removed.
Need to get 0B/40.3kB of archives.
After this operation, 221kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 
dpkg: warning: files list file for package `ttf-mscorefonts-installer' missing, assuming package has no files currently installed.
(Reading database ... 142573 files and directories currently installed.)
Preparing to replace ttf-mscorefonts-installer 3.2ubuntu2 (using .../ttf-mscorefonts-installer_3.2ubuntu2_all.deb) ...
Unpacking replacement ttf-mscorefonts-installer ...
Processing triggers for fontconfig ...
Setting up ttf-mscorefonts-installer (3.2ubuntu2) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2011-03-04 22:02:52--  [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following]
--2011-03-04 22:02:53--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following]
--2011-03-04 22:02:53--  [http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe)
Resolving cdnetworks-us-2.dl.sourceforge.net... 174.35.19.12
Connecting to cdnetworks-us-2.dl.sourceforge.net|174.35.19.12|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198384 (194K) [application/octet-stream]
Saving to: `./andale32.exe'

     0K .......... .......... .......... .......... .......... 25%  101K 1s
    50K .......... .......... .......... .......... .......... 51%  208K 1s
   100K .......... .......... .......... .......... .......... 77%  299K 0s
   150K .......... .......... .......... .......... ...       100%  389K=1.0s

2011-03-04 22:02:54 (190 KB/s) - `./andale32.exe' saved [198384/198384]

--2011-03-04 22:02:54--  [http://downloads.sourceforge.net/corefonts/arialb32.exe](http://downloads.sourceforge.net/corefonts/arialb32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe) [following]
--2011-03-04 22:02:55--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe](http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe) [following]
--2011-03-04 22:02:55--  [http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe](http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe)
Resolving iweb.dl.sourceforge.net... 70.38.0.134
Connecting to iweb.dl.sourceforge.net|70.38.0.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 168176 (164K) [application/x-msdos-program]
Saving to: `./arialb32.exe'

     0K .......... .......... .......... .......... .......... 30%  144K 1s
    50K .......... .......... .......... .......... .......... 60%  345K 0s
   100K .......... .......... .......... .......... .......... 91%  523K 0s
   150K .......... ....                                       100%  538K=0.6s

2011-03-04 22:02:56 (268 KB/s) - `./arialb32.exe' saved [168176/168176]

--2011-03-04 22:02:56--  [http://downloads.sourceforge.net/corefonts/arial32.exe](http://downloads.sourceforge.net/corefonts/arial32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe) [following]
--2011-03-04 22:02:56--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe) [following]
--2011-03-04 22:02:56--  [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe)
Resolving softlayer.dl.sourceforge.net... 74.86.229.28
Connecting to softlayer.dl.sourceforge.net|74.86.229.28|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 554208 (541K) [application/octet-stream]
Saving to: `./arial32.exe'

     0K .......... .......... .......... .......... ..........  9%  145K 3s
    50K .......... .......... .......... .......... .......... 18%  372K 2s
   100K .......... .......... .......... .......... .......... 27%  503K 2s
   150K .......... .......... .......... .......... .......... 36%  496K 1s
   200K .......... .......... .......... .......... .......... 46%  609K 1s
   250K .......... .......... .......... .......... .......... 55%  482K 1s
   300K .......... .......... .......... .......... .......... 64%  532K 1s
   350K .......... .......... .......... .......... .......... 73%  503K 0s
   400K .......... .......... .......... .......... .......... 83%  600K 0s
   450K .......... .......... .......... .......... .......... 92%  412K 0s
   500K .......... .......... .......... .......... .         100%  535K=1.3s

2011-03-04 22:02:58 (404 KB/s) - `./arial32.exe' saved [554208/554208]

--2011-03-04 22:02:58--  [http://downloads.sourceforge.net/corefonts/comic32.exe](http://downloads.sourceforge.net/corefonts/comic32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe) [following]
--2011-03-04 22:02:59--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe](http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe) [following]
--2011-03-04 22:02:59--  [http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe](http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe)
Resolving surfnet.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 246008 (240K) [application/x-msdos-program]
Saving to: `./comic32.exe'

     0K .......... .......... .......... .......... .......... 20% 71.0K 3s
    50K .......... .......... .......... .......... .......... 41%  155K 1s
   100K .......... .......... .......... .......... .......... 62%  464K 1s
   150K .......... .......... .......... .......... .......... 83%  336K 0s
   200K .......... .......... .......... ..........           100%  357K=1.4s

2011-03-04 22:03:01 (172 KB/s) - `./comic32.exe' saved [246008/246008]

--2011-03-04 22:03:01--  [http://downloads.sourceforge.net/corefonts/courie32.exe](http://downloads.sourceforge.net/corefonts/courie32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe) [following]
--2011-03-04 22:03:01--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe) [following]
--2011-03-04 22:03:01--  [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe)
Resolving softlayer.dl.sourceforge.net... 74.86.229.28
Connecting to softlayer.dl.sourceforge.net|74.86.229.28|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 646368 (631K) [application/octet-stream]
Saving to: `./courie32.exe'

     0K .......... .......... .......... .......... ..........  7%  212K 3s
    50K .......... .......... .......... .......... .......... 15%  293K 2s
   100K .......... .......... .......... .......... .......... 23%  512K 2s
   150K .......... .......... .......... .......... .......... 31%  397K 1s
   200K .......... .......... .......... .......... .......... 39%  575K 1s
   250K .......... .......... .......... .......... .......... 47%  461K 1s
   300K .......... .......... .......... .......... .......... 55%  617K 1s
   350K .......... .......... .......... .......... .......... 63%  490K 1s
   400K .......... .......... .......... .......... .......... 71%  435K 0s
   450K .......... .......... .......... .......... .......... 79%  504K 0s
   500K .......... .......... .......... .......... .......... 87%  499K 0s
   550K .......... .......... .......... .......... .......... 95%  300K 0s
   600K .......... .......... .......... .                    100%  697K=1.5s

2011-03-04 22:03:03 (411 KB/s) - `./courie32.exe' saved [646368/646368]

--2011-03-04 22:03:03--  [http://downloads.sourceforge.net/corefonts/georgi32.exe](http://downloads.sourceforge.net/corefonts/georgi32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe) [following]
--2011-03-04 22:03:03--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe](http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe) [following]
--2011-03-04 22:03:04--  [http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe](http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe)
Resolving cdnetworks-us-2.dl.sourceforge.net... 174.35.19.12
Connecting to cdnetworks-us-2.dl.sourceforge.net|174.35.19.12|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 392440 (383K) [application/octet-stream]
Saving to: `./georgi32.exe'

     0K .......... .......... .......... .......... .......... 13%  105K 3s
    50K .......... .......... .......... .......... .......... 26%  319K 2s
   100K .......... .......... .......... .......... .......... 39%  204K 1s
   150K .......... .......... .......... .......... .......... 52%  332K 1s
   200K .......... .......... .......... .......... .......... 65%  320K 1s
   250K .......... .......... .......... .......... .......... 78%  325K 0s
   300K .......... .......... .......... .......... .......... 91%  610K 0s
   350K .......... .......... .......... ...                  100%  335K=1.5s

2011-03-04 22:03:06 (252 KB/s) - `./georgi32.exe' saved [392440/392440]

--2011-03-04 22:03:06--  [http://downloads.sourceforge.net/corefonts/impact32.exe](http://downloads.sourceforge.net/corefonts/impact32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe) [following]
--2011-03-04 22:03:06--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://cdnetworks-us-1.dl.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe](http://cdnetworks-us-1.dl.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe) [following]
--2011-03-04 22:03:06--  [http://cdnetworks-us-1.dl.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe](http://cdnetworks-us-1.dl.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe)
Resolving cdnetworks-us-1.dl.sourceforge.net... 174.35.19.11
Connecting to cdnetworks-us-1.dl.sourceforge.net|174.35.19.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 173288 (169K) [application/octet-stream]
Saving to: `./impact32.exe'

     0K .......... .......... .......... .......... .......... 29% 93.4K 1s
    50K .......... .......... .......... .......... .......... 59%  318K 0s
   100K .......... .......... .......... .......... .......... 88%  309K 0s
   150K .......... .........                                  100%  299K=0.9s

2011-03-04 22:03:08 (184 KB/s) - `./impact32.exe' saved [173288/173288]

--2011-03-04 22:03:08--  [http://downloads.sourceforge.net/corefonts/times32.exe](http://downloads.sourceforge.net/corefonts/times32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe) [following]
--2011-03-04 22:03:08--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe](http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe) [following]
--2011-03-04 22:03:08--  [http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe](http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe)
Resolving voxel.dl.sourceforge.net... 74.63.46.198, 74.63.46.220, 74.63.46.218, ...
Connecting to voxel.dl.sourceforge.net|74.63.46.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 661728 (646K) [application/octet-stream]
Saving to: `./times32.exe'

     0K .......... .......... .......... .......... ..........  7%  163K 4s
    50K .......... .......... .......... .......... .......... 15%  319K 3s
   100K .......... .......... .......... .......... .......... 23%  403K 2s
   150K .......... .......... .......... .......... .......... 30%  520K 2s
   200K .......... .......... .......... .......... .......... 38%  416K 1s
   250K .......... .......... .......... .......... .......... 46%  403K 1s
   300K .......... .......... .......... .......... .......... 54%  492K 1s
   350K .......... .......... .......... .......... .......... 61%  309K 1s
   400K .......... .......... .......... .......... .......... 69%  589K 1s
   450K .......... .......... .......... .......... .......... 77%  601K 0s
   500K .......... .......... .......... .......... .......... 85%  574K 0s
   550K .......... .......... .......... .......... .......... 92%  324K 0s
   600K .......... .......... .......... .......... ......    100%  313K=1.7s

2011-03-04 22:03:11 (370 KB/s) - `./times32.exe' saved [661728/661728]

--2011-03-04 22:03:11--  [http://downloads.sourceforge.net/corefonts/trebuc32.exe](http://downloads.sourceforge.net/corefonts/trebuc32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe) [following]
--2011-03-04 22:03:11--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe](http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe) [following]
--2011-03-04 22:03:11--  [http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe](http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe)
Resolving iweb.dl.sourceforge.net... 70.38.0.134
Connecting to iweb.dl.sourceforge.net|70.38.0.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 357200 (349K) [application/x-msdos-program]
Saving to: `./trebuc32.exe'

     0K .......... .......... .......... .......... .......... 14%  187K 2s
    50K .......... .......... .......... .......... .......... 28%  338K 1s
   100K .......... .......... .......... .......... .......... 43%  541K 1s
   150K .......... .......... .......... .......... .......... 57%  501K 0s
   200K .......... .......... .......... .......... .......... 71%  383K 0s
   250K .......... .......... .......... .......... .......... 86%  481K 0s
   300K .......... .......... .......... .......... ........  100%  762K=0.9s

2011-03-04 22:03:12 (385 KB/s) - `./trebuc32.exe' saved [357200/357200]

--2011-03-04 22:03:12--  [http://downloads.sourceforge.net/corefonts/verdan32.exe](http://downloads.sourceforge.net/corefonts/verdan32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe) [following]
--2011-03-04 22:03:13--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe) [following]
--2011-03-04 22:03:13--  [http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe)
Resolving voxel.dl.sourceforge.net... 74.63.46.208, 74.63.46.196, 74.63.46.203, ...
Connecting to voxel.dl.sourceforge.net|74.63.46.208|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 351992 (344K) [application/octet-stream]
Saving to: `./verdan32.exe'

     0K .......... .......... .......... .......... .......... 14%  192K 2s
    50K .......... .......... .......... .......... .......... 29%  402K 1s
   100K .......... .......... .......... .......... .......... 43%  605K 1s
   150K .......... .......... .......... .......... .......... 58%  553K 0s
   200K .......... .......... .......... .......... .......... 72%  421K 0s
   250K .......... .......... .......... .......... .......... 87%  713K 0s
   300K .......... .......... .......... .......... ...       100%  303K=0.9s

2011-03-04 22:03:14 (386 KB/s) - `./verdan32.exe' saved [351992/351992]

--2011-03-04 22:03:14--  [http://downloads.sourceforge.net/corefonts/webdin32.exe](http://downloads.sourceforge.net/corefonts/webdin32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe) [following]
--2011-03-04 22:03:15--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://cdnetworks-us-1.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://cdnetworks-us-1.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe) [following]
--2011-03-04 22:03:15--  [http://cdnetworks-us-1.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://cdnetworks-us-1.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe)
Resolving cdnetworks-us-1.dl.sourceforge.net... 174.35.19.11
Connecting to cdnetworks-us-1.dl.sourceforge.net|174.35.19.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 185072 (181K) [application/octet-stream]
Saving to: `./webdin32.exe'

     0K .......... .......... .......... .......... .......... 27%  103K 1s
    50K .......... .......... .......... .......... .......... 55%  278K 1s
   100K .......... .......... .......... .......... .......... 82%  294K 0s
   150K .......... .......... ..........                      100%  557K=0.9s

2011-03-04 22:03:16 (202 KB/s) - `./webdin32.exe' saved [185072/185072]

andale32.exe: OK
Extracting cabinet: andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
arialb32.exe: OK
Extracting cabinet: arialb32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
arial32.exe: OK
Extracting cabinet: arial32.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
comic32.exe: OK
Extracting cabinet: comic32.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
courie32.exe: OK
Extracting cabinet: courie32.exe
  extracting cour.ttf
  extracting courbd.ttf
  extracting courbi.ttf
  extracting fontinst.inf
  extracting couri.ttf
  extracting fontinst.exe

All done, no errors.
georgi32.exe: OK
Extracting cabinet: georgi32.exe
  extracting fontinst.inf
  extracting Georgiaz.TTF
  extracting Georgiab.TTF
  extracting Georgiai.TTF
  extracting Georgia.TTF
  extracting fontinst.exe

All done, no errors.
impact32.exe: OK
Extracting cabinet: impact32.exe
  extracting fontinst.exe
  extracting Impact.TTF
  extracting fontinst.inf

All done, no errors.
times32.exe: OK
Extracting cabinet: times32.exe
  extracting fontinst.inf
  extracting Times.TTF
  extracting Timesbd.TTF
  extracting Timesbi.TTF
  extracting Timesi.TTF
  extracting FONTINST.EXE

All done, no errors.
trebuc32.exe: OK
Extracting cabinet: trebuc32.exe
  extracting FONTINST.EXE
  extracting trebuc.ttf
  extracting Trebucbd.ttf
  extracting trebucbi.ttf
  extracting trebucit.ttf
  extracting fontinst.inf

All done, no errors.
verdan32.exe: OK
Extracting cabinet: verdan32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting Verdanab.TTF
  extracting Verdanai.TTF
  extracting Verdanaz.TTF
  extracting Verdana.TTF

All done, no errors.
webdin32.exe: OK
Extracting cabinet: webdin32.exe
  extracting fontinst.exe
  extracting Webdings.TTF
  extracting fontinst.inf
  extracting Licen.TXT

All done, no errors.
All fonts downloaded and installed.
Updating fontconfig cache for /usr/share/fonts/truetype/msttcorefonts
shawn@shawn-pc-pc:~$ sudo dpkg --configure -a
shawn@shawn-pc-pc:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  icedtea6-plugin ubuntu-restricted-addons unrar
The following NEW packages will be installed:
  icedtea6-plugin ubuntu-restricted-addons ubuntu-restricted-extras unrar
0 upgraded, 4 newly installed, 0 to remove and 266 not upgraded.
Need to get 0B/190kB of archives.
After this operation, 602kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package ubuntu-restricted-addons.
(Reading database ... 142583 files and directories currently installed.)
Unpacking ubuntu-restricted-addons (from .../ubuntu-restricted-addons_4_i386.deb) ...
Selecting previously deselected package ubuntu-restricted-extras.
Unpacking ubuntu-restricted-extras (from .../ubuntu-restricted-extras_42_i386.deb) ...
Selecting previously deselected package unrar.
Unpacking unrar (from .../unrar_1%3a3.9.10-1_i386.deb) ...
Selecting previously deselected package icedtea6-plugin.
Unpacking icedtea6-plugin (from .../icedtea6-plugin_6b20-1.9.7-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up ubuntu-restricted-addons (4) ...
Setting up ubuntu-restricted-extras (42) ...
Setting up unrar (1:3.9.10-1) ...
update-alternatives: using /usr/bin/unrar-nonfree to provide /usr/bin/unrar (unrar) in auto mode.
Setting up icedtea6-plugin (6b20-1.9.7-0ubuntu1) ...
shawn@shawn-pc-pc:~$

---

### Post by patchwork on 2011-03-04
The upgrading is totally up to you, and is unrelated to the original issue.  The issue that caused the error in your original post should be fixed (that being the missing ttf installer that was just installed)

---

### Post by sesipdo on 2011-03-04
o okay 

and thank you so so much for helping me out on this :)

---

### Post by patchwork on 2011-03-04
no problem

---

### Post by sesipdo on 2011-03-04
this issue is closed now .. :popcorn:

---

