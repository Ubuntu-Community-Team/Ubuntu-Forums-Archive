---
title: "Is anyone else unable to update?"
date: 2010-10-05
forum: General Help
---

### Post by Chris1274 on 2010-10-05
When I try to update I'm getting this:
```
sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the list directory

```
Is there some kind of maintenance going on with the repository, or could this be a problem on my end?

---

### Post by WorMzy on 2010-10-05
That's a client-side error - it's on your PC. It looks as though apt didn't exit correctly the last time you ran it, and, as a result, the lock file hasn't been removed. Look in the list of processes for instances of apt:
```
ps aux | grep apt
```
If you get a result for something suspicious (post all the output if you're unsure), then kill it with:
```
kill <process id>
```
It should work after that.

You could probably kill the process through gnome-system-monitor too, if you'd prefer a GUI solution.

---

### Post by coffeecat on 2010-10-05
It's your end. Do you have  Synaptic, Update Manager or Software Centre open? Close them before running apt-get.

---

### Post by Chris1274 on 2010-10-05
I just tried rebooting, but I still get the same error.

---

### Post by Chris1274 on 2010-10-05
Here's the output:
```
ps aux | grep apt
1000      1724  0.0  0.0   7624   908 pts/0    S+   15:14   0:00 grep --color=auto apt

```
doesn't seem like much

---

### Post by Chris1274 on 2010-10-05
can I remove the lock file myself or would that mess things up?

---

### Post by Majorflam on 2010-10-05
I'm having problems updating:

Getting the error that it can't download the files and I should check my internet connection, my connection is fine.

> 
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution/libevolution_2.30.3-1ubuntu5_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution/libevolution_2.30.3-1ubuntu5_i386.deb) 404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution_2.30.3-1ubuntu5_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution_2.30.3-1ubuntu5_i386.deb) 404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-common_2.30.3-1ubuntu5_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-common_2.30.3-1ubuntu5_all.deb) 404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-plugins_2.30.3-1ubuntu5_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-plugins_2.30.3-1ubuntu5_i386.deb) 404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-sql-mysql_4.7.0-0ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-sql-mysql_4.7.0-0ubuntu3_i386.deb) 404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-opengl-dev_4.7.0-0ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-opengl-dev_4.7.0-0ubuntu3_i386.deb) 404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/qt4-qmake_4.7.0-0ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/qt4-qmake_4.7.0-0ubuntu3_i386.deb) 404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-dev_4.7.0-0ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-dev_4.7.0-0ubuntu3_i386.deb) 404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-qt3support_4.7.0-0ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-qt3support_4.7.0-0ubuntu3_i386.deb) 404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-help_4.7.0-0ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-help_4.7.0-0ubuntu3_i386.deb) 404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-declarative_4.7.0-0ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-declarative_4.7.0-0ubuntu3_i386.deb) 404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-sql_4.7.0-0ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-sql_4.7.0-0ubuntu3_i386.deb) 404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-svg_4.7.0-0ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-svg_4.7.0-0ubuntu3_i386.deb) 404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-scripttools_4.7.0-0ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-scripttools_4.7.0-0ubuntu3_i386.deb) 404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-designer_4.7.0-0ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-designer_4.7.0-0ubuntu3_i386.deb) 404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-opengl_4.7.0-0ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-opengl_4.7.0-0ubuntu3_i386.deb) 404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtgui4_4.7.0-0ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtgui4_4.7.0-0ubuntu3_i386.deb) 404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-script_4.7.0-0ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-script_4.7.0-0ubuntu3_i386.deb) 404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-xmlpatterns_4.7.0-0ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-xmlpatterns_4.7.0-0ubuntu3_i386.deb) 404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-network_4.7.0-0ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-network_4.7.0-0ubuntu3_i386.deb) 404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-dbus_4.7.0-0ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-dbus_4.7.0-0ubuntu3_i386.deb) 404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-xml_4.7.0-0ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-xml_4.7.0-0ubuntu3_i386.deb) 404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-test_4.7.0-0ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-test_4.7.0-0ubuntu3_i386.deb) 404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtcore4_4.7.0-0ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtcore4_4.7.0-0ubuntu3_i386.deb) 404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-sso-client/ubuntu-sso-client_1.0.2-0ubuntu1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-sso-client/ubuntu-sso-client_1.0.2-0ubuntu1_all.deb) 404  Not Found



---

### Post by droogiemon on 2010-10-05
I am also having a problem. But it seems to be just a connection issue.
I used the Synaptic Package Manager just 2 days ago with no problem.

Now I can't even ping the repository : us.archive.ubuntu.com

I tried to change repositories but the package I needed wasn't on the others.

You could try changing repositories.

---

