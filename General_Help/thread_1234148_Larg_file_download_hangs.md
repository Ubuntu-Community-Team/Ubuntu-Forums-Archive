---
title: "Larg file download hangs"
date: 2009-08-07
forum: General Help
---

### Post by zaphod777 on 2009-08-07
Whenever I try and download a large file somthing like an iso filw that is 700 MB + it starts downloading really fast and then it just hangs. If I hit pause and resume it will start again for a short time. 

I have resorted to downloading ISO files with torrents. 

Any ideas? I mostly use firefox.

I am using 9.04 x64.

---

### Post by michy99 on 2009-08-07
Try using a download manager like Downloader for X.```
sudo apt-get install d4x
```

---

### Post by zaphod777 on 2009-08-07
okay I Will check that out tonight.

---

### Post by burmanabhay88 on 2009-08-07
How much does it stop at???? Is there some fixed size???, like 40 MB or something like that???

---

### Post by zaphod777 on 2009-08-07
not pertuclurley it will go fro maybe a min or two then stop. 

Firfox still shows the speed at a fixed siz say 1.3 MB/S (I have a 20 MB connection).

---

### Post by fennec_fox on 2009-08-07
Do other programs freeze or hang up? Is it just firefox that stops downloading? Do system updates, apt-get or wget freeze on large downloads? You might want to try to download something large with wget and see if that freezes to. That will help narrow the problem.

EDIT: try something like 
```
wget -c -o [http://ubuntu.media.mit.edu/ubuntu-releases/9.04/ubuntu-9.04-desktop-i386.iso](http://ubuntu.media.mit.edu/ubuntu-releases/9.04/ubuntu-9.04-desktop-i386.iso)
```

-c is supposed to continue partial downloads but, you can try it without to see if it crashes if the above doesn't
```
wget -c [http://ubuntu.media.mit.edu/ubuntu-releases/9.04/ubuntu-9.04-desktop-i386.iso](http://ubuntu.media.mit.edu/ubuntu-releases/9.04/ubuntu-9.04-desktop-i386.iso)
```[]("http://ubuntu.media.mit.edu/ubuntu-releases/9.04/ubuntu-9.04-desktop-i386.iso")

---

### Post by burmanabhay88 on 2009-08-07
> **zaphod777 said:**
> not pertuclurley it will go fro maybe a min or two then stop. 

Firfox still shows the speed at a fixed siz say 1.3 MB/S (I have a 20 MB connection).

Okay.. Now it's a hunch, but it just might work.
Goto Edit > Preferences
Advanced > Network

Increase the cache to around 800MB... and restart firefox.
Try downloading the ISO again.
Tell me if this works.

---

### Post by zaphod777 on 2009-08-07
That sounds very promissing actually. I bet that is it. I will check it out and let you guys know.

Thanks!

---

### Post by dlmarti on 2009-08-07
> **zaphod777 said:**
> That sounds very promissing actually. I bet that is it. I will check it out and let you guys know.

Thanks!

I doubt it is.
My guess is your network provider, or the site your downloading from.

---

### Post by fcuk112 on 2009-08-07
downloadthemall! is also a popular download manager for firefox (addon).

---

