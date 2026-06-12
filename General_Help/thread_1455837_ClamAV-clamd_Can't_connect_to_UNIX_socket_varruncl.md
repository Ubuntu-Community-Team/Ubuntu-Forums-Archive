---
title: "ClamAV-clamd: Can't connect to UNIX socket /var/run/clamav/clamd.ctl"
date: 2010-04-16
forum: General Help
---

### Post by robbrandt on 2010-04-16
This started happening sometime yesterday afternoon on a server that's been trouble free for years.

Linux Ubuntu 8.0.4
Amavis 1:2.5.3-1ubuntu3
clamav-base 0.95.3+dfsg-1ubuntu0.09.04~hardy2.2
clamav-daemon 0.92.1~dfsg2-1.1ubuntu0.5
clamav-freshclam 0.92.1~dfsg2-1.1ubuntu0.5
libclamav3 0.92.1~dfsg2-1.1ubuntu0.5

My Ubuntu update is scheduled to run every month on the 5th, so this was roughly 10 days after that.  So it seems to me it's not update related.  The only thing I've done on the server lately is update a spamassassin rule which required an amavis restart. That was done earlier in the week.

I've already reviewed issues at
[http://www200.pair.com/mecham/spam/clamav-amavisd-new.html](http://www200.pair.com/mecham/spam/clamav-amavisd-new.html)
and all the conditions are correct for the more recent How to.

I can also confirm that, in fact, /var/run/clamav/clamd.ctl does not exist.

Ideas?

---

### Post by merlinv12 on 2010-04-16
The support for the version you are using has ended, and is the reason why you are getting this problem. For the time being, disable virus scanning so that your emails can atleast get through.

I have the same issue.

Will let you know when I figure it out.

---

### Post by merlinv12 on 2010-04-16
Version 0.94 support has ended. Only version .95 and higher are supported so updates are required.

Here is how I solved the issue, or at least until version .95 is out of date.

sudo apt-get install clamav clamav-daemon clamav-base amavisd-new clamav-freshclam clamav-docs

Now my mail is coming through again after being scanned. I will know for sure if it works when it does the next daily update.

---

### Post by 2byakin on 2010-04-16
I have been looking at this all day.  finally found where the version I have has expired.  I am VERY new to this.  I am using the following, as far as I can tell.  I had an employee that took care of this but is no longer working for me.  Like I said, VERY knew at unix and clamav....
 
I was able to get the spam from checking any longer and get my email going but we get so much spam, I need to get this fixed.  
 
Ubuntu 7.10
Clamav-daemon .92.1
 
I tried apt-get install clamav and got the following error:
 
[EMAIL="root@mx2:/etc"]root@mx2:/etc[/EMAIL]# apt-get install clamav
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  clamav-docs
The following NEW packages will be installed:
  clamav
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 895kB of archives.
After unpacking 1368kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  clamav
Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe clamav 0.92.1~dfsg2-1.1~gutsy3.1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe clamav 0.92.1~dfsg2-1.1~gutsy3.1
  404 Not Found [IP: 91.189.88.37 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/c/clamav/clamav_0.92.1~dfsg2-1.1~gutsy3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/clamav/clamav_0.92.1~dfsg2-1.1~gutsy3.1_i386.deb)  404 Not Found [IP: 91.189.88.37 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

 
I don't have any idea how to update this.  Please advise ASAP.  My butt is in a sling here.
 
Thanks in advance

---

### Post by dcstar on 2010-04-17
> **2byakin said:**
> 
.......
I don't have any idea how to update this.  Please advise ASAP.  My butt is in a sling here.
 
Thanks in advance

Change the repository.

---

### Post by 2byakin on 2010-04-17
Below is my sources.list file.  How would I change it to update the repository.  I am thinking this is what you are talking about from my other research.  Would I have to update to later version of Ubuntu or what?  I just don't know much about unix and how it works.  Any advise would be greatly appreciated.  I am trying to update Clamav so not understanding this process.
 
[EMAIL="root@mx2:/etc/apt"]root@mx2:/etc/apt[/EMAIL]# vi sources.list
#
# deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

---

### Post by btaylor101 on 2010-04-24
I ran the following : 
> sudo apt-get install clamav clamav-daemon clamav-base amavisd-new clamav-freshclam clamav-docs 

and I am still getting the following error. 
>  CLAMAV: couldn't connect to: /var/run/clamav/clamd.ctl: No such file or directory 

any idea on where I could look at next?

---

### Post by btaylor101 on 2010-04-24
I got this to work by restarting the clamav-daemon.

---

