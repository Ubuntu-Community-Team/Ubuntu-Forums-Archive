---
title: "Installing Stuck"
date: 2010-12-03
forum: General Help
---

### Post by teddy379 on 2010-12-03
Hey
I was installing Google Chrome on Ubuntu 10.10 earlier from a .deb package, and it got stuck at the "Applying Changes" part. I tried cancelling but it would keep stuck at cancelling too, the progress bar doesn't move at all. I tried rebooting and going to the Synaptic Package Manager but I got this error:
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```
So I ran ```
sudo dpkg --configure -a
``` and I got this:
```
teddy@teddy-P31-DS3L:~$ sudo dpkg --configure -a
[sudo] password for teddy: 
Setting up ttf-mscorefonts-installer (3.2) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2010-12-03 10:37:46--  http://downloads.sourceforge.net/corefonts/andale32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following]
--2010-12-03 10:37:47--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following]
--2010-12-03 10:37:47--  http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Resolving garr.dl.sourceforge.net... 32.1.7.96, 2001:760:ffff:b0::34
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Connecting to garr.dl.sourceforge.net|2001:760:ffff:b0::34|:80... failed: Network is unreachable.
--2010-12-03 10:38:09--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving switch.dl.sourceforge.net... 32.1.6.32, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|32.1.6.32|:80... failed: Connection timed out.
Connecting to switch.dl.sourceforge.net|2001:620:0:1b::21|:80... failed: Network is unreachable.
--2010-12-03 10:38:30--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=mesh.dl.sourceforge.net [following]
--2010-12-03 10:38:31--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=mesh.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe?download=&failedmirror=mesh.dl.sourceforge.net [following]
--2010-12-03 10:38:31--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe?download=&failedmirror=mesh.dl.sourceforge.net
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following]
--2010-12-03 10:38:32--  http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Resolving garr.dl.sourceforge.net... 32.1.7.96
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Giving up.

--2010-12-03 10:38:53--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving dfn.dl.sourceforge.net... 194.95.236.130
Connecting to dfn.dl.sourceforge.net|194.95.236.130|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net [following]
--2010-12-03 10:38:54--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe?download=&failedmirror=dfn.dl.sourceforge.net [following]
--2010-12-03 10:38:54--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe?download=&failedmirror=dfn.dl.sourceforge.net
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following]
--2010-12-03 10:38:54--  http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Resolving garr.dl.sourceforge.net... 32.1.7.96
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Giving up.

--2010-12-03 10:39:16--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving heanet.dl.sourceforge.net... 32.1.7.112, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|32.1.7.112|:80... failed: Connection timed out.
Connecting to heanet.dl.sourceforge.net|2001:770:18:aa40::c101:c142|:80... failed: Network is unreachable.
--2010-12-03 10:39:37--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving jaist.dl.sourceforge.net... 32.1.2.0, 2001:200:141:feed::feed
Connecting to jaist.dl.sourceforge.net|32.1.2.0|:80... failed: Connection timed out.
Connecting to jaist.dl.sourceforge.net|2001:200:141:feed::feed|:80... failed: Network is unreachable.
--2010-12-03 10:39:58--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving nchc.dl.sourceforge.net... 32.1.14.16, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|32.1.14.16|:80... failed: Connection timed out.
Connecting to nchc.dl.sourceforge.net|2001:e10:ffff:1f02::17|:80... failed: Network is unreachable.
--2010-12-03 10:40:19--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving ufpr.dl.sourceforge.net... 200.17.202.1
Connecting to ufpr.dl.sourceforge.net|200.17.202.1|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net [following]
--2010-12-03 10:40:23--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe?download=&failedmirror=ufpr.dl.sourceforge.net [following]
--2010-12-03 10:40:23--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe?download=&failedmirror=ufpr.dl.sourceforge.net
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following]
--2010-12-03 10:40:24--  http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Resolving garr.dl.sourceforge.net... 32.1.7.96
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Giving up.

--2010-12-03 10:40:45--  http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internode.dl.sourceforge.net... 150.101.135.12
Connecting to internode.dl.sourceforge.net|150.101.135.12|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net [following]
--2010-12-03 10:40:46--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe?download=&failedmirror=internode.dl.sourceforge.net [following]
--2010-12-03 10:40:47--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe?download=&failedmirror=internode.dl.sourceforge.net
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following]
--2010-12-03 10:40:47--  http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Resolving garr.dl.sourceforge.net... 32.1.7.96
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Giving up.

