---
title: "Getting Error message while trying to update"
date: 2010-04-16
forum: General Help
---

### Post by mravikiran on 2010-04-16
Hi this is Ravikiran ...i'm using Ubuntu 9.10
When i tried to update i am getting following error message:-

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_IN.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_IN.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_IN.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_IN.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/karmic/Release.gpg](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/karmic/Release.gpg)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/karmic/main/i18n/Translation-en_IN.bz2](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/karmic/main/i18n/Translation-en_IN.bz2)  Could not resolve 'ppa.launchpad.net'

W: Some index files failed to download, they have been ignored, or old ones used instead.

Not able to solve my problem.So please help me regarding above problem....

---

### Post by warfacegod on 2010-04-16
I would try using a different sources mirror. Go to: System> Software Sources> Ubuntu Software tab> Download From: choose Other> click Select Best Server.

When it's done, click Choose Server and then click Reload. Now try updating again.

---

### Post by mravikiran on 2010-04-16
After doing the above steps as told by you i'm getting following message:-

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic/main/binary-i386/Packages.gz](http://ubuntuarchive.hnsdc.com/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic/restricted/binary-i386/Packages.gz](http://ubuntuarchive.hnsdc.com/dists/karmic/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic/main/source/Sources.gz](http://ubuntuarchive.hnsdc.com/dists/karmic/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic/restricted/source/Sources.gz](http://ubuntuarchive.hnsdc.com/dists/karmic/restricted/source/Sources.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic/universe/binary-i386/Packages.gz](http://ubuntuarchive.hnsdc.com/dists/karmic/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic/universe/source/Sources.gz](http://ubuntuarchive.hnsdc.com/dists/karmic/universe/source/Sources.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic/multiverse/binary-i386/Packages.gz](http://ubuntuarchive.hnsdc.com/dists/karmic/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic/multiverse/source/Sources.gz](http://ubuntuarchive.hnsdc.com/dists/karmic/multiverse/source/Sources.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic-updates/main/binary-i386/Packages.gz](http://ubuntuarchive.hnsdc.com/dists/karmic-updates/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic-updates/restricted/binary-i386/Packages.gz](http://ubuntuarchive.hnsdc.com/dists/karmic-updates/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic-updates/main/source/Sources.gz](http://ubuntuarchive.hnsdc.com/dists/karmic-updates/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic-updates/restricted/source/Sources.gz](http://ubuntuarchive.hnsdc.com/dists/karmic-updates/restricted/source/Sources.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic-updates/universe/binary-i386/Packages.gz](http://ubuntuarchive.hnsdc.com/dists/karmic-updates/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic-updates/universe/source/Sources.gz](http://ubuntuarchive.hnsdc.com/dists/karmic-updates/universe/source/Sources.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic-updates/multiverse/binary-i386/Packages.gz](http://ubuntuarchive.hnsdc.com/dists/karmic-updates/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic-updates/multiverse/source/Sources.gz](http://ubuntuarchive.hnsdc.com/dists/karmic-updates/multiverse/source/Sources.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic-backports/main/binary-i386/Packages.gz](http://ubuntuarchive.hnsdc.com/dists/karmic-backports/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic-backports/restricted/binary-i386/Packages.gz](http://ubuntuarchive.hnsdc.com/dists/karmic-backports/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic-backports/universe/binary-i386/Packages.gz](http://ubuntuarchive.hnsdc.com/dists/karmic-backports/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic-backports/multiverse/binary-i386/Packages.gz](http://ubuntuarchive.hnsdc.com/dists/karmic-backports/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic-backports/main/source/Sources.gz](http://ubuntuarchive.hnsdc.com/dists/karmic-backports/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic-backports/restricted/source/Sources.gz](http://ubuntuarchive.hnsdc.com/dists/karmic-backports/restricted/source/Sources.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic-backports/universe/source/Sources.gz](http://ubuntuarchive.hnsdc.com/dists/karmic-backports/universe/source/Sources.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic-backports/multiverse/source/Sources.gz](http://ubuntuarchive.hnsdc.com/dists/karmic-backports/multiverse/source/Sources.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic-security/main/binary-i386/Packages.gz](http://ubuntuarchive.hnsdc.com/dists/karmic-security/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic-security/restricted/binary-i386/Packages.gz](http://ubuntuarchive.hnsdc.com/dists/karmic-security/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic-security/main/source/Sources.gz](http://ubuntuarchive.hnsdc.com/dists/karmic-security/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic-security/restricted/source/Sources.gz](http://ubuntuarchive.hnsdc.com/dists/karmic-security/restricted/source/Sources.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic-security/universe/binary-i386/Packages.gz](http://ubuntuarchive.hnsdc.com/dists/karmic-security/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic-security/universe/source/Sources.gz](http://ubuntuarchive.hnsdc.com/dists/karmic-security/universe/source/Sources.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic-security/multiverse/binary-i386/Packages.gz](http://ubuntuarchive.hnsdc.com/dists/karmic-security/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ubuntuarchive.hnsdc.com/dists/karmic-security/multiverse/source/Sources.gz](http://ubuntuarchive.hnsdc.com/dists/karmic-security/multiverse/source/Sources.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by 2hot6ft2 on 2010-04-16
Try doing what warfacegod said again and choose another server. For some reason those 2 appear to be down. Even the PPA in the first post seems to be down.
Maybe try setting it to the Main Server.
> **warfacegod said:**
> I would try using a different sources mirror. Go to: System> Software Sources> Ubuntu Software tab> Download From: choose Other> click Select Best Server.

When it's done, click Choose Server and then click Reload. Now try updating again.

EDIT: The server under India when you select Choose server then Other named
> ftp.iitm.ac.in
Appears to be working. Give that one a try. It shows it was last updated
04/16/2010
11:09:00 PM

Also this server in India appears to be up and working so pick one of them
> mirror.cse.iitk.ac.in

---

### Post by acompay on 2010-04-16
> **mravikiran said:**
> Hi this is Ravikiran ...i'm using Ubuntu 9.10
When i tried to update i am getting following error message:-

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_IN.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_IN.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_IN.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_IN.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/karmic/Release.gpg](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/karmic/Release.gpg)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/karmic/main/i18n/Translation-en_IN.bz2](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/karmic/main/i18n/Translation-en_IN.bz2)  Could not resolve 'ppa.launchpad.net'

