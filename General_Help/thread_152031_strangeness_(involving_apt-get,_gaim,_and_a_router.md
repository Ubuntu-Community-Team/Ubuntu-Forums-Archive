---
title: "strangeness (involving apt-get, gaim, and a router)"
date: 2006-03-29
forum: General Help
---

### Post by ImplicitProcrastination on 2006-03-29
I just switched from Gnome to KDE within the last couple of months and love it dearly.

But listen to how odd this is: on gnome we couldn't run RoadRunner through a router and have it work on my computer... but KDE apparantely changed all that, and now everybody in my house can be on the internet at the same time... GREAT!

But now I can't connect to AOL Instant Messenger or MSN through gAIM (although Yahoo! works fine), and furthermore I get this bundle of repository strangeness when trying to apt-get update or install something (starting god knows where, but you get the picture):

```

Err http://security.ubuntu.com breezy-security Release.gpg
  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Ign http://security.ubuntu.com breezy-security Release
Ign http://security.ubuntu.com breezy-security/main Packages
Ign http://security.ubuntu.com breezy-security/restricted Packages
Ign http://security.ubuntu.com breezy-security/main Sources
Ign http://security.ubuntu.com breezy-security/restricted Sources
Ign http://security.ubuntu.com breezy-security/universe Packages
Ign http://security.ubuntu.com breezy-security/universe Sources
Err http://security.ubuntu.com breezy-security/main Packages
  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err http://security.ubuntu.com breezy-security/restricted Packages
  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err http://security.ubuntu.com breezy-security/main Sources
  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err http://security.ubuntu.com breezy-security/restricted Sources
  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err http://security.ubuntu.com breezy-security/universe Packages
  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err http://security.ubuntu.com breezy-security/universe Sources
  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err http://archive.ubuntu.com breezy Release.gpg
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err http://archive.ubuntu.com breezy-updates Release.gpg
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err http://archive.ubuntu.com breezy-backports Release.gpg
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Ign http://archive.ubuntu.com breezy Release
Ign http://archive.ubuntu.com breezy-updates Release
Ign http://archive.ubuntu.com breezy-backports Release
Ign http://archive.ubuntu.com breezy/main Packages
Ign http://archive.ubuntu.com breezy/restricted Packages
Ign http://archive.ubuntu.com breezy/main Sources
Ign http://archive.ubuntu.com breezy/restricted Sources
Ign http://archive.ubuntu.com breezy/universe Packages
Ign http://archive.ubuntu.com breezy/universe Sources
Ign http://archive.ubuntu.com breezy/multiverse Packages
Ign http://archive.ubuntu.com breezy/multiverse Sources
Ign http://archive.ubuntu.com breezy-updates/main Packages
Ign http://archive.ubuntu.com breezy-updates/restricted Packages
Ign http://archive.ubuntu.com breezy-updates/main Sources
Ign http://archive.ubuntu.com breezy-updates/restricted Sources
Ign http://archive.ubuntu.com breezy-backports/main Packages
Ign http://archive.ubuntu.com breezy-backports/restricted Packages
Ign http://archive.ubuntu.com breezy-backports/universe Packages
Ign http://archive.ubuntu.com breezy-backports/multiverse Packages
Err http://archive.ubuntu.com breezy/main Packages
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err http://archive.ubuntu.com breezy/restricted Packages
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err http://archive.ubuntu.com breezy/main Sources
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err http://archive.ubuntu.com breezy/restricted Sources
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err http://archive.ubuntu.com breezy/universe Packages
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err http://archive.ubuntu.com breezy/universe Sources
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err http://archive.ubuntu.com breezy/multiverse Packages
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err http://archive.ubuntu.com breezy/multiverse Sources
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err http://archive.ubuntu.com breezy-updates/main Packages
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err http://archive.ubuntu.com breezy-updates/restricted Packages
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err http://archive.ubuntu.com breezy-updates/main Sources
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err http://archive.ubuntu.com breezy-updates/restricted Sources
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err http://archive.ubuntu.com breezy-backports/main Packages
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err http://archive.ubuntu.com breezy-backports/restricted Packages
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err http://archive.ubuntu.com breezy-backports/universe Packages
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err http://archive.ubuntu.com breezy-backports/multiverse Packages
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
rockstar@rockstar:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rockstar@rockstar:~$ 
```

Anyway, this occurred for my original set of sources (compliments of the previous version of Automatix) as well as the set I pasted in an attempt to install zenity and try to install the newer version. I've found that I can't run an apt-get update or anything... nor can I send email using KMail or Thunderbird (although that may be unrelated or related to Google). Everything else works fine... I'm starting to think god just doesn't want me computer to run optimally when I'm away from college          ](*,) 


Much love...

---

### Post by reductionist on 2006-03-29
Oh yes, this old thing. It's most prob to do with DHCP setting your DNS to be that of your router/gateway. Have a look at your etc/resolv.conf. If it has one line which says (something like) "nameserver: 192.168.0.1" then it's prob wrong. 
I don't know how to fix this permanently, which is why I'm here, but you can temporarily fix it by entering your ISP's DNS addresses into /etc/resolv.conf (need SU rights). That fixed it for me to at least get apt-get and its relatives working.

But we do need a permanent fix for this. Anyone?

---

### Post by reductionist on 2006-03-29
Well I've fixed the DNS strangeness: -

type this:
              kdesu kate  /etc/dhcp3/dhclient.conf
uncomment the line #prepend domain-name-servers 127.0.0.1
and change the 127.0.0.1 to your ISPs DNS - should be 2, separate them with a comma.
Then re-boot.
Hope it works for you.

---

### Post by ImplicitProcrastination on 2006-03-29
How do I figure out my ISPs DNS?

In gnome I was pretty sure the reason I couldn't get my router to work had to do with DNS settings, and I damn near figured it out except I didn't know what to enter for the settings...

and RoadRunner is absolutely no help whatsoever.

---

### Post by reductionist on 2006-03-30
This is decidedly tricky - I know nothing of road-runner being as I'm in the UK - but  I have heard that some users of that ISP use 4.2.2.1 thru 4.2.2.5 as their DNS and it works for them. It won't hurt to give those a try...

regards

---

