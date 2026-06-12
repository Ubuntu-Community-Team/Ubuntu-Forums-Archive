---
title: "Need help with local repository"
date: 2011-04-11
forum: General Help
---

### Post by Tolein on 2011-04-11
I am attempting to make a local repository server in ubuntu server 10.10 for a final project in a linux server class. I got pretty far but I hit a wall that I can't seem to figure out that I am hoping I can get some help with here. I installed apache2 and created the /var/www/repo directory. I then changed directories to /var/cache/apt/archives and did a apt-get clean. This cleared the cache in the archive folder. I then enter "apt-get install -d gimp". After this I copy all of the files to the /var/www/repo/archives folder. I changed directories to /var/www/repo and ran the command "sudo dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz". This creates the Packages.gz file in the repo directory. From this point I went to a different machine on the same network and commented out everything in the sources.list file and added "deb http://10.80.1.150/repo". After this I entered "apt-get update" and everything updates fine. After this when I type in apt-get install gimp on the host I get the message package cannot be found. What frustrates me is when I edit the sources.list file on the server to the same thing I can install it fine. I also can type in the URL of the repository on both machines and get to it via the web browser. Any help would be very appreciated.

---

