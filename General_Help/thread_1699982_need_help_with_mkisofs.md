---
title: "need help with mkisofs"
date: 2011-03-04
forum: General Help
---

### Post by senca on 2011-03-04
hey everyone,
I have an iso file that I want to mount. It turned out to contain only data so I need to make it into a working iso file using mkisof. For some  reason it was done in a couple of seconds while the file is more then 7Gb. The output is....nothing :s. I looked inside /media/isodrive and there is nothing there. The originale img is suddenly only 363Mb :s.
What am I doing wrong?

This is the commandline I used:

sven@sven-XPS-L501X:~/Desktop$ sudo mkisofs -o shaun.white.iso /media/isodrive/
[sudo] password for sven: 
I: -input-charset not specified, using utf-8 (detected in locale settings)
  2.69% done, estimate finish Fri Mar  4 19:04:42 2011
  5.38% done, estimate finish Fri Mar  4 19:04:23 2011
  8.06% done, estimate finish Fri Mar  4 19:04:17 2011
 10.76% done, estimate finish Fri Mar  4 19:04:14 2011
 13.44% done, estimate finish Fri Mar  4 19:04:12 2011
 16.13% done, estimate finish Fri Mar  4 19:04:11 2011
 18.82% done, estimate finish Fri Mar  4 19:04:15 2011
 21.51% done, estimate finish Fri Mar  4 19:04:14 2011
 24.19% done, estimate finish Fri Mar  4 19:04:13 2011
 26.88% done, estimate finish Fri Mar  4 19:04:12 2011
 29.57% done, estimate finish Fri Mar  4 19:04:11 2011
 32.26% done, estimate finish Fri Mar  4 19:04:11 2011
 34.94% done, estimate finish Fri Mar  4 19:04:13 2011
 37.63% done, estimate finish Fri Mar  4 19:04:12 2011
 40.32% done, estimate finish Fri Mar  4 19:04:12 2011
 43.01% done, estimate finish Fri Mar  4 19:04:11 2011
 45.69% done, estimate finish Fri Mar  4 19:04:11 2011
 48.39% done, estimate finish Fri Mar  4 19:04:13 2011
 51.07% done, estimate finish Fri Mar  4 19:04:12 2011
 53.76% done, estimate finish Fri Mar  4 19:04:12 2011
 56.45% done, estimate finish Fri Mar  4 19:04:12 2011
 59.14% done, estimate finish Fri Mar  4 19:04:11 2011
 61.82% done, estimate finish Fri Mar  4 19:04:11 2011
 64.51% done, estimate finish Fri Mar  4 19:04:12 2011
 67.20% done, estimate finish Fri Mar  4 19:04:12 2011
 69.89% done, estimate finish Fri Mar  4 19:04:12 2011
 72.57% done, estimate finish Fri Mar  4 19:04:11 2011
 75.26% done, estimate finish Fri Mar  4 19:04:11 2011
 77.95% done, estimate finish Fri Mar  4 19:04:12 2011
 80.64% done, estimate finish Fri Mar  4 19:04:12 2011
 83.32% done, estimate finish Fri Mar  4 19:04:12 2011
 86.02% done, estimate finish Fri Mar  4 19:04:11 2011
 88.70% done, estimate finish Fri Mar  4 19:04:11 2011
 91.39% done, estimate finish Fri Mar  4 19:04:11 2011
 94.08% done, estimate finish Fri Mar  4 19:04:12 2011
 96.77% done, estimate finish Fri Mar  4 19:04:12 2011
 99.45% done, estimate finish Fri Mar  4 19:04:12 2011
Total translation table size: 0
Total rockridge attributes bytes: 0
Total directory bytes: 0
Path table size(bytes): 10
Max brk space used 0
186021 extents written (363 MB)

---

### Post by TeoBigusGeekus on 2011-03-04
Try with 
```
sudo mkisofs -o shaun.white.iso -J /media/isodrive/
```

---

### Post by senca on 2011-03-05
> **TeoBigusGeekus said:**
> Try with 
```
sudo mkisofs -o shaun.white.iso -J /media/isodrive/
```

Tried it but the only thing that happens is that it takes about 5 seconds longer to complete. Again the same output: 363 Mb from a 7.4 Gb file :s

---

### Post by senca on 2011-03-05
Why is the path at the end of the commandline necessary? It doensn't seem to do anything :s

---

