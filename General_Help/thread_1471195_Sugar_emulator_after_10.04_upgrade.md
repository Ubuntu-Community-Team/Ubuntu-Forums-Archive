---
title: "Sugar emulator after 10.04 upgrade"
date: 2010-05-03
forum: General Help
---

### Post by idzikow on 2010-05-03
I have upgraded to 10.04 and I'm trying to make sugar-emulator to work.

I'm reinstalling sugar:

```
sudo apt-get install ubuntu-sugar-remix

The following packages have unmet dependencies.
  ubuntu-sugar-remix: Depends: sugar-activities but it is not going to be installed
E: Broken packages


sudo apt-get install sugar-activities 

The following packages have unmet dependencies.
  sugar-activities: Depends: hulahop but it is not installable
E: Broken packages


sudo apt-get install hulahop
E: Package hulahop has no installation candidate

sudo apt-get install python-hulahop
python-hulahop is already the newest version.

```

any ideas?

---

### Post by idzikow on 2010-05-04
I have installed this python-hulahop:
```
http://packages.ubuntu.com/karmic/python-hulahop
```and then hulahop:
```
http://packages.ubuntu.com/karmic/hulahop
```Now I can install ubuntu-sugar-remix but I get this error:

```
sugar-emulator 
Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "/usr/lib/python2.6/dist-packages/jarabe/util/emulator.py", line 26, in <module>
    from sugar import env
ImportError: cannot import name env
```

---

