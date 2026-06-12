---
title: "Downloading repositories to hard drive"
date: 2009-11-26
forum: General Help
---

### Post by knit.manish on 2009-11-26
hiii friends,
  i have a question regarding the repositories. is it possible to download our hard disk and use them without connecting to net. i.e whenever i install ubuntu then each time i have to internet  to install softwares. Is there any way to make a backup in hard drive and then add it to our source list and then install softwares. 
Please help me
regards

---

### Post by RealG187 on 2009-11-26
[http://bestwikiever.wikidot.com/ubuntu:local-repository](http://bestwikiever.wikidot.com/ubuntu:local-repository)

I do this all the time. You can transfer the DEB packages to a USB drive and use them on a computer without an internet connection or just to save bandwidth.

---

### Post by Anonymousable on 2009-11-26
Sounds like you're using the live CD. You'll have to use a Live USB drive or install ubuntu on your system first.

---

### Post by blueridgedog on 2009-11-26
Here is a method:

[http://popey.com/blog/2006/10/24/Creating_an_Ubuntu_repository_mirror_with_apt-mirror/](http://popey.com/blog/2006/10/24/Creating_an_Ubuntu_repository_mirror_with_apt-mirror/)

---

### Post by knit.manish on 2009-11-26
[http://bestwikiever.wikidot.com/ubuntu:local-repository](http://bestwikiever.wikidot.com/ubuntu:local-repository) 
hey REAL though the link provided by u is useful yet there are some problems  on the terminal everything goes fine with no error except that i have to make it as follow
 dpkg-scanpackages debs /dev/null | gzip > /home/phu/debs/dists/karmic/local/binary-i386/Packages.gz 
it is beacuse i m using karmic after the terminal process i added it to the software sources then reloaded it.
Now whenever i m installing any application from that i getting the message 


could not find the marked packages 
can u tell me what is worng now

---

### Post by knit.manish on 2009-11-26
> **RealG187 said:**
> [http://bestwikiever.wikidot.com/ubuntu:local-repository](http://bestwikiever.wikidot.com/ubuntu:local-repository)

I do this all the time. You can transfer the DEB packages to a USB drive and use them on a computer without an internet connection or just to save bandwidth.

[http://bestwikiever.wikidot.com/ubuntu:local-repository](http://bestwikiever.wikidot.com/ubuntu:local-repository) 
hey REAL though the link provided by u is useful yet there are some problems  on the terminal everything goes fine with no error except that i have to make it as follow
 dpkg-scanpackages debs /dev/null | gzip > /home/phu/debs/dists/karmic/local/binary-i386/Packages.gz 
it is beacuse i m using karmic after the terminal process i added it to the software sources then reloaded it.
Now whenever i m installing any application from that i getting the message 


could not find the marked packages 
can u tell me what is worng now

---

### Post by knit.manish on 2009-11-26
> **blueridgedog said:**
> Here is a method:

[http://popey.com/blog/2006/10/24/Creating_an_Ubuntu_repository_mirror_with_apt-mirror/](http://popey.com/blog/2006/10/24/Creating_an_Ubuntu_repository_mirror_with_apt-mirror/)



thanx frnd ur link was of great assistance to me i m trying to implement it

---

