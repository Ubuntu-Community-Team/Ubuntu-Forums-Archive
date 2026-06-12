---
title: "n game issues"
date: 2010-09-01
forum: General Help
---

### Post by matthatesspam on 2010-09-01
I've recently discovered a game called "n" over [here]("http://www.thewayoftheninja.org/n_downloads.html"). I have played it on Windows without a hitch, but when I try to run the linux version I get his error:

```
./n_v14: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```

So, I tried searching for "libgtk-1.2.so.0" in the Synaptic Package Manager and the Software Repository to no avail. I'm at a loss to what to do; any help is appreciated.

---

### Post by lordhaworth on 2010-09-01
That probably means that libgtk-1.2.so.0 is out of date. What you can do though is go into synaptic package manager --> repositories  and manually add 

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse

If you then click the "reload" button and search for libgtk-1.2.so.0 you should be able to download it. However, you should remove the extra repository when you are done.

---

### Post by matthatesspam on 2010-09-01
I tried that and it came back with the same search results. This is weird.

---

### Post by lordhaworth on 2010-09-01
I searched ubuntu packages:
[http://packages.ubuntu.com/search?keywords=libgtk1.2&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=libgtk1.2&searchon=names&suite=all&section=all)

but don't know if it contains what you are after...

---

### Post by DrMelon on 2010-09-01
I've had this problem before.

```
sudo apt-get install libgtk1.2
```

worked for me.

---

### Post by matthatesspam on 2010-09-01
Still no dice.

```

matt@ThinkPad:~$ sudo apt-get install libgtk1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgtk1.2

```

---

### Post by kiddykoff on 2010-09-01
i've had the same problems, but i gave up on it. I'm also on a 64 bit machine, so i may have had more trouble than you.

I remember having to use libget.

---

