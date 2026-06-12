---
title: "downloads.sourceforge.net"
date: 2010-06-19
forum: General Help
---

### Post by teddy379 on 2010-06-19
Hello,
I've been trying to install the ms fonts and msn messenger through PlayOnLinix and through the terminal but I always get an error like downloads.sourceforge.conet is no longer available (that is for the msn messenger download) or in case of the ms fonts it keeps trying and trying forever. Is it really down or should I change something to be able to download both?


teddy@teddy-desktop:~$ sh winetricks
Executing wget -O arial32.exe -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate [http://downloads.sourceforge.net/corefonts/arial32.exe](http://downloads.sourceforge.net/corefonts/arial32.exe)
--2010-06-19 11:07:49--  [http://downloads.sourceforge.net/corefonts/arial32.exe](http://downloads.sourceforge.net/corefonts/arial32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe) [following]
--2010-06-19 11:07:50--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe) [following]
--2010-06-19 11:07:50--  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe)
Resolving garr.dl.sourceforge.net... 32.1.7.96, 2001:760:ffff:b0::34
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Connecting to garr.dl.sourceforge.net|2001:760:ffff:b0::34|:80... failed: Network is unreachable.
Retrying.

--2010-06-19 11:08:36--  (try: 2)  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe)
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Connecting to garr.dl.sourceforge.net|2001:760:ffff:b0::34|:80... failed: Network is unreachable.
Retrying.

--2010-06-19 11:09:23--  (try: 3)  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe)
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Connecting to garr.dl.sourceforge.net|2001:760:ffff:b0::34|:80... failed: Network is unreachable.
Retrying.

--2010-06-19 11:10:11--  (try: 4)  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe)
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Connecting to garr.dl.sourceforge.net|2001:760:ffff:b0::34|:80... failed: Network is unreachable.
Retrying.

--2010-06-19 11:11:00--  (try: 5)  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe)
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Connecting to garr.dl.sourceforge.net|2001:760:ffff:b0::34|:80... failed: Network is unreachable.
Retrying.

--2010-06-19 11:11:50--  (try: 6)  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe)
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Connecting to garr.dl.sourceforge.net|2001:760:ffff:b0::34|:80... failed: Network is unreachable.
Retrying.

--2010-06-19 11:12:41--  (try: 7)  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe)
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Connecting to garr.dl.sourceforge.net|2001:760:ffff:b0::34|:80... failed: Network is unreachable.
Retrying.

--2010-06-19 11:13:33--  (try: 8)  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe)
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Connecting to garr.dl.sourceforge.net|2001:760:ffff:b0::34|:80... failed: Network is unreachable.
Retrying.

--2010-06-19 11:14:26--  (try: 9)  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe)
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Connecting to garr.dl.sourceforge.net|2001:760:ffff:b0::34|:80... failed: Network is unreachable.
Retrying.

--2010-06-19 11:15:20--  (try:10)  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe)


-----------------------------------------------------------------

I get this too


teddy@teddy-desktop:~$ sudo apt-get install msttcorefonts
[sudo] password for teddy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting ttf-mscorefonts-installer instead of msttcorefonts
ttf-mscorefonts-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Pollox on 2010-06-19
The thing at the end of your post just indicates that you have mscorefonts installed already.  Why do you need to install them using wine/PlayOnLinux?  Also, you might consider using one of the many IM programs that run natively in Ubuntu and work with msn messenger (such as empathy or pidgin).

---

### Post by teddy379 on 2010-06-20
Yea I'm using Pidgin atm and I was trying to download the msn in PlayOnLinux just for fun. Thing is, whenever I start up PlayOnLinux it tells me I should install the ms fonts. I tried copying ALL my fonts from Windows7 into every fonts folder I found in Ubuntu (the ones that belong to the system and to wine/POL) but I only see them when I use OpenOffice. After installing Gtalk for example on POL it was font-less. Not a single letter.

---

