---
title: "Ubuntu not installing everything"
date: 2011-09-02
forum: General Help
---

### Post by Vinilguy on 2011-09-02
I got this message when I tried installing wine. I get similar problems when installing other programs.
[PHP]installArchives() failed: Preconfiguring packages ... 
Preconfiguring packages ... 
Selecting previously deselected package ttf-symbol-replacement. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 158004 files and directories currently installed.) 
Unpacking ttf-symbol-replacement (from .../ttf-symbol-replacement_1.2.2-0ubuntu2~lucid1_all.deb) ... 
Selecting previously deselected package libmpg123-0. 
Unpacking libmpg123-0 (from .../libmpg123-0_1.12.1-0ubuntu1_i386.deb) ... 
Selecting previously deselected package libopenal1. 
Unpacking libopenal1 (from .../libopenal1_1%3a1.12.854-0ubuntu1~lucid1_i386.deb) ... 
Selecting previously deselected package wine1.2. 
Unpacking wine1.2 (from .../wine1.2_1.2.2-0ubuntu2~lucid1_i386.deb) ... 
Selecting previously deselected package wine1.2-gecko. 
Unpacking wine1.2-gecko (from .../wine1.2-gecko_1.0.0-0ubuntu4_i386.deb) ... 
Selecting previously deselected package cabextract. 
Unpacking cabextract (from .../cabextract_1.2-3+lenny1build0.10.04.1_i386.deb) ... 
Selecting previously deselected package ttf-droid. 
Unpacking ttf-droid (from .../ttf-droid_1.00~b112+dfsg+1-0ubuntu1_all.deb) ... 
Selecting previously deselected package ttf-mscorefonts-installer. 
Unpacking ttf-mscorefonts-installer (from .../ttf-mscorefonts-installer_3.2ubuntu0.1_all.deb) ... 
Selecting previously deselected package ttf-umefont. 
Unpacking ttf-umefont (from .../ttf-umefont_411-1_all.deb) ... 
Selecting previously deselected package winbind. 
Unpacking winbind (from .../winbind_2%3a3.4.7~dfsg-1ubuntu3.7_i386.deb) ... 
Selecting previously deselected package wine. 
Unpacking wine (from .../wine_1.2.2-0ubuntu2~lucid1_all.deb) ... 
Processing triggers for fontconfig ... 
Processing triggers for man-db ... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache... 
Processing triggers for ureadahead ... 
ureadahead will be reprofiled on next reboot 
Processing triggers for python-support ... 
Setting up kdebase-runtime (4:4.4.5-0ubuntu1) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing kdebase-runtime (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up liblastfm0 (0.4.0~git20090710-1) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing liblastfm0 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libmysqlclient16 (5.1.41-3ubuntu12.10) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libmysqlclient16 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up ttf-symbol-replacement (1.2.2-0ubuntu2~lucid1) ... 
Setting up libmpg123-0 (1.12.1-0ubuntu1) ... 
 
Setting up libopenal1 (1:1.12.854-0ubuntu1~lucid1) ... 
 
Setting up wine1.2 (1.2.2-0ubuntu2~lucid1) ... 
procps stop/waiting 
procps stop/waiting 
 
Setting up wine1.2-gecko (1.0.0-0ubuntu4) ... 
Setting up cabextract (1.2-3+lenny1build0.10.04.1) ... 
Setting up ttf-droid (1.00~b112+dfsg+1-0ubuntu1) ... 
No CIDSupplement specified for Dotum-Bold, defaulting to 0. 
No CIDSupplement specified for Batang-Regular, defaulting to 0. 
No CIDSupplement specified for DroidSansJapanese, defaulting to 0. 
No CIDSupplement specified for Dotum-Regular, defaulting to 0. 
No CIDSupplement specified for DroidSansJapanese-JaH, defaulting to 0. 
No CIDSupplement specified for Batang-Bold, defaulting to 0. 
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-droid 
 
Setting up ttf-mscorefonts-installer (3.2ubuntu0.1) ... 
 
These fonts were provided by Microsoft "in the interest of cross- 
platform compatibility".  This is no longer the case, but they are 
still available from third parties. 
 
You are free to download these fonts and use them for your own use, 
but you may not redistribute them in modified form, including changes 
to the file name or packaging format. 
 
--2011-09-02 20:01:36--  http://downloads.sourceforge.net/corefonts/andale32.exe 
Resolving downloads.sourceforge.net... 216.34.181.59 
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected. 
HTTP request sent, awaiting response... 301 Moved Permanently 
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following] 
--2011-09-02 20:01:36--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe 
Reusing existing connection to downloads.sourceforge.net:80. 
HTTP request sent, awaiting response... 302 Found 
Location: http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following] 
--2011-09-02 20:01:36--  http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe 
Resolving surfnet.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21 
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 198384 (194K) [application/x-msdos-program] 
Saving to: `./andale32.exe' 
 
     0K .......... .......... .......... .......... .......... 25% 72.9K 2s 
    50K .......... .......... .......... .......... .......... 51%  161K 1s 
   100K .......... .......... .......... .......... .......... 77%  493K 0s 
   150K .......... .......... .......... .......... ...       100%  278K=1.3s 
 
2011-09-02 20:01:38 (154 KB/s) - `./andale32.exe' saved [198384/198384] 
 
