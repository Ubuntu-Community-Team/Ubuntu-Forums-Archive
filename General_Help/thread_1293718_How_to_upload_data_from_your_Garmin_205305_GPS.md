---
title: "How to upload data from your Garmin 205/305 GPS"
date: 2009-10-17
forum: General Help
---

### Post by dalesd on 2009-10-17
I got this great cycle computer/gps, the Garmin 305, but the only way for me to upload the data to the Garmin website to review it was to start up a Windows VM.  That got old fast, and I found a better way.

[http://braiden.org/?p=62](http://braiden.org/?p=62)

First, I installed garmin-forerunner-tools

```
sudo apt-get update
apt-get build-dep garmin-forerunner-tools
sudo apt-get build-dep garmin-forerunner-tools
sudo apt-get install garmin-forerunner-tools
```

Then I downloaded and installed garmintools from: [http://code.google.com/p/garmintools/](http://code.google.com/p/garmintools/)
The instructions are in the download, but it goes like this.  Extract the archive.  Then:
```
./configure
make
sudo make install
```

I wanted to put the scripts in my ~/bin drectory, but you an put this wherever you want.  (svn will put the files in a garmin directory for you.)
```
cd ~/bin
svn co http://linuxnerd.net/svn/trunk/projects/garmin
```

To upload your new files:
```
cd garmin
./saveruns && USER=braiden PASSWORD=abc123 ./uploadruns
```
You'll need to change the USER= and PASSWORD= fields to your garmin connect username and password.  If your password has special characters, enclose it in single quotes 'like this'

---

### Post by super.niels on 2009-12-26
I tried it with my garmin forerunner 205 and it works perfectly. Thanks:-)

---

### Post by guraknugen on 2010-12-31
> **dalesd said:**
> I got this great cycle computer/gps, the Garmin 305, but the only way for me to upload the data to the Garmin website to review it was to start up a Windows VM.  That got old fast, and I found a better way.

[http://braiden.org/?p=62](http://braiden.org/?p=62)

First, I installed garmin-forerunner-tools

```
sudo apt-get update
apt-get build-dep garmin-forerunner-tools
sudo apt-get build-dep garmin-forerunner-tools
sudo apt-get install garmin-forerunner-tools
```

Then I downloaded and installed garmintools from: [http://code.google.com/p/garmintools/](http://code.google.com/p/garmintools/)
The instructions are in the download, but it goes like this.  Extract the archive.  Then:
```
./configure
make
sudo make install
```

I wanted to put the scripts in my ~/bin drectory, but you an put this wherever you want.  (svn will put the files in a garmin directory for you.)
```
cd ~/bin
svn co http://linuxnerd.net/svn/trunk/projects/garmin
```

To upload your new files:
```
cd garmin
./saveruns && USER=braiden PASSWORD=abc123 ./uploadruns
```
You'll need to change the USER= and PASSWORD= fields to your garmin connect username and password.  If your password has special characters, enclose it in single quotes 'like this'

Sorry for replying to an old thread like this&#8230;

Just bought a Forerunner 305 and installed like the descriptions above. The &#8221;saveruns&#8221; command works fine, some GMN-files arrives in &#8221;/home/guraknugen/bin/garmin/2010/12&#8221;. It's the upload command that doesn't seem to work, maybe Garmin changed something at their site, here's my output:
> $ USER=me PASSWORD=mypassword ./uploadruns 
- validates
--2010-12-31 13:33:27--  [http://connect.garmin.com/signin](http://connect.garmin.com/signin)
Resolving connect.garmin.com... 95.100.14.235
Connecting to connect.garmin.com|95.100.14.235|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://connect.garmin.com/signin](https://connect.garmin.com/signin) [following]
--2010-12-31 13:33:27--  [https://connect.garmin.com/signin](https://connect.garmin.com/signin)
Connecting to connect.garmin.com|95.100.14.235|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 14136 (14K) [text/html]
Saving to: `/dev/null'

100%[========================================================================================>] 14,136      --.-K/s   in 0s      

2010-12-31 13:33:27 (142 MB/s) - `/dev/null' saved [14136/14136]

--2010-12-31 13:33:27--  [https://connect.garmin.com/signin](https://connect.garmin.com/signin)
Resolving connect.garmin.com... 95.100.14.235
Connecting to connect.garmin.com|95.100.14.235|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://connect.garmin.com/dashboard?cid=1060625](http://connect.garmin.com/dashboard?cid=1060625) [following]
--2010-12-31 13:33:28--  [http://connect.garmin.com/dashboard?cid=1060625](http://connect.garmin.com/dashboard?cid=1060625)
Connecting to connect.garmin.com|95.100.14.235|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `/dev/null'

    [ <=>                                                                                     ] 32,932      --.-K/s   in 0.005s  

2010-12-31 13:33:28 (5.86 MB/s) - `/dev/null' saved [32932]

--2010-12-31 13:33:28--  [http://connect.garmin.com/proxy/upload-service-1.1/json/upload](http://connect.garmin.com/proxy/upload-service-1.1/json/upload)
Resolving connect.garmin.com... 95.100.14.235
Connecting to connect.garmin.com|95.100.14.235|:80... connected.
HTTP request sent, awaiting response... 599 Unknown
2010-12-31 13:33:29 ERROR 599: Unknown.

blaha@blah:~/bin/garmin$

Of course I use my real USER and PASSWORD and not those mentioned above.

I tried to upload my run-files manually by logging in to the site manually with my web browser, and it works fine after converting the files to TCX format with the &#8221;gmn2tcx&#8221; script.

The installing instructions seems to work, but you could remove one line:
```
sudo apt-get update
apt-get build-dep garmin-forerunner-tools
sudo apt-get build-dep garmin-forerunner-tools
sudo apt-get install garmin-forerunner-tools
```

The second and the third line are the same except that &#8221;sudo&#8221; is missing on the second line&#8230;
```
sudo apt-get update
sudo apt-get build-dep garmin-forerunner-tools
sudo apt-get install garmin-forerunner-tools
```

---

### Post by dalesd on 2010-12-31
Yes, Garmin changed their site since I posted this.  I had to switch to the garmin-dev files over at Braiden.org.  It's mentioned in the comments over there.

---

### Post by guraknugen on 2010-12-31
> **dalesd said:**
> Yes, Garmin changed their site since I posted this.  I had to switch to the garmin-dev files over at Braiden.org.  It's mentioned in the comments over there.

Yes, you are right. I see that now. Updated and now it works.
Thanks!

---

### Post by guraknugen on 2010-12-31
Ignore this…

---

### Post by guraknugen on 2010-12-31
&#8230;and ignore this as well.

---

