---
title: "How to install Tandem Repeats Finder, It is not simple"
date: 2010-07-21
forum: General Help
---

### Post by john1923 on 2010-07-21
Hi

I am trying to install a program called Tandem Repeats Finder on Ubuntu 10.04, 64-bit.

This is the website, 

```
[http://tandem.bu.edu/trf/trf404.linux64.download.html](http://tandem.bu.edu/trf/trf404.linux64.download.html)

```The file that gets downloaded is called 

```
trf404.linux64.exe
``` and claims to be some kind of binary file.

I have tried

```
sudo chmod a+x 
```and then typed it's name into the terminal, that didn't work so I am out of ideas.

I also can't find the source code or a Ubuntu package for this program

Any help or suggestions are appreciated as I am a but stuck.

---

### Post by oldos2er on 2010-07-21
According to the installation instructions, you need to move it to a directory in your path. I used **sudo mv trf404.linux64.exe /usr/local/bin** then typed **trf404.linux64.exe**, and it worked.

---

### Post by john1923 on 2010-07-22
Thank you  oldos2er

It worked perfectly. I didn't know what my path was. Now I do.

---