--2011-09-02 20:01:38--  http://downloads.sourceforge.net/corefonts/arialb32.exe 
Resolving downloads.sourceforge.net... 216.34.181.59 
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected. 
HTTP request sent, awaiting response... 301 Moved Permanently 
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe [following] 
--2011-09-02 20:01:38--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe 
Reusing existing connection to downloads.sourceforge.net:80. 
HTTP request sent, awaiting response... 302 Found 
Location: http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe [following] 
--2011-09-02 20:01:39--  http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe 
Resolving iweb.dl.sourceforge.net... 70.38.0.134, 2607:f748:10:12::5f:2 
Connecting to iweb.dl.sourceforge.net|70.38.0.134|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 168176 (164K) [application/x-msdos-program] 
Saving to: `./arialb32.exe' 
 
     0K .......... .......... .......... .......... .......... 30%  148K 1s 
    50K .......... .......... .......... .......... .......... 60%  400K 0s 
   100K .......... .......... .......... .......... .......... 91%  476K 0s 
   150K .......... ....                                       100%  535K=0.6s 
 
2011-09-02 20:01:39 (277 KB/s) - `./arialb32.exe' saved [168176/168176] 
 
--2011-09-02 20:01:39--  http://downloads.sourceforge.net/corefonts/arial32.exe 
Resolving downloads.sourceforge.net... 216.34.181.59 
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected. 
HTTP request sent, awaiting response... 301 Moved Permanently 
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe [following] 
--2011-09-02 20:01:40--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe 
Reusing existing connection to downloads.sourceforge.net:80. 
HTTP request sent, awaiting response... 302 Found 
Location: http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe [following] 
--2011-09-02 20:01:40--  http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe 
Resolving iweb.dl.sourceforge.net... 70.38.0.134, 2607:f748:10:12::5f:2 
Connecting to iweb.dl.sourceforge.net|70.38.0.134|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 554208 (541K) [application/x-msdos-program] 
Saving to: `./arial32.exe' 
 
     0K .......... .......... .......... .......... ..........  9%  176K 3s 
    50K .......... .......... .......... .......... .......... 18%  324K 2s 
   100K .......... .......... .......... .......... .......... 27%  479K 1s 
   150K .......... .......... .......... .......... .......... 36%  489K 1s 
   200K .......... .......... .......... .......... .......... 46%  491K 1s 
   250K .......... .......... .......... .......... .......... 55%  475K 1s 
   300K .......... .......... .......... .......... .......... 64%  493K 1s 
   350K .......... .......... .......... .......... .......... 73%  475K 0s 
   400K .......... .......... .......... .......... .......... 83%  490K 0s 
   450K .......... .......... .......... .......... .......... 92%  490K 0s 
   500K .......... .......... .......... .......... .         100%  489K=1.3s 
 
2011-09-02 20:01:41 (401 KB/s) - `./arial32.exe' saved [554208/554208] 
 
