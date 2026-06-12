---
title: "Strange error when apt-get update"
date: 2006-05-18
forum: General Help
---

### Post by Isoss on 2006-05-18
I have the original repositories, and when I do apt-get update it out puts this:
```
isos@ubuntu:~$ sudo apt-get update
Get:1 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:2 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:3 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Hit http://archive.ubuntu.com breezy Release
Get:4 http://archive.ubuntu.com breezy-updates Release [30.9kB]
Get:5 http://archive.ubuntu.com breezy-backports Release [19.6kB]
Get:6 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:7 http://security.ubuntu.com breezy-security Release [27.0kB]
Hit http://archive.ubuntu.com breezy/main Packages
Get:8 http://security.ubuntu.com breezy-security/main Packages [60.2kB]
Get:9 http://security.ubuntu.com breezy-security/restricted Packages [4458B]
Get:10 http://security.ubuntu.com breezy-security/main Sources [17.3kB]
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Get:11 http://security.ubuntu.com breezy-security/restricted Sources [960B]
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/multiverse Sources
Ign http://archive.ubuntu.com breezy-updates/main Packages
Get:12 http://archive.ubuntu.com breezy-updates/restricted Packages [14B]
Get:13 http://archive.ubuntu.com breezy-updates/main Sources [18.6kB]
Get:14 http://archive.ubuntu.com breezy-updates/restricted Sources [14B]
Get:15 http://archive.ubuntu.com breezy-backports/main Packages [14.0kB]
Get:16 http://archive.ubuntu.com breezy-backports/restricted Packages [14B]
Get:17 http://archive.ubuntu.com breezy-backports/universe Packages [26.1kB]
Get:18 http://security.ubuntu.com breezy-security/universe Packages [35.0kB]
Get:19 http://security.ubuntu.com breezy-security/multiverse Packages [3830B]
Get:20 http://archive.ubuntu.com breezy-backports/multiverse Packages [1353B]
Get:21 http://security.ubuntu.com breezy-security/universe Sources [5007B]
Get:22 http://archive.ubuntu.com breezy-updates/main Packages [47.9kB]
99% [22 Packages gzip 0] [21 Sources 4264/5007B 85%]                10.4kB/s 0s
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com breezy-updates/main Packages
  Sub-process gzip returned an error code (1)
Hit http://security.ubuntu.com breezy-security/multiverse Sources
Fetched 264kB in 34s (7672B/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```
besides, each time I try to apt-get install or wget something it tells me i.e: 
```
Resolving switch.dl.sourceforge.net... 130.59.138.20, 2001:620:0:1b::20
Connecting to switch.dl.sourceforge.net|130.59.138.20|:80... failed: Connection refused.

```
But when I download the source package manually from it's website using firefox it works and after that I can install it as usual. but there is no way i can download anything using apt-get install or wget!!! what's wrong? I am pretty sure of my /etc/apt/apt.conf! and everything else is working so perfectly - expect for messengers which run on no condition but at meebo.com. 

I've been using ubuntu for more than a month now. I've learnt so so much in these forums and thanks to you guys cuz I guess no one uses linux within a mile arround me! and I never met a linux user my whole life! and so these forums were a blessing. But I am so embarrassed that I've 207 posts so far and all are trying to fix stupid probles like this. But I am really thankful for the helpfull ppl here and hope I can help in the things I've been through when I get over them! so bare with me for a while! still learning and I love linux and just working so hard so I can move 100% to linux and quit windows.

---

### Post by lukew on 2006-05-18
One or more of the repositories is either not there or in this case does not support your version / architecture. This might be because it is temporarily down.

Try the sources.list generator ontop of the unofficial starter guide.

I hope this helps.

Luke

---

