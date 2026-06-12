---
title: "Update or software source problem"
date: 2010-05-27
forum: General Help
---

### Post by ALF102 on 2010-05-27
I tried to update many times but I always faced with this message:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg)  Could not connect to archive.getdeb.net:80 (81.92.203.249). - connect (110: Connection timed out)
Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/games/i18n/Translation-en_US.bz2](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/games/i18n/Translation-en_US.bz2)  Unable to connect to archive.getdeb.net:http:
Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/games/binary-i386/Packages.gz](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/games/binary-i386/Packages.gz)  Unable to connect to archive.getdeb.net:http:
Some index files failed to download, they have been ignored, or old ones used instead.


Well, I do know what it means and why it happens but I can't shake the feeling that there's a hidden problem in here. Should I just ignore this and wait like another 2-3 days and it will be fix? As far as I can try, I tried to change the software source to another server and the same problem occurs.  the same thing also happen when I try to reload my Synaptic Package  manager

---

### Post by jerrrys on 2010-05-27
check it out, may be the fix

[http://www.ubuntugeek.com/getdebplaydeb-ubuntu-10-04-lucid-lynx-repository-available-now.html](http://www.ubuntugeek.com/getdebplaydeb-ubuntu-10-04-lucid-lynx-repository-available-now.html)

---

### Post by ALF102 on 2010-05-27
I don;t this has anything to do with GetDeb, I will face this problem whenever I try to update, reload my syanptic package manager or reload the software source. As though it only occurs whenever it tries to do anything that has to do with trying to fetch anything from the servers

Does this command line is the cause? 

sudo apt-get remove evolution evolution-common evolution-couchdb evolution-exchange evolution-indicator evolution-plugins evolution-webcal

---

### Post by 3rdalbum on 2010-05-27
> **ALF102 said:**
> I don;t this has anything to do with GetDeb, I will face this problem whenever I try to update, reload my syanptic package manager or reload the software source. As though it only occurs whenever it tries to do anything that has to do with trying to fetch anything from the servers

Does this command line is the cause? 



The error message says that it can't fetch the Getdeb repository. So it's probably that repository that is down.

---

### Post by jerrrys on 2010-05-27
funny you should ask.  i just did the above sudo command about an hour ago, looked good to me, left the desktop in tact...

the reason i went with getdeb was the addresses on the last two dead links in your post...

---

### Post by ALF102 on 2010-05-27
Yeah right, I somehow forgot to take that factor into consideration. It seems the repo is down, so I should wait for it to get back up. Thanks anyway

---

