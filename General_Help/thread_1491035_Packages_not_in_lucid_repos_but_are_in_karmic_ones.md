---
title: "Packages not in lucid repos but are in karmic ones"
date: 2010-05-23
forum: General Help
---

### Post by ztrange on 2010-05-23
I wanted to install opera browser (not that I like it) in my new lucid (updated from karmic) but the package is not in the repos.
I also need libmysqlclient15off as a dependency for mysql-workbench but is also missing from lucid repos. 

However, they are in the karmic repos. So, what should I do? I could download de debs and install them but my question is whether they should be available in lucid repos and if the'll be...

Thanks in advance

---

### Post by SlidingHorn on 2010-05-23
I think there may have been a licensing issue with Opera, and as far as I know, it's not in the repos anymore.  You can still get it though:

Add generic Opera repository 

```
deb http://deb.opera.com/opera/ stable non-free
```

Add the Opera GPG key:

```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
sudo apt-get install debian-archive-keyring
```

Install:

```
sudo apt-get update
sudo apt-get install opera
```

libmysqlclient15off was also dropped from the repos for some reason which I am unaware.  However, you can install it from the Karmic package list here: [[color="Blue"]http://packages.ubuntu.com/karmic/libmysqlclient15off[/color]]("http://packages.ubuntu.com/karmic/libmysqlclient15off")

Hope this helps!

---

### Post by ztrange on 2010-05-23
Thanks for taking the time to give such complete answer. I was just wondering, about the libmysql thing, if it has something to do with oracle doing more things to be rejected by users (as they usually do) or it was a mistake. Also if maybe it was possible to get package from some sort of backports repo.

Thanks for your time

---