--2010-12-03 10:41:08--  http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving voxel.dl.sourceforge.net... 208.122.31.4, 208.122.31.24, 208.122.31.26, ...
Connecting to voxel.dl.sourceforge.net|208.122.31.4|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=voxel.dl.sourceforge.net [following]
--2010-12-03 10:41:09--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=voxel.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe?download=&failedmirror=voxel.dl.sourceforge.net [following]
--2010-12-03 10:41:09--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe?download=&failedmirror=voxel.dl.sourceforge.net
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following]
--2010-12-03 10:41:10--  http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Resolving garr.dl.sourceforge.net... 32.1.7.96
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Giving up.

--2010-12-03 10:41:31--  http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving kent.dl.sourceforge.net... 212.219.56.167
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=kent.dl.sourceforge.net [following]
--2010-12-03 10:41:32--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=kent.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe?download=&failedmirror=kent.dl.sourceforge.net [following]
--2010-12-03 10:41:33--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe?download=&failedmirror=kent.dl.sourceforge.net
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following]
--2010-12-03 10:41:33--  http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Resolving garr.dl.sourceforge.net... 32.1.7.96
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Giving up.

--2010-12-03 10:41:54--  http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internap.dl.sourceforge.net... 69.88.152.3
Connecting to internap.dl.sourceforge.net|69.88.152.3|:80... connected.
HTTP request sent, awaiting response... 

```
And it keeps trying over and over. Atm I can't install anything else as I've tried to install Skype from the Software Centre and it got stuck too.

---

### Post by sikander3786 on 2010-12-03
First of all search Software Center for any software you intend to install instead of downloading and installing a .deb.

Do these commands and post the output.

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get install -f
```

If unsuccessful,

```
sudo apt-get remove --purge ttf-mscorefonts-installer
```

Please post the complete output for each of them.

---

### Post by teddy379 on 2010-12-04
First
```
teddy@teddy-P31-DS3L:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for teddy: 
Hit http://eg.archive.ubuntu.com maverick Release.gpg
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Get:1 http://eg.archive.ubuntu.com maverick-updates Release.gpg [198B]
Get:2 http://extras.ubuntu.com maverick Release.gpg [65B]                      
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US         
Hit http://extras.ubuntu.com maverick Release                                
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Hit http://security.ubuntu.com maverick-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://eg.archive.ubuntu.com maverick Release
Hit http://extras.ubuntu.com maverick/main Sources                             
Get:3 http://eg.archive.ubuntu.com maverick-updates Release [31.4kB]           
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://extras.ubuntu.com maverick/main i386 Packages                     
Hit http://security.ubuntu.com maverick-security Release                     
Hit http://security.ubuntu.com maverick-security/main Sources
Hit http://eg.archive.ubuntu.com maverick/main Sources
Hit http://eg.archive.ubuntu.com maverick/restricted Sources
Hit http://eg.archive.ubuntu.com maverick/universe Sources
Hit http://eg.archive.ubuntu.com maverick/multiverse Sources
Hit http://eg.archive.ubuntu.com maverick/main i386 Packages
Hit http://eg.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://security.ubuntu.com maverick-security/restricted Sources
Hit http://security.ubuntu.com maverick-security/universe Sources
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/main i386 Packages
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages
Hit http://eg.archive.ubuntu.com maverick/universe i386 Packages
Hit http://eg.archive.ubuntu.com maverick/multiverse i386 Packages
Get:4 http://eg.archive.ubuntu.com maverick-updates/main Sources [46.3kB]
Hit http://security.ubuntu.com maverick-security/universe i386 Packages
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages
Get:5 http://eg.archive.ubuntu.com maverick-updates/restricted Sources [14B]
Get:6 http://eg.archive.ubuntu.com maverick-updates/universe Sources [15.6kB]
Get:7 http://eg.archive.ubuntu.com maverick-updates/multiverse Sources [1,068B]
Get:8 http://eg.archive.ubuntu.com maverick-updates/main i386 Packages [124kB]
Get:9 http://eg.archive.ubuntu.com maverick-updates/restricted i386 Packages [14B]
Get:10 http://eg.archive.ubuntu.com maverick-updates/universe i386 Packages [53.3kB]
Get:11 http://eg.archive.ubuntu.com maverick-updates/multiverse i386 Packages [2,522B]
Fetched 274kB in 4s (64.6kB/s)                          
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

2nd
```
teddy@teddy-P31-DS3L:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

