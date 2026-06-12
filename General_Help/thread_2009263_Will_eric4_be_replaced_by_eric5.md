---
title: "Will eric4 be replaced by eric5?"
date: 2012-06-24
forum: General Help
---

### Post by hjvangelder on 2012-06-24
I really like the Eric IDE for python programming. Currently there are two major versions of Eric; Version 4 supports python 2.x and version 5 supports python 3.x. Since I would like to use the 'latest and greatest' python version I was wondering if there is a way to find out if (and when) Eric5 will be added to the software repositorys. Anyone got a clue where to look?

---

### Post by rai4shu2 on 2012-06-25
I think the main hold up is the Python 3 support in Debian is a little uninspiring. Eric is pretty nice, but I would probably stick with Geany or something lighter myself.

A lot of the dependencies for Eric5 are in the repositories in 12.04, so it isn't as big a challenge to build from source as it was a year or so ago.

---

### Post by RGilbert on 2012-11-05
To install eric5 on 12.04, download package from Eric Python IDE website. Unpack to home directory.

sudo apt-get install

python3.2
python-qt4
python3-pyqt4
libqscintilla2-8
python3-pyqt4.qsci

cd to unpacked eric5 subdirectory
     and then
sudo python3 install.py

---

