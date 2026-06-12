---
title: "lzma problem. Can't install nor upgrade anything."
date: 2009-06-27
forum: General Help
---

### Post by Gummi on 2009-06-27
I've had a problem for the last few months. That problem makes it unable for me to install nor upgrade anything. When I try I get this error:


```

dpkg: error processing (insert package name.filext here) (--remove/install/upgrade):
files list file for package `lzma' contains empty filename
E: Sub-process /usr/bin/dpkg exited unexpectedly

```
This is actually quite the bother. I do hope you can help me.

---

### Post by TeoBigusGeekus on 2009-06-27
Try
```
sudo dpkg --configure -a
```

---

### Post by Gummi on 2009-06-27
I have quite a few times, it has proven ineffective at all times.

---

### Post by ajgreeny on 2009-06-27
Try using synaptic and fixing any broken packages from the edit menu. It seems that there is a problem with **lzma** in some way, so perhaps try reinstalling that if still no-go.

---

### Post by Gummi on 2009-06-27
There are no packages listed as broken, I attempted to reinstall the 'lzma' package itself, but alas the original error showed.

---

### Post by Gummi on 2009-06-27
I've tried to reinstall everything connected to lzma nothing worked

---

### Post by Gummi on 2009-06-27
Bump. I really do need some help here as I'm not very qualified with machinery.

---

### Post by Gummi on 2009-06-28
Is there really no one that can help me?

---

### Post by Gummi on 2009-06-28
I don't really want to be bumping this thread, but this is quite a fix I'm in. Not being able to install nor upgrade anything is really bothersome.

---

### Post by michy99 on 2009-06-28
What is the output of this command?```
ls /var/cache/apt/archives
```

---

### Post by Gummi on 2009-06-28
```
hipo_0.6.1-0ubuntu2_all.deb         lzma_4.43-12ubuntu1_i386.deb
lock                                partial
lzma-dev_4.43-12ubuntu1_i386.deb    podsleuth_0.6.1-1_all.deb
lzma-source_4.43-12ubuntu1_all.deb
```

---

### Post by michy99 on 2009-06-28
Try this and see if it helps.```
sudo rm /var/cache/apt/archives/lzma*
sudo apt-get update
```

---

### Post by Gummi on 2009-06-28
This unfortunately did help very little but remove the folder.

---

### Post by michy99 on 2009-06-28
What errors do you get from```
sudo apt-get update
```

---

### Post by Gummi on 2009-06-28
I actually got no errors from that command, but the original problem still resides.
I attempted later on to install the new flash player 10 and the error I have dealt with from the beginning appeared.

---

### Post by Gummi on 2009-06-29
[IMG]http://img265.imageshack.us/img265/9794/errorz.png[/IMG]
This is what happened to be precise

---

### Post by Gummi on 2009-07-01
Yet another bump

---