W: Some index files failed to download, they have been ignored, or old ones used instead.

Not able to solve my problem.So please help me regarding above problem....


Hello There!
I am having the same problem when I try to reload repositories using Synaptic or installing free software on Ubuntu Software Centre. What can we do to fix this problem?

---

### Post by 2hot6ft2 on 2010-04-16
> **acompay said:**
> Hello There!
I am having the same problem when I try to reload repositories using Synaptic or installing free software on Ubuntu Software Centre. What can we do to fix this problem?
Are you in India too?
If you are then see post # 4
If you are NOT in India see post # 2

---

### Post by acompay on 2010-04-16
Hello There!
I am also having problems trying to reload repositories with Synaptic but look at the errors am having all the time:
                                 W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not resolve 'username' 
  
 W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_CA.bz2)  Could not resolve 'username' 
  
 W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_CA.bz2)  Could not resolve 'username' 
  
 W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_CA.bz2)  Could not resolve 'username' 
  
 W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_CA.bz2)  Could not resolve 'username' 
  
 W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Could not resolve 'username' 
  
 W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_CA.bz2)  Could not resolve 'username' 
  
 W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_CA.bz2)  Could not resolve 'username' 
  
 W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_CA.bz2)  Could not resolve 'username' 
  
 W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_CA.bz2)  Could not resolve 'username' 
  
 W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg](http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg)  Could not resolve 'username' 
  
 W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_CA.bz2](http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_CA.bz2)  Could not resolve 'username' 
  
 W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  Could not resolve 'username' 
  
 W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_CA.bz2)  Could not resolve 'username' 
  
 W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_CA.bz2)  Could not resolve 'username' 
  
 W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_CA.bz2)  Could not resolve 'username' 
  
 W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_CA.bz2)  Could not resolve 'username' 
  
 W: Some index files failed to download, they have been ignored, or old ones used instead.
 All the errors "could not resolve 'username'