--2011-09-02 20:01:42--  http://downloads.sourceforge.net/corefonts/comic32.exe 
Resolving downloads.sourceforge.net... 216.34.181.59 
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected. 
HTTP request sent, awaiting response... 301 Moved Permanently 
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe [following] 
--2011-09-02 20:01:42--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe 
Reusing existing connection to downloads.sourceforge.net:80. 
HTTP request sent, awaiting response... 302 Found 
Location: http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe [following] 
--2011-09-02 20:01:42--  http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe 
Resolving cdnetworks-us-2.dl.sourceforge.net... 174.35.19.12 
Connecting to cdnetworks-us-2.dl.sourceforge.net|174.35.19.12|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 246008 (240K) [application/octet-stream] 
Saving to: `./comic32.exe' 
 
     0K .......... .......... .......... .......... .......... 20%  136K 1s 
    50K .......... .......... .......... .......... .......... 41%  290K 1s 
   100K .......... .......... .......... .......... .......... 62%  472K 0s 
   150K .......... .......... .......... .......... .......... 83%  515K 0s 
   200K .......... .......... .......... ..........           100%  507K=0.8s 
 
2011-09-02 20:01:43 (292 KB/s) - `./comic32.exe' saved [246008/246008] 
 
--2011-09-02 20:01:43--  http://downloads.sourceforge.net/corefonts/courie32.exe 
Resolving downloads.sourceforge.net... 216.34.181.59 
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected. 
HTTP request sent, awaiting response... 301 Moved Permanently 
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe [following] 
--2011-09-02 20:01:43--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe 
Reusing existing connection to downloads.sourceforge.net:80. 
HTTP request sent, awaiting response... 302 Found 
Location: http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe [following] 
--2011-09-02 20:01:44--  http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe 
Resolving cdnetworks-us-2.dl.sourceforge.net... 174.35.19.12 
Connecting to cdnetworks-us-2.dl.sourceforge.net|174.35.19.12|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 646368 (631K) [application/octet-stream] 
Saving to: `./courie32.exe' 
 
     0K .......... .......... .......... .......... ..........  7%  135K 4s 
    50K .......... .......... .......... .......... .......... 15%  281K 3s 
   100K .......... .......... .......... .......... .......... 23%  402K 2s 
   150K .......... .......... .......... .......... .......... 31%  491K 2s 
   200K .......... .......... .......... .......... .......... 39%  479K 1s 
   250K .......... .......... .......... .......... .......... 47%  487K 1s 
   300K .......... .......... .......... .......... .......... 55%  462K 1s 
   350K .......... .......... .......... .......... .......... 63%  492K 1s 
   400K .......... .......... .......... .......... .......... 71%  488K 1s 
   450K .......... .......... .......... .......... .......... 79%  480K 0s 
   500K .......... .......... .......... .......... .......... 87%  416K 0s 
   550K .......... .......... .......... .......... .......... 95%  479K 0s 
   600K .......... .......... .......... .                    100%  516K=1.7s 
 
2011-09-02 20:01:45 (375 KB/s) - `./courie32.exe' saved [646368/646368] 
 
--2011-09-02 20:01:46--  http://downloads.sourceforge.net/corefonts/georgi32.exe 
Resolving downloads.sourceforge.net... 216.34.181.59 
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected. 
HTTP request sent, awaiting response... 301 Moved Permanently 
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe [following] 
--2011-09-02 20:01:46--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe 
Reusing existing connection to downloads.sourceforge.net:80. 
HTTP request sent, awaiting response... 302 Found 
Location: http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe [following] 
--2011-09-02 20:01:46--  http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe 
Resolving surfnet.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21 
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 392440 (383K) [application/x-msdos-program] 
Saving to: `./georgi32.exe' 
 
     0K .......... .......... .......... .......... .......... 13% 97.9K 3s 
    50K .......... .......... .......... .......... .......... 26%  169K 2s 
   100K .......... .......... .......... .......... .......... 39%  335K 1s 
   150K .......... .......... .......... .......... .......... 52%  472K 1s 
   200K .......... .......... .......... .......... .......... 65%  417K 1s 
   250K .......... .......... .......... .......... .......... 78%  505K 0s 
   300K .......... .......... .......... .......... .......... 91%  489K 0s 
   350K .......... .......... .......... ...                  100%  493K=1.5s 
 
2011-09-02 20:01:48 (264 KB/s) - `./georgi32.exe' saved [392440/392440] 
 
