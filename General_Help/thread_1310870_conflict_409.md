---
title: "conflict 409?"
date: 2009-11-02
forum: General Help
---

### Post by bryncoles on 2009-11-02
Hi all. I just upgraded to Karmic (64 bit) and am enjoying the few problems it is giving me so far! 

Todays issue: if I run the command ```
sudo apt-get update
``` in the terminal, I get a lot of failures to hit. something about > W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-amd64/Packages.gz)  409  Conflict [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz)  409  Conflict [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-amd64/Packages.gz)  409  Conflict [IP: 91.189.88.30 80]

(Thats not the full message, just a flavour. But all the errors continue in that theme).

Whats not right here? how do I solve this issue?

---

### Post by bryncoles on 2009-11-03
Ha, as usual, I had done stupid configuration things. I'm still having issues with the medibuntu repo's, but I've found out and resolved the error 409 - I'd set my interweb up wrong!

---

### Post by R Ashton on 2010-03-09
Could you enlighten us on what you did to fix this? I'm getting similar 409 errors when I try to install packages. 

Edit: Don't worry I've managed to fix things :) Turns out I was being a dummy

---

