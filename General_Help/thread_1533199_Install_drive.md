---
title: "Install drive"
date: 2010-07-17
forum: General Help
---

### Post by João Oliveira on 2010-07-17
Hi everybody! So...I need to instal a driver called X7170SampleSANE-1.0-1!

Path: home/joao/Documentos/X7170SampleSANE-1.0-1

[http://img819.imageshack.us/img819/5046/capturaecraf.png](http://img819.imageshack.us/img819/5046/capturaecraf.png)


help!

---

### Post by AlphaLexman on 2010-07-17
Have you tried:
```
./configure
make
sudo make install
```

---

### Post by João Oliveira on 2010-07-18
What's the complete code?!

---

### Post by AlphaLexman on 2010-07-18
Apparently, you have to compile the source code. In a terminal, type:
```
./configure
```
Press enter, make note of any errors and post them here. If you do not get any errors, type:
```
make
```
Press enter, make note of any errors and post them here. If you do not get any errors, type:
```
sudo make install
```
enter your password when prompted, If everything goes well, your driver should be installed.

Good luck.

---

