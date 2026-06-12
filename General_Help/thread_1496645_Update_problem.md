---
title: "Update problem"
date: 2010-05-29
forum: General Help
---

### Post by Dr-a on 2010-05-29
Hi I'm using ubuntu 10.04 when I update I see red notification Icon and this message 

> 

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures were invalid: BADSIG 608BF7B93528AE20 Launchpad Docky Development PPAGPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures were invalid: BADSIG 5A9A06AEF9CB8DB0 Launchpad PPA for Ubuntu Wine TeamGPG error: [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release: The following signatures were invalid: BADSIG A8A515F046D7E7CF GetDeb Archive Automatic Signing Key <archive@getdeb.net>Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://www.geekconnection.org/remastersys/repository/lucid/Packages.gz](http://www.geekconnection.org/remastersys/repository/lucid/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by gdonwallace on 2010-05-29
On the first few it looks as if the key file or "Signature" is either bad, missing or the file that they where in is corrupted.  

The last two are 404 errors meaning that the website cannot be found.  

My first suggestion would be **sudo apt-get update** and you may need to run it a couple times.  Also check your sources under the administration menu and make sure they are still good.

Check this out on how to add repos and to get the keys for the repos that you add.  Should fix any problems that you have [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Dr-a on 2010-05-29
> **gdonwallace said:**
> On the first few it looks as if the key file or "Signature" is either bad, missing or the file that they where in is corrupted.  

The last two are 404 errors meaning that the website cannot be found.  

My first suggestion would be **sudo apt-get update** and you may need to run it a couple times.  Also check your sources under the administration menu and make sure they are still good.

Check this out on how to add repos and to get the keys for the repos that you add.  Should fix any problems that you have [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

still not fixed

---

### Post by Mark_in_Hollywood on 2010-05-29
I'm starting to think there is more than a repository problem. I read:

[http://www.webupd8.org/2010/04/getdeb-ubuntu-1004-lucid-lynx.html](http://www.webupd8.org/2010/04/getdeb-ubuntu-1004-lucid-lynx.html)

where they try a different mirror. That hasn't worked.

My Update Mgr. error message reads:

[COLOR="Red"]Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://packages.medibuntu.org/dists/lucid/Release.gpg](http://packages.medibuntu.org/dists/lucid/Release.gpg)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg)  Could not connect to archive.getdeb.net:80 (81.92.203.249). - connect (110: Connection timed out)
Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/i18n/Translation-en_US.bz2](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/i18n/Translation-en_US.bz2)  Unable to connect to archive.getdeb.net:http:
Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-i386/Packages.gz](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-i386/Packages.gz)  Unable to connect to archive.getdeb.net:http:
Some index files failed to download, they have been ignored, or old ones used instead.[/COLOR]

I have used GetDeb from time to time, so I tried the fix for a different mirror and when I edited my ~/sources.list, I could not find lines about GetDeb (ppa://xxx). I added the suggested lines, updated and continue to receive error messages.

I read elsewhere at Ubuntuforums that [getdeb]("http://ubuntuforums.org/showthread.php?t=1418949") is having some problems. 

[And Down For Everyone Or Just For Me]("http://downforeveryoneorjustme.com") also says [http://getdeb.net](http://getdeb.net) is down.

I'm just going to sit tight on this.

---

### Post by abelundercity on 2010-05-30
After googling "getdeb down" I came across [their blog]("http://blog.getdeb.net/2010/02/web-services-down.html").  Yup, they're down and working on it.

---

### Post by Dr-a on 2010-05-31
> Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

still not solved :confused:

---

### Post by drs305 on 2010-05-31
To solve the CD issue, open Software Sources or Synaptic, go to the Settings, Repositories section and remove the tick next to the CD-ROM option in the lower section of the "Ubuntu Software" tab. If it is unchecked, look at the other tabs to see if a CD is listed therein and remove it.

---

### Post by Dr-a on 2010-05-31
thanks the CD ROM problem is solved now 
but I still have this 
> 
Failed to fetch [http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by drs305 on 2010-05-31
> **Dr-a said:**
> thanks the CD ROM problem is solved now 
but I still have this

I checked the ppa and the *lucid* repositories do not currently exist. Either they have been removed temporarily or you updated the release on your own from a previous release.

In any case, you can open the repository listings in Synaptic as previous and untick this (do-core) repository from the "Other Software" sources tab.

---

### Post by Dr-a on 2010-05-31
thanks problem solved

---

### Post by Mark_in_Hollywood on 2010-05-31
I thought that perhaps there was a GPG error and, reading at:


Automatically Import All Missing Launchpad PPA GPG Keys [Ubuntu .deb]

[http://www.webupd8.org/2010/05/automatically-import-all-missing.html](http://www.webupd8.org/2010/05/automatically-import-all-missing.html)

I d/l'd the script and ran it. The terminal returned for lines ending in OK.

However, I still have a red triangle with an "!" in my panel in it and running "Update" returns:

Failed to fetch [http://packages.medibuntu.org/dists/lucid/Release.gpg](http://packages.medibuntu.org/dists/lucid/Release.gpg)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg)  Could not connect to archive.getdeb.net:80 (81.92.203.249). - connect (110: Connection timed out)
Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/i18n/Translation-en_US.bz2](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/i18n/Translation-en_US.bz2)  Unable to connect to archive.getdeb.net:http:
Failed to fetch [http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-i386/Packages.gz](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-i386/Packages.gz)  Unable to connect to archive.getdeb.net:http:
Some index files failed to download, they have been ignored, or old ones used instead.

---

