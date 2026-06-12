---
title: "Updating - A TON of &quot;failed to fetch&quot; messages."
date: 2010-04-22
forum: General Help
---

### Post by marley07 on 2010-04-22
Okay. So I've spent hours on these forms looking through similar posts...I'm sorry to have to post one more thread but I have not been able to find a solution. (Ubuntu newbie.)

I get the red triangle telling me that I need to update. I click the check button to find updates. It brings up the pop-up box for a second and then gives me a TON of update error messages. The same thing happens when I try 

sudo apt-get update

Here is what the output is for this command:

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Err [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Err [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Err [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports Release.gpg
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/main Translation-en_US
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/restricted Translation-en_US
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/universe Translation-en_US
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/multiverse Translation-en_US
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed Release.gpg      
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/restricted Translation-en_US
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/main Translation-en_US
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/multiverse Translation-en_US
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/universe Translation-en_US
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg        
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]
Reading package lists... Done                                     
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/Release.gpg)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg](http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_US.bz2)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-proposed/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/karmic-proposed/Release.gpg)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-proposed/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-proposed/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-proposed/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-proposed/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-proposed/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-proposed/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-proposed/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-proposed/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release.gpg](http://dl.google.com/linux/deb/dists/stable/Release.gpg)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/main/i18n/Translation-en_US.bz2](http://dl.google.com/linux/deb/dists/stable/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:8080 (127.0.0.1). - connect (111: Connection refused) [IP: 127.0.0.1 8080]

W: Some index files failed to download, they have been ignored, or old ones used instead.



____________
I've tried switching servers and the same problem happens. I've tried to search for the best server and it gives me an error message. I've looked through various config files and whatnot and have copied what other users have as their config's (I'm assuming a server list it pretty much universal) to no avail....I'm lost. Any help would be appreciated.

---

### Post by marley07 on 2010-04-29
So apparently using my phone with tethering solves the problem. I'm still not sure what's up with it. I've checked to make sure no proxies are set and I've applied it systemwide. Oh well. I'll tether for now. :P

---