--2011-09-02 20:01:48--  http://downloads.sourceforge.net/corefonts/impact32.exe 
Resolving downloads.sourceforge.net... 216.34.181.59 
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected. 
HTTP request sent, awaiting response... 301 Moved Permanently 
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe [following] 
--2011-09-02 20:01:48--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe 
Reusing existing connection to downloads.sourceforge.net:80. 
HTTP request sent, awaiting response... 302 Found 
Location: http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe [following] 
--2011-09-02 20:01:48--  http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe 
Resolving softlayer.dl.sourceforge.net... 74.86.229.28 
Connecting to softlayer.dl.sourceforge.net|74.86.229.28|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 173288 (169K) [application/octet-stream] 
Saving to: `./impact32.exe' 
 
     0K .......... .......... .......... .......... .......... 29%  242K 0s 
    50K .......... .......... .......... .......... .......... 59%  485K 0s 
   100K .......... .......... .......... .......... .......... 88%  411K 0s 
   150K .......... .........                                  100%  512K=0.5s 
 
2011-09-02 20:01:49 (361 KB/s) - `./impact32.exe' saved [173288/173288] 
 
--2011-09-02 20:01:49--  http://downloads.sourceforge.net/corefonts/times32.exe 
Resolving downloads.sourceforge.net... 216.34.181.59 
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected. 
HTTP request sent, awaiting response... 301 Moved Permanently 
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe [following] 
--2011-09-02 20:01:49--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe 
Reusing existing connection to downloads.sourceforge.net:80. 
HTTP request sent, awaiting response... 302 Found 
Location: http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe [following] 
--2011-09-02 20:01:49--  http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe 
Resolving iweb.dl.sourceforge.net... 70.38.0.134, 2607:f748:10:12::5f:2 
Connecting to iweb.dl.sourceforge.net|70.38.0.134|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 661728 (646K) [application/x-msdos-program] 
Saving to: `./times32.exe' 
 
     0K .......... .......... .......... .......... ..........  7%  145K 4s 
    50K .......... .......... .......... .......... .......... 15%  162K 4s 
   100K .......... .......... .......... .......... .......... 23%  147K 3s 
   150K .......... .......... .......... .......... .......... 30%  132K 3s 
   200K .......... .......... .......... .......... .......... 38%  220K 3s 
   250K .......... .......... .......... .......... .......... 46%  126K 2s 
   300K .......... .......... .......... .......... .......... 54%  232K 2s 
   350K .......... .......... .......... .......... .......... 61%  374K 1s 
   400K .......... .......... .......... .......... .......... 69% 81.6K 1s 
   450K .......... .......... .......... .......... .......... 77%  232K 1s 
   500K .......... .......... .......... .......... .......... 85%  379K 1s 
   550K .......... .......... .......... .......... .......... 92%  399K 0s 
   600K .......... .......... .......... .......... ......    100%  191K=3.7s 
 
2011-09-02 20:01:53 (176 KB/s) - `./times32.exe' saved [661728/661728] 
 
--2011-09-02 20:01:53--  http://downloads.sourceforge.net/corefonts/trebuc32.exe 
Resolving downloads.sourceforge.net... 216.34.181.59 
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected. 
HTTP request sent, awaiting response... 301 Moved Permanently 
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe [following] 
--2011-09-02 20:01:55--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe 
Reusing existing connection to downloads.sourceforge.net:80. 
HTTP request sent, awaiting response... 302 Found 
Location: http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe [following] 
--2011-09-02 20:01:55--  http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe 
Resolving softlayer.dl.sourceforge.net... 74.86.229.28 
Connecting to softlayer.dl.sourceforge.net|74.86.229.28|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 357200 (349K) [application/octet-stream] 
Saving to: `./trebuc32.exe' 
 
     0K .......... .......... .......... .......... .......... 14%  169K 2s 
    50K .......... .......... .......... .......... .......... 28%  489K 1s 
   100K .......... .......... .......... .......... .......... 43%  478K 1s 
   150K .......... .......... .......... .......... .......... 57%  490K 0s 
   200K .......... .......... .......... .......... .......... 71%  490K 0s 
   250K .......... .......... .......... .......... .......... 86%  477K 0s 
   300K .......... .......... .......... .......... ........  100%  495K=0.9s 
 
2011-09-02 20:01:56 (383 KB/s) - `./trebuc32.exe' saved [357200/357200] 
 
