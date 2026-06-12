---
title: "apt pinning problems"
date: 2010-01-14
forum: General Help
---

### Post by berglin on 2010-01-14
I'm having problems configuring pinning for APT, when I use apt-cache policy to review the policies I see that the "release" line is missing.
 
I have this working on one machine and I have copied the preferences file so that they are exactly the same.
It looks like this:
 
Package: *
Pin: release n=common
Pin-Priority: 300
 
Working machine:
apt-cache policy
Package files:
 100 /var/lib/dpkg/status
     release a=now
 300 [http://192.168.1.160](http://192.168.1.160) common/all Packages
     release o=Mine,a=common,n=common,l=My Automatic updater,c=all
     origin 192.168.1.160
 
Faulty Machine:
apt-cache policy
"Package"-filer:
 100 /var/lib/dpkg/status
     release a=now
 500 [http://192.168.1.160](http://192.168.1.160) common/all Packages
     origin 192.168.1.160
 
Any ideas?
 
Thanks.

---

### Post by berglin on 2010-01-14
Update:

I've replaced the entire /etc/apt directory on the faulty machine with the one from the working one but it still presents the wrong pinning information.

Obviously, the problem is elsewhere.

Any pointers?

// b

---

### Post by berglin on 2010-01-14
Solved it.

Apparantly the repositories have to be signed in order for pinning to work.
After adding Release.gpg files to the repo pinning started working.

Maybe apt could've been configured with AllowUnauthenticated and it would've had the same effect...

---