3rd
```
teddy@teddy-P31-DS3L:~$ sudo apt-get remove --purge ttf-mscorefonts-installer
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

And then I tried sudo dpkg --configure -a, it keeps trying and trying

```
teddy@teddy-P31-DS3L:~$ sudo dpkg --configure -a
Setting up ttf-mscorefonts-installer (3.2) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2010-12-04 09:06:00--  http://downloads.sourceforge.net/corefonts/andale32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following]
--2010-12-04 09:06:01--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following]
--2010-12-04 09:06:01--  http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Resolving garr.dl.sourceforge.net... 32.1.7.96, 2001:760:ffff:b0::34
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Connecting to garr.dl.sourceforge.net|2001:760:ffff:b0::34|:80... failed: Network is unreachable.
--2010-12-04 09:06:23--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving switch.dl.sourceforge.net... 32.1.6.32, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|32.1.6.32|:80... failed: Connection timed out.
Connecting to switch.dl.sourceforge.net|2001:620:0:1b::21|:80... failed: Network is unreachable.
--2010-12-04 09:06:44--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=mesh.dl.sourceforge.net [following]
--2010-12-04 09:06:45--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=mesh.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe?download=&failedmirror=mesh.dl.sourceforge.net [following]
--2010-12-04 09:06:45--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe?download=&failedmirror=mesh.dl.sourceforge.net
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following]
--2010-12-04 09:06:46--  http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Resolving garr.dl.sourceforge.net... 32.1.7.96
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... 

```

And yea, I still can't use the Package Manager yet as it still gives me the same error.

---

### Post by teddy379 on 2010-12-04
bump

---

### Post by idi0tf0wl on 2010-12-04
try running this quick one-two combo:
```
sudo apt-get --purge remove dpkg
```
and then
```
sudo apt-get install dpkg
```

---

### Post by teddy379 on 2010-12-04
What about the timing out thing, I also get it trying to download those fonts when they're needed by wine.

---

### Post by sikander3786 on 2010-12-04
> **teddy379 said:**
> What about the timing out thing, I also get it trying to download those fonts when they're needed by wine.
Does the internet work just fine in your browser? Are you behind a proxy?

---

### Post by teddy379 on 2010-12-04
Yea my internet is fine. I haven't tried the last suggestion yet as I haven't got a chance yet. I'll report shortly.

---

### Post by teddy379 on 2010-12-04
```
teddy@teddy-P31-DS3L:~$ sudo apt-get --purge remove dpkg
[sudo] password for teddy: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
teddy@teddy-P31-DS3L:~$ sudo apt-get install dpkg
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