--2011-09-02 20:01:56--  http://downloads.sourceforge.net/corefonts/verdan32.exe 
Resolving downloads.sourceforge.net... 216.34.181.59 
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected. 
HTTP request sent, awaiting response... 301 Moved Permanently 
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe [following] 
--2011-09-02 20:01:56--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe 
Reusing existing connection to downloads.sourceforge.net:80. 
HTTP request sent, awaiting response... 302 Found 
Location: http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe [following] 
--2011-09-02 20:01:56--  http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe 
Resolving voxel.dl.sourceforge.net... 208.122.28.11, 208.122.28.30, 208.122.28.2, ... 
Connecting to voxel.dl.sourceforge.net|208.122.28.11|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 351992 (344K) [application/octet-stream] 
Saving to: `./verdan32.exe' 
 
     0K .......... .......... .......... .......... .......... 14%  141K 2s 
    50K .......... .......... .......... .......... .......... 29%  358K 1s 
   100K .......... .......... .......... .......... .......... 43%  480K 1s 
   150K .......... .......... .......... .......... .......... 58%  484K 1s 
   200K .......... .......... .......... .......... .......... 72%  466K 0s 
   250K .......... .......... .......... .......... .......... 87%  505K 0s 
   300K .......... .......... .......... .......... ...       100%  495K=1.0s 
 
2011-09-02 20:01:58 (345 KB/s) - `./verdan32.exe' saved [351992/351992] 
 
--2011-09-02 20:01:58--  http://downloads.sourceforge.net/corefonts/webdin32.exe 
Resolving downloads.sourceforge.net... 216.34.181.59 
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected. 
HTTP request sent, awaiting response... 301 Moved Permanently 
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe [following] 
--2011-09-02 20:01:58--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe 
Reusing existing connection to downloads.sourceforge.net:80. 
HTTP request sent, awaiting response... 302 Found 
Location: http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe [following] 
--2011-09-02 20:01:58--  http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe 
Resolving iweb.dl.sourceforge.net... 70.38.0.134, 2607:f748:10:12::5f:2 
Connecting to iweb.dl.sourceforge.net|70.38.0.134|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 185072 (181K) [application/x-msdos-program] 
Saving to: `./webdin32.exe' 
 
     0K .......... .......... .......... .......... .......... 27%  178K 1s 
    50K .......... .......... .......... .......... .......... 55%  182K 0s 
   100K .......... .......... .......... .......... .......... 82%  462K 0s 
   150K .......... .......... ..........                      100%  503K=0.7s 
 
2011-09-02 20:01:59 (249 KB/s) - `./webdin32.exe' saved [185072/185072] 
 
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
No CIDSupplement specified for Dotum-Bold, defaulting to 0. 
No CIDSupplement specified for Batang-Regular, defaulting to 0. 
No CIDSupplement specified for DroidSansJapanese, defaulting to 0. 
No CIDSupplement specified for Dotum-Regular, defaulting to 0. 
No CIDSupplement specified for DroidSansJapanese-JaH, defaulting to 0. 
No CIDSupplement specified for Batang-Bold, defaulting to 0. 
Updating fontconfig cache for /usr/share/fonts/truetype/msttcorefonts 
 
Setting up ttf-umefont (411-1) ... 
Setting up winbind (2:3.4.7~dfsg-1ubuntu3.7) ... 
 * Starting the Winbind daemon winbind 
   ...done. 
 
Setting up wine (1.2.2-0ubuntu2~lucid1) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 kdebase-runtime 
 liblastfm0 
 libmysqlclient16 
Setting up liblastfm0 (0.4.0~git20090710-1) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing liblastfm0 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up kdebase-runtime (4:4.4.5-0ubuntu1) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing kdebase-runtime (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libmysqlclient16 (5.1.41-3ubuntu12.10) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libmysqlclient16 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
[/PHP]

---

