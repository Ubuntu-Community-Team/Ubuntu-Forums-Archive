---
title: "Installed vuze....But where is it?"
date: 2010-05-02
forum: General Help
---

### Post by Adrienk on 2010-05-02
On windows its in the C:/ProgramFile/vuze

on Linux when typing in whereis vuze I get:

/usr/bin/vuze
/usr/share/man/man1/vuze.1.gz

I am looking for the swt.jar to include in java project that has to do with vuze src code.

BUT

when I type in whereis swt.jar I get "swt:" and thats it....

so where is this swt.jar file? that is supose to be part of vuze?


Linux version: ubuntu 10.4

---

### Post by WorMzy on 2010-05-02
Common places it could be are /opt/vuse and /usr/lib/vuse

I'm guessing the folder would be called vuse, as I don't use it. Have a look in the /opt and /usr/lib folders if the above folders don't exist.

---

### Post by SnickerSnack on 2010-05-02
I've never used it before, but it looks like whereis only searches for runnable commands.  You need to use find or locate (run "sudo updatedb" first for locate).  Try

```
locate swt.jat
```

it will probably give a long list of files (with locations).  You can then narrow your search with

```
locate swt.jar | grep [search term]
```

If you want to remove a search term (basically like saying 'do not return items with this term'), use

```
locate swt.jar | grep -v [search term]
```

You can also try looking in your home folder for a hidden folder that may house the files you need to add.  Try

```
cd ~ ; ls -a
```

---

### Post by Adrienk on 2010-05-02
neither of those exist :S - what i mean is theirt is no folder named vuze, and when i search swt.jar the search sais it dosent exist
I installed vuse via the terminal with apt-get install vuze
which shouldnt matter much..

---

### Post by Adrienk on 2010-05-02
> **SnickerSnack said:**
> I've never used it before, but it looks like whereis only searches for runnable commands.  You need to use find or locate (run "sudo updatedb" first for locate).  Try

```
locate swt
```it will probably give a long list of files (with locations).  You can then narrow your search with



Does nothing its like

root@adam:~# locate swt
root@adam:~#

Thats it

---

### Post by Adrienk on 2010-05-02
I am also wondering where is vuze installed in general where are all the files installed?

---

### Post by Boss Happy on 2010-05-10
I also tried re-installing Vuze from the Synaptic Package Manager and it wouldn't take.  So I completely removed it (again using Synaptic).

I noticed the Vuze icon still appeared under Applications -> Internet -> Vuze.

Finally, I opened the Ubuntu Software Center(USC), under Applications, I removed Vuze using the USC and re-installed Vuze (again with USC) and now it works.

---