Still, nothing new :(
It looks like the fonts are the problem now, that I can't download them or anything as it showed above. Any help?

---

### Post by sikander3786 on 2010-12-05
Feels like a problem with wget now.

I don't know much about that but look under /etc/wgetrc for details.

```
cat /etc/wgetrc
```

Not sure though :-k

---

### Post by teddy379 on 2010-12-05
Well I'm not a pro linux user. I really need a quick and easy fix for this, I don't feel like reinstalling Ubuntu all over :(

---

### Post by Quackers on 2010-12-05
Have you run ```
sudo dpkg --configure -a
``` as advised in the error message?

---

### Post by teddy379 on 2010-12-05
> **Quackers said:**
> Have you run ```
sudo dpkg --configure -a
``` as advised in the error message?

Yes, look at my first post. It tried downloading those fonts apparently and it got stuck there. When I had Ubuntu installed a few months ago, it got stuck trying to download those fonts when wine needed them. So no, the ```
sudo dpkg --configure -a
``` isn't working as it's not able to download those fonts since the server has been changed or smth.

---

### Post by teddy379 on 2010-12-06
This was my thread but it seems the forum over there wasn't as active so I'll give it a try here

[http://ubuntuforums.org/showthread.php?t=1636410](http://ubuntuforums.org/showthread.php?t=1636410)

---

### Post by dcstar on 2010-12-06
> **teddy379 said:**
> This was my thread but it seems the forum over there wasn't as active so I'll give it a try here

[http://ubuntuforums.org/showthread.php?t=1636410](http://ubuntuforums.org/showthread.php?t=1636410)

Stop expecting that you should be getting immediate attention, people are not here 24x7 to serve you.

Just wait for others to reply.

---

### Post by Sef on 2010-12-06
Merged threads because they are on the same problem.

---

### Post by teddy379 on 2010-12-06
> **Sef said:**
> Merged threads because they are on the same problem.

Thanks

---

### Post by teddy379 on 2010-12-06
Actually I got it fixed, I simply left: 
sudo dpkg --configure -a trying for a while and it worked. Thanks for the help.

---

### Post by sikander3786 on 2010-12-06
Glad you got it fixed.

But out of curiosity, were you previously not letting *dpkg --configure -a* to run until it finished the job? You were quitting that while in the process or such?

---

### Post by teddy379 on 2010-12-06
> **sikander3786 said:**
> Glad you got it fixed.

But out of curiosity, were you previously not letting *dpkg --configure -a* to run until it finished the job? You were quitting that while in the process or such?
Yea, I guess I didn't fully read the output as soon as I noticed words like microsoft core fonts, server has been changed, unable to reach and all that lol. I told you, I've always got the same problem when Wine needed the same fonts, winetricks actually.

---

### Post by teddy379 on 2010-12-06
> **sikander3786 said:**
> Glad you got it fixed.

But out of curiosity, were you previously not letting *dpkg --configure -a* to run until it finished the job? You were quitting that while in the process or such?

So, I was trying to install Steam and following the steps I ended up with this:

```
teddy@teddy-P31-DS3L:~$ wget http://www.kegel.com/wine/winetricks
--2010-12-06 22:13:33--  http://www.kegel.com/wine/winetricks
Resolving www.kegel.com... 216.92.86.126
Connecting to www.kegel.com|216.92.86.126|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 190672 (186K) [text/plain]
Saving to: `winetricks'

100%[======================================>] 190,672     56.0K/s   in 3.3s    

2010-12-06 22:13:37 (56.0 KB/s) - `winetricks' saved [190672/190672]

teddy@teddy-P31-DS3L:~$ sh winetricks corefonts allfonts tahoma gecko gecko-dbg vcrun2005
Executing wget -O arial32.exe -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate http://downloads.sourceforge.net/corefonts/arial32.exe
--2010-12-06 22:13:51--  http://downloads.sourceforge.net/corefonts/arial32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe [following]
--2010-12-06 22:13:54--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe [following]
--2010-12-06 22:13:56--  http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Resolving garr.dl.sourceforge.net... 32.1.7.96, 2001:760:ffff:b0::34
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Connecting to garr.dl.sourceforge.net|2001:760:ffff:b0::34|:80... failed: Network is unreachable.
Retrying.

--2010-12-06 22:14:19--  (try: 2)  http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Connecting to garr.dl.sourceforge.net|2001:760:ffff:b0::34|:80... failed: Network is unreachable.
Retrying.

--2010-12-06 22:14:42--  (try: 3)  http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Connecting to garr.dl.sourceforge.net|2001:760:ffff:b0::34|:80... failed: Network is unreachable.
Retrying.

--2010-12-06 22:15:06--  (try: 4)  http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Connecting to garr.dl.sourceforge.net|2001:760:ffff:b0::34|:80... failed: Network is unreachable.
Retrying.

--2010-12-06 22:15:31--  (try: 5)  http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Connecting to garr.dl.sourceforge.net|2001:760:ffff:b0::34|:80... failed: Network is unreachable.
Retrying.

--2010-12-06 22:15:57--  (try: 6)  http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Connecting to garr.dl.sourceforge.net|2001:760:ffff:b0::34|:80... failed: Network is unreachable.
Retrying.

--2010-12-06 22:16:24--  (try: 7)  http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Connecting to garr.dl.sourceforge.net|2001:760:ffff:b0::34|:80... failed: Network is unreachable.
Retrying.

--2010-12-06 22:16:52--  (try: 8)  http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Connecting to garr.dl.sourceforge.net|2001:760:ffff:b0::34|:80... failed: Network is unreachable.
Retrying.

--2010-12-06 22:17:21--  (try: 9)  http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Connecting to garr.dl.sourceforge.net|2001:760:ffff:b0::34|:80... failed: Network is unreachable.
Retrying.

--2010-12-06 22:17:51--  (try:10)  http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Connecting to garr.dl.sourceforge.net|2001:760:ffff:b0::34|:80... failed: Network is unreachable.
Retrying.

--2010-12-06 22:18:22--  (try:11)  http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Connecting to garr.dl.sourceforge.net|2001:760:ffff:b0::34|:80... failed: Network is unreachable.
Retrying.

--2010-12-06 22:18:53--  (try:12)  http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Connecting to garr.dl.sourceforge.net|2001:760:ffff:b0::34|:80... failed: Network is unreachable.
Retrying.

--2010-12-06 22:19:24--  (try:13)  http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Connecting to garr.dl.sourceforge.net|2001:760:ffff:b0::34|:80... failed: Network is unreachable.
Retrying.

```It's really bothering me. Any help would be appreciated.

---

### Post by Sociologist on 2010-12-07
Try to uncomment and set https_proxy, http_proxy and ftp_proxy in /etc/wgetrc

---

### Post by teddy379 on 2010-12-10
> **Sociologist said:**
> Try to uncomment and set https_proxy, http_proxy and ftp_proxy in /etc/wgetrc

I don't really get it.
I assume I should edit the wgetrc file, but what do I exactly should type in there?

---