### Post by WorMzy on 2010-10-05
> **Chris1274 said:**
> Here's the output:
```
ps aux | grep apt
1000      1724  0.0  0.0   7624   908 pts/0    S+   15:14   0:00 grep --color=auto apt

```
doesn't seem like much

Ahah, that's the command you just ran, it found itself.

Yeah, if restarting didn't help, then manually remove the lock file.

```
sudo rm /var/lib/apt/lists/lock
```

---

### Post by WorMzy on 2010-10-05
> **Majorflam said:**
> I'm having problems updating:

Getting the error that it can't download the files and I should check my internet connection, my connection is fine.

Your package lists are out of date, you just need to run ```
sudo apt-get update
```

---

### Post by dave_1212 on 2010-10-05
I am experiencing the same issue. I am getting a connection timeout to us.archive.ubuntu.com:80 when using sudo apt-get update

This is my first experience with Ubuntu (10.04.1) and I've done searching that turned up results about the problem being related to proxy settings, which I'm not using.

I thought it might be something else going on when I saw this post.

Any ideas?

Thanks

---

### Post by Chris1274 on 2010-10-05
> **WorMzy said:**
> Ahah, that's the command you just ran, it found itself.

Yeah, if restarting didn't help, then manually remove the lock file.

```
sudo rm /var/lib/apt/lists/lock
```

Hmm. I'm getting some new weirdness:

```
 sudo apt-get update
Err http://archive.canonical.com lucid Release.gpg                             
  Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (110: Connection timed out)
Err http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US       
  Unable to connect to archive.canonical.com:http:
Ign http://archive.canonical.com lucid Release                                 
Ign http://archive.canonical.com lucid/partner Packages                        
Ign http://archive.canonical.com lucid/partner Packages                        
Err http://archive.canonical.com lucid/partner Packages                        
  Unable to connect to archive.canonical.com:http:
Err http://security.ubuntu.com lucid-security Release.gpg                      
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (110: Connection timed out) [IP: 91.189.88.37 80]
Err http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Ign http://security.ubuntu.com lucid-security Release                          
Ign http://security.ubuntu.com lucid-security/main Packages
Ign http://security.ubuntu.com lucid-security/restricted Packages
Ign http://security.ubuntu.com lucid-security/main Sources
Ign http://security.ubuntu.com lucid-security/restricted Sources
Ign http://security.ubuntu.com lucid-security/universe Packages
Ign http://security.ubuntu.com lucid-security/universe Sources
Ign http://security.ubuntu.com lucid-security/multiverse Packages
Ign http://security.ubuntu.com lucid-security/multiverse Sources
Ign http://security.ubuntu.com lucid-security/main Packages
Ign http://security.ubuntu.com lucid-security/restricted Packages
Ign http://security.ubuntu.com lucid-security/main Sources
Ign http://security.ubuntu.com lucid-security/restricted Sources
Ign http://security.ubuntu.com lucid-security/universe Packages
Ign http://security.ubuntu.com lucid-security/universe Sources
Ign http://security.ubuntu.com lucid-security/multiverse Packages
Ign http://security.ubuntu.com lucid-security/multiverse Sources
Err http://security.ubuntu.com lucid-security/main Packages
Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err http://security.ubuntu.com lucid-security/restricted Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err http://security.ubuntu.com lucid-security/main Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err http://security.ubuntu.com lucid-security/restricted Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err http://security.ubuntu.com lucid-security/universe Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err http://security.ubuntu.com lucid-security/universe Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err http://security.ubuntu.com lucid-security/multiverse Packages
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err http://security.ubuntu.com lucid-security/multiverse Sources
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err http://us.archive.ubuntu.com lucid Release.gpg      ^A
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.30). - connect (110: Connection timed out) [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com lucid-updates Release.gpg
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]
Ign http://us.archive.ubuntu.com lucid Release          
Ign http://us.archive.ubuntu.com lucid-updates Release
Ign http://us.archive.ubuntu.com lucid/main Packages
Ign http://us.archive.ubuntu.com lucid/restricted Packages
Ign http://us.archive.ubuntu.com lucid/main Sources
Ign http://us.archive.ubuntu.com lucid/restricted Sources
Ign http://us.archive.ubuntu.com lucid/universe Packages
Ign http://us.archive.ubuntu.com lucid/universe Sources
Ign http://us.archive.ubuntu.com lucid/multiverse Packages
Ign http://us.archive.ubuntu.com lucid/multiverse Sources
Ign http://us.archive.ubuntu.com lucid-updates/main Packages
Ign http://us.archive.ubuntu.com lucid-updates/restricted Packages
Ign http://us.archive.ubuntu.com lucid-updates/main Sources
Ign http://us.archive.ubuntu.com lucid-updates/restricted Sources
Ign http://us.archive.ubuntu.com lucid-updates/universe Packages
Ign http://us.archive.ubuntu.com lucid-updates/universe Sources
Ign http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Ign http://us.archive.ubuntu.com lucid/main Packages
Ign http://us.archive.ubuntu.com lucid/restricted Packages
Ign http://us.archive.ubuntu.com lucid/main Sources
Ign http://us.archive.ubuntu.com lucid/restricted Sources
Ign http://us.archive.ubuntu.com lucid/universe Packages
Ign http://us.archive.ubuntu.com lucid/universe Sources
Ign http://us.archive.ubuntu.com lucid/multiverse Packages
Ign http://us.archive.ubuntu.com lucid/multiverse Sources
Ign http://us.archive.ubuntu.com lucid-updates/main Packages
Ign http://us.archive.ubuntu.com lucid-updates/restricted Packages
Ign http://us.archive.ubuntu.com lucid-updates/main Sources
Ign http://us.archive.ubuntu.com lucid-updates/restricted Sources
Ign http://us.archive.ubuntu.com lucid-updates/universe Packages
Ign http://us.archive.ubuntu.com lucid-updates/universe Sources
Ign http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Err http://us.archive.ubuntu.com lucid/main Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com lucid/restricted Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com lucid/main Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com lucid/restricted Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com lucid/universe Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com lucid/universe Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com lucid/multiverse Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com lucid/multiverse Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com lucid-updates/main Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com lucid-updates/restricted Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com lucid-updates/main Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com lucid-updates/restricted Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com lucid-updates/universe Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com lucid-updates/universe Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com lucid-updates/multiverse Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]
Err http://us.archive.ubuntu.com lucid-updates/multiverse Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg  Could not connect to us.archive.ubuntu.com:80 (91.189.88.30). - connect (110: Connection timed out) [IP: 91.189.88.30 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (110: Connection timed out) [IP: 91.189.88.37 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg  Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (110: Connection timed out)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_US.bz2  Unable to connect to archive.canonical.com:http:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-amd64/Packages.gz  Unable to connect to archive.canonical.com:http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-amd64/Packages.gz  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-amd64/Packages.gz  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-amd64/Packages.gz  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-amd64/Packages.gz  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-amd64/Packages.gz  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-amd64/Packages.gz  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-amd64/Packages.gz  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.gz  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-amd64/Packages.gz  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-amd64/Packages.gz  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-amd64/Packages.gz  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.88.30 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by scrooge_74 on 2010-10-05
Try other repositories I was able to update/upgrade just fine

---

### Post by Chris1274 on 2010-10-05
Here's my /etc/apt/sources.list:
```
# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://archive.canonical.com/ubuntu lucid partner


