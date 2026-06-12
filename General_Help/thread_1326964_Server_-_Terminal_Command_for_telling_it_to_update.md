---
title: "Server - Terminal Command for telling it to update from the Main Server (edit 9.04)"
date: 2009-11-14
forum: General Help
---

### Post by daaussie on 2009-11-14
I need the Server Terminal Command for telling it to update from the Main Server?? no GUI

I know how to do this from desktop easy, but with server there is no interface, just terminal.

I tried, sudo apt-get update main server, but it doesnt work.

Reason why I need to switch is that there is a problem with  updating from my regions server.

Thanks

---

### Post by centralmtk on 2009-11-15
I am having this same problem.

When running aptitude update. i get messages like this:

Err [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US                   
  Unable to connect to archive.canonical.com http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                          
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US               
  Unable to connect to security.ubuntu.com http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
  Unable to connect to security.ubuntu.com http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
  Unable to connect to security.ubuntu.com http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
  Unable to connect to security.ubuntu.com http:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg     
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.30), connection timed out [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports Release.gpg
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/main Translation-en_US
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/restricted Translation-en_US
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/universe Translation-en_US
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/multiverse Translation-en_US
  Unable to connect to us.archive.ubuntu.com http: [IP: 91.189.88.30 80]
Reading package lists... Done






Anyone know how to help ?

---

### Post by daaussie on 2009-11-15
That's interesting. I am in Australia, and I get the same issue with the desktop, but the list ends with AU...

I know how to fix if your in a desktop version, you just go to the update, click settings (down bottom), and re-direct the updates to come from the "Main Server".

But when it comes to the server, there is no Graphical interface, so I don't know how to reset it....

---

