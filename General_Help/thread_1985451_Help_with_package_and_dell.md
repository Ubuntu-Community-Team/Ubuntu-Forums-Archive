---
title: "Help with package and dell"
date: 2012-05-23
forum: General Help
---

### Post by rama1712 on 2012-05-23
I am trying to install osma on to my dell poweredge i am running ubuntu server 10
 
I follow these instructions
(Optional for Upgrade) Create a new file ending in 'sources.list' in the '/etc/apt/sources.list.d' directory. Cut and paste the command below. (If typing by hand, note carefully the spacing.) 
[INDENT]**echo 'deb [http://linux.dell.com/repo/community/deb/latest](http://linux.dell.com/repo/community/deb/latest) /' | sudo tee -a /etc/apt/sources.list.d/linux.dell.com.sources.list**
 
[LEFT][/LEFT]
[/INDENT]I have done that
[LEFT]Ithen did apt-get update as per instructions but i get the following i do do not understand why.
I need to install this software to monitor how hardware[/LEFT]
 
[LEFT]Err [http://linux.dell.com](http://linux.dell.com) |/-a i386 Packages 
404 Not Found
Err [http://linux.dell.com](http://linux.dell.com) |//etc/apt/sources.list.d/linux.dell.com.sources.list i386 Packages
404 Not Found
Fetched 5,673kB in 7s (802kB/s) 
W: Failed to fetch [http://linux.dell.com/repo/community/deb/latest/dists/|/sudo/binary-i386/Packages.gz](http://linux.dell.com/repo/community/deb/latest/dists/|/sudo/binary-i386/Packages.gz) 404 Not Found
W: Failed to fetch [http://linux.dell.com/repo/community/deb/latest/dists/|/tee/binary-i386/Packages.gz](http://linux.dell.com/repo/community/deb/latest/dists/|/tee/binary-i386/Packages.gz) 404 Not Found
W: Failed to fetch [http://linux.dell.com/repo/community/deb/latest/dists/|/-a/binary-i386/Packages.gz](http://linux.dell.com/repo/community/deb/latest/dists/|/-a/binary-i386/Packages.gz) 404 Not Found
W: Failed to fetch [http://linux.dell.com/repo/community/deb/latest/dists/|//etc/apt/sources.list.d/linux.dell.com.sources.list/binary-i386/Packages.gz](http://linux.dell.com/repo/community/deb/latest/dists/|//etc/apt/sources.list.d/linux.dell.com.sources.list/binary-i386/Packages.gz) 404 Not Found
E: Some index files failed to download, they have been ignored, or old ones used instead.[/LEFT]
 
[LEFT]Can any one help please i am a newbie at this so i going back to play with windows [/LEFT]
 
[LEFT]Thanks in Advance
Stu[/LEFT]

---

### Post by zvacet on 2012-05-23
Did you add key?

```
gpg --keyserver pool.sks-keyservers.net --recv-key 1285491434D8786F

gpg -a --export 1285491434D8786F | sudo apt-key add -
```

If you didn´t do it by running one command at the time.After that 

```
sudo apt-get update
```

---