```What other repositories are available?

---

### Post by coffeecat on 2010-10-05
> **Chris1274 said:**
> What other repositories are available?

Plenty.

Go to System > Administration > Software Sources and under "Download from" you can select the main server, your country or "other". Choose other and you can select any you like from a very long list or click on the 'Select Best Server' button.

---

### Post by Chris1274 on 2010-10-05
> **coffeecat said:**
> Plenty.

Go to System > Administration > Software Sources and under "Download from" you can select the main server, your country or "other". Choose other and you can select any you like from a very long list or click on the 'Select Best Server' button.

Excellent, thank you, this fix worked.

---

### Post by ryann2k1 on 2010-11-23
Hi, I am a newbie here.

I am experiencing the same problem when installing the simspark environment.

Code.
[HTML]Ign cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1) lucid Release.gpg
Ign cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1)/ lucid/restricted Translation-en_US
Ign cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1) lucid Release
Ign cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1) lucid/main Packages
Ign cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1) lucid/restricted Packages
Ign cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1) lucid/main Packages
Ign cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1) lucid/restricted Packages
Err cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1) lucid/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1) lucid/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit http://kambing.ui.ac.id lucid Release.gpg                                  
Ign http://kambing.ui.ac.id/ubuntu/ lucid/main Translation-en_US               
Ign http://kambing.ui.ac.id/ubuntu/ lucid/restricted Translation-en_US         
Ign http://kambing.ui.ac.id/ubuntu/ lucid/universe Translation-en_US           
Ign http://kambing.ui.ac.id/ubuntu/ lucid/multiverse Translation-en_US         
Hit http://kambing.ui.ac.id lucid-updates Release.gpg                          
Ign http://kambing.ui.ac.id/ubuntu/ lucid-updates/main Translation-en_US       
Ign http://kambing.ui.ac.id/ubuntu/ lucid-updates/restricted Translation-en_US 
Ign http://kambing.ui.ac.id/ubuntu/ lucid-updates/universe Translation-en_US   
Ign http://kambing.ui.ac.id/ubuntu/ lucid-updates/multiverse Translation-en_US 
Hit http://us.archive.ubuntu.com lucid-backports Release.gpg                   
Hit http://archive.canonical.com lucid Release.gpg                             
Hit http://kambing.ui.ac.id lucid-security Release.gpg                         
Ign http://kambing.ui.ac.id/ubuntu/ lucid-security/main Translation-en_US      
Ign http://kambing.ui.ac.id/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://kambing.ui.ac.id/ubuntu/ lucid-security/universe Translation-en_US  
Ign http://kambing.ui.ac.id/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://kambing.ui.ac.id lucid Release                                      
Hit http://kambing.ui.ac.id lucid-updates Release                              
Hit http://kambing.ui.ac.id lucid-security Release                             
Hit http://kambing.ui.ac.id lucid/main Packages                                
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
Hit http://kambing.ui.ac.id lucid/restricted Packages                          
Hit http://kambing.ui.ac.id lucid/main Sources                                 
Hit http://kambing.ui.ac.id lucid/restricted Sources                           
Hit http://kambing.ui.ac.id lucid/universe Packages                            
Hit http://kambing.ui.ac.id lucid/universe Sources                             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
Hit http://kambing.ui.ac.id lucid/multiverse Packages                          
Hit http://kambing.ui.ac.id lucid/multiverse Sources                           
Hit http://kambing.ui.ac.id lucid-updates/main Packages                        
Hit http://kambing.ui.ac.id lucid-updates/restricted Packages                  
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
Hit http://kambing.ui.ac.id lucid-updates/main Sources                         
Hit http://kambing.ui.ac.id lucid-updates/restricted Sources                   
Hit http://kambing.ui.ac.id lucid-updates/universe Packages                    
Hit http://kambing.ui.ac.id lucid-updates/universe Sources                     
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
Hit http://kambing.ui.ac.id lucid-updates/multiverse Packages                  
Hit http://kambing.ui.ac.id lucid-updates/multiverse Sources                   
Hit http://kambing.ui.ac.id lucid-security/main Packages                       
Hit http://us.archive.ubuntu.com lucid-backports Release                       
Hit http://kambing.ui.ac.id lucid-security/restricted Packages                 
Hit http://kambing.ui.ac.id lucid-security/main Sources                        
Hit http://kambing.ui.ac.id lucid-security/restricted Sources                  
Hit http://kambing.ui.ac.id lucid-security/universe Packages         
Hit http://us.archive.ubuntu.com lucid-backports/main Packages       
Hit http://kambing.ui.ac.id lucid-security/universe Sources          
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Hit http://us.archive.ubuntu.com lucid-backports/restricted Packages 
Hit http://kambing.ui.ac.id lucid-security/multiverse Packages       
Hit http://archive.canonical.com lucid Release                       
Hit http://kambing.ui.ac.id lucid-security/multiverse Sources                  
Hit http://us.archive.ubuntu.com lucid-backports/universe Packages   
Hit http://archive.canonical.com lucid/partner Packages              
Hit http://archive.canonical.com lucid/partner Sources               
Hit http://us.archive.ubuntu.com lucid-backports/multiverse Packages 
Hit http://us.archive.ubuntu.com lucid-backports/main Sources
Get:1 http://packages.medibuntu.org lucid Release.gpg [197B]
Hit http://us.archive.ubuntu.com lucid-backports/restricted Sources
Ign http://packages.medibuntu.org/ lucid/free Translation-en_US                
Hit http://us.archive.ubuntu.com lucid-backports/universe Sources              
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_US            
Hit http://us.archive.ubuntu.com lucid-backports/multiverse Sources            
Get:2 http://packages.medibuntu.org lucid Release [6,854B]                     
Ign http://packages.medibuntu.org lucid Release                                
Hit http://packages.medibuntu.org lucid/free Packages                          
Hit http://packages.medibuntu.org lucid/non-free Packages                      
Fetched 198B in 19s (10B/s)                                                    
W: GPG error: http://packages.medibuntu.org lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1)/dists/lucid/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1)/dists/lucid/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.[/HTML]

---

### Post by RicktheBrick on 2010-11-24
I have the same problem and when I tried to remove the lock I got a message to put the cd disk with Ubuntu 10.10 into the drive.  I updated with update manager so I do not have a disk.  When I try to use update manager in tells me to authenticate and after I put in my password it tells me to authenticate again but this time there is no where to put my password but only a box with the label authenticate on it.  Clicking on it does not work and using the esc key brings on a message that it is waiting for apt-get to exit.

---

