---
title: "Software to prevent RSI. Alternatives to rsibreak, workrave, drwright"
date: 2012-06-11
forum: General Help
---

### Post by ranjith19 on 2012-06-11
Hey.

I wanted to install a application to prevent repetitive strain injury.

I tried workrave, it does not install. I do not know how to compile the source.

I tried drwright, installation fails through apt.

So I tried RSIbreak which works fine except that it is not storing my preferences.

Is it possible to do something about it? Or does anyone know a good application that will work on ubuntu 12.04.

PS: I really regret having moved from ubuntu 10.04 to 12.04. I hate unity.

---

### Post by ranjith19 on 2012-06-11
I was able to install the package workrave from [http://sourceforge.net/projects/workrave/files/latest/download?source=files](http://sourceforge.net/projects/workrave/files/latest/download?source=files)

I had to install dependencies by myself:

```
sudo apt-get install libxtst-dev libglibmm-2.4-dev libgtkmm-2.4-dev libsigc++-dev
./configure
make
sudo make install

```
It seems to be working fine.

---

