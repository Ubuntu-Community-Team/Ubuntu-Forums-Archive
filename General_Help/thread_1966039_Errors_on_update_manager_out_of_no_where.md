---
title: "Errors on update manager out of no where"
date: 2012-04-26
forum: General Help
---

### Post by Sissy8788 on 2012-04-26
Hello all.

I tried to update from terminal

```
sudo apt-get update
      sudo apt-get upgrade
```

and I get these errors

```
W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/Release.gpg  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/apps/binary-amd64/Packages  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/games/binary-amd64/Packages  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/apps/binary-i386/Packages  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/games/binary-i386/Packages  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/apps/i18n/Translation-en_US  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/apps/i18n/Translation-en  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/games/i18n/Translation-en_US  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/games/i18n/Translation-en  Unable to connect to archive.getdeb.net:http:

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Last night it was just working fine but not today.
And now Update manager won't work.
Any help would be a appreciated.Thank you in advance for your time :)

---

### Post by jadtech on 2012-04-26
in update manager change the server

---

### Post by Sissy8788 on 2012-04-26
> **jadtech said:**
> in update manager change the server

Thank you for your time and your reply but this didn't help,

I get the same errors.

---

### Post by plucky on 2012-04-26
> W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/games/binary-i386/Packages](http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/games/binary-i386/Packages)  Unable to connect to archive.getdeb.net:http:


Have you thought that the getdeb repository might be down?

It is not an official repository owned by Canonical,so changing the server will not help.

Try disabling all the getdeb entries in Software Sources and see if the errors go away,then re-enabling them whenever the owners of the repository fix whatever problems the repository has.

It won't even load the getdeb.net home page. [http://www.getdeb.net/](http://www.getdeb.net/)

Good luck

---

### Post by tomsfeenie on 2012-04-26
Same error here, perhaps the server is down... Will try in a few hours, or perhaps tomorrow...:-\"

---

### Post by techsupport on 2012-04-26
> **tomsfeenie said:**
> Same error here, perhaps the server is down... Will try in a few hours, or perhaps tomorrow...:-\"

12.04 just got released today guys.  Getdeb PPA may not be ready for prime time yet. Contact them directly to find out when that might be.

---

### Post by mcovey on 2012-04-27
repo is just down right now. Google's repos are also timing out during update, causing apt-get update to take forever...

I'm sure the issues will be resolved in time. Today's 12.04 release means that Ubuntu servers are getting hammered during upgrades, and as a side effect everyone simultaneously updating apt caches is probably DDOSing the servers.

I'm Using aptitude right now to do updates, it seems to fail gracefully when servers time out and just keep going after ignoring the ones that are down.

---

### Post by Sissy8788 on 2012-04-27
> **plucky said:**
> Have you thought that the getdeb repository might be down?

It is not an official repository owned by Canonical,so changing the server will not help.

Try disabling all the getdeb entries in Software Sources and see if the errors go away,then re-enabling them whenever the owners of the repository fix whatever problems the repository has.

It won't even load the getdeb.net home page. [http://www.getdeb.net/](http://www.getdeb.net/)

Good luck

Thank you for your reply, I forgot to mention that I'm a newbie to Linux. :P I will try again now.

Yep, it worked!! Thank you very much :)

---

### Post by Sissy8788 on 2012-04-27
Thank you all for your replies.It's probably what you said cause I didn't touch a thing on my laptop.And I avoid messing with everything cause I know i will break it. :P

---

