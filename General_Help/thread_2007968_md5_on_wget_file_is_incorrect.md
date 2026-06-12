---
title: "md5 on wget file is incorrect"
date: 2012-06-21
forum: General Help
---

### Post by sc0tti on 2012-06-21
Hi,

I'm having issues with wget on 64bit ubuntu 12.04.  32bit ubuntu 12.04 works fine.

I'm a ruby developer, using rbenv and ruby-build to manage my ruby versions and installations. 

running rbenv install 1.9.3-p194 produces the following 

s@ubuntu:~$ rbenv install 1.9.3-p194
Downloading [http://pyyaml.org/download/libyaml/yaml-0.1.4.tar.gz](http://pyyaml.org/download/libyaml/yaml-0.1.4.tar.gz)...
Installing yaml-0.1.4...
Installed yaml-0.1.4 to /home/s/.rbenv/versions/1.9.3-p194
Downloading [http://ftp.ruby-lang.org/pub/ruby/1.9/ruby-1.9.3-p194.tar.gz](http://ftp.ruby-lang.org/pub/ruby/1.9/ruby-1.9.3-p194.tar.gz)...

BUILD FAILED

Inspect or clean up the working tree at /tmp/ruby-build.20120622114547.11032
Results logged to /tmp/ruby-build.20120622114547.11032.log

Last 10 log lines:
/tmp/ruby-build.20120622114547.11032 ~
~
/tmp/ruby-build.20120622114547.11032 ~
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 57.2M  100 57.2M    0     0  1621k      0  0:00:36  0:00:36 --:--:-- 1469k

[COLOR=Red]gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error is not recoverable: exiting now[/COLOR]

Ive discovered that it appears to be an error with wget used within ruby-build to download the ruby tar.gz files.  I can reproduce this error manually outside ruby-build and rbenv.

The md5sum listed on the ruby site shows 1.9.3-p194 is bc0c715c69da4d1d8bd57069c19f6c0e

Downloading the ruby tar.gz file via wget produces the md5sum as c796faed4b6a43c6260c437a228e6623

s@optimus:~/Downloads$ wget [http://ftp.ruby-lang.org/pub/ruby/1.9/ruby-1.9.3-p194.tar.gz](http://ftp.ruby-lang.org/pub/ruby/1.9/ruby-1.9.3-p194.tar.gz)
--2012-06-22 11:41:40--  [http://ftp.ruby-lang.org/pub/ruby/1.9/ruby-1.9.3-p194.tar.gz](http://ftp.ruby-lang.org/pub/ruby/1.9/ruby-1.9.3-p194.tar.gz)
Resolving ftp.ruby-lang.org (ftp.ruby-lang.org)... 221.186.184.68
Connecting to ftp.ruby-lang.org (ftp.ruby-lang.org)|221.186.184.68|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 60016640 (57M) [application/x-tar]
Saving to: `ruby-1.9.3-p194.tar.gz'

100%[=========================================================================>] 60,016,640  1.39M/s   in 35s     

2012-06-22 11:42:15 (1.64 MB/s) - `ruby-1.9.3-p194.tar.gz' saved [60016640/60016640]

s@optimus:~/Downloads$ md5sum ruby-1.9.3-p194.tar.gz 
c796faed4b6a43c6260c437a228e6623  ruby-1.9.3-p194.tar.gz


Downloading via Firefox and checking the result md5sum produces the correct value

s@optimus:~/Downloads$ md5sum "ruby-1.9.3-p194(1).tar.gz"
bc0c715c69da4d1d8bd57069c19f6c0e  ruby-1.9.3-p194(1).tar.gz


I'm unsure why it appears to do this only on 64bit, 32bit works fine. I did notice the inconsistencies with the file size as well. Downloading via Firefox indicates the file is 11.9mb, but 57mb when requested with wget

Is this a bug in wget on 64bit? I need to deploy to 64bit production servers. 

Thanks in advance!

Scott

Ubuntu 12.04
Core i7 3.33ghz
Radeon 7850
16g Memory

---