What can I do to fix this problem?
Thanks!

---

### Post by warfacegod on 2010-04-16
acompay, are those errors for software that you have installed that don't come from the "official" sources.

As an aside, I'm wondering if all of this is because the servers are overloaded from all the Lucid updates that have been released recently. I got around 360 updates yesterday and it had been only ten days since I'd last checked for them.

---

### Post by 2hot6ft2 on 2010-04-16
acompay,
I take it you're in Canada.
In software sources click on Choose server
then Canada and select
> ubuntu.hitsol.net
then choose server
it seems to be up and working

---

### Post by 2hot6ft2 on 2010-04-16
> **warfacegod said:**
> 
As an aside, I'm wondering if all of this is because the servers are overloaded from all the Lucid updates that have been released recently. I got around 360 updates yesterday and it had been only ten days since I'd last checked for them.
I can see it's going to get worse before it gets better...
:lolflag:

---

### Post by warfacegod on 2010-04-16
Just wait until the actual release!:P

---

### Post by 2hot6ft2 on 2010-04-16
> **warfacegod said:**
> Just wait until the actual release!:P
I hear that. I'm not going to be one of the first ones because I already know what it will be like. I wont even do updates for the week of its release.

I'll just sit back and have some :popcorn:

---

### Post by acompay on 2010-04-17
> **warfacegod said:**
> acompay, are those errors for software that you have installed that don't come from the "official" sources.
 
As an aside, I'm wondering if all of this is because the servers are overloaded from all the Lucid updates that have been released recently. I got around 360 updates yesterday and it had been only ten days since I'd last checked for them.
 
 
 
 
Thank you for your reply. I get these errors when I try to install new software. I want to install Joomla and Apache2, MySQL-server, MySQL-client and php5 are required. I found these software, marked them and later pressed on "Apply;" the process started and suddenly stopped and gave these errors. The common fact is "it can't resolve for username." What does that mean?
 
Regards,

---

### Post by acompay on 2010-04-17
> **2hot6ft2 said:**
> acompay,
I take it you're in Canada.
In software sources click on Choose server
then Canada and select
 
then choose server
it seems to be up and working
 
Thanks! I did as you suggested but I did not find that mirror in the list. I then tried one by one all the mirrors given and no one worked.
Regards,

---

### Post by geekwanabe on 2010-04-17
I did get all of those errors, change the mirror to 'best' and tried aptitude instead of apt-get and got rid of all except:

W: Failed to fetch [http://ppa.launchpad.net/syke83/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/syke83/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


Any ideas?

---

### Post by warfacegod on 2010-04-17
> **geekwanabe said:**
> I did get all of those errors, change the mirror to 'best' and tried aptitude instead of apt-get and got rid of all except:

W: Failed to fetch [http://ppa.launchpad.net/syke83/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/syke83/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


Any ideas?

That's a Lucid package. What's there, in that PPA, that you can't get from the Lucid repository? If it's some media player or other bit of minor (as in non-critical) software, I'd just remove it from sources.

---

### Post by geekwanabe on 2010-04-17
"What's there, in that PPA, that you can't get from the Lucid repository?"

Good point!  I googled it and found this thread:  [http://ubuntuforums.org/showthread.php?p=9111812](http://ubuntuforums.org/showthread.php?p=9111812)

which I had viewed and applied manually per the advice in post 2 the other day when trying the system wide equalizer!  I removed it and was able to update without the error!  I never did get the sound on that equalizer to stop crackling.  

Thanks so much, it was right in front of my face!

---

