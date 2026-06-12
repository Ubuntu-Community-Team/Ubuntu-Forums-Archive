---
title: "/var/lib/dpkg/info/ destroyed"
date: 2010-02-06
forum: General Help
---

### Post by frt975 on 2010-02-06
I was running[ this]("http://ubuntuforums.org/showthread.php?t=1004376") script, but it destroyed /var/lib/dpkg/info/. (It's worked before)
Then I tried fixing the problem by running [this]("http://linuxmafia.com/faq/Debian/package-database-rebuild.html"), but nothing happened. How do I get my  /var/lib/dpkg/info/ back so that I can use apt-get?

---

### Post by Soul-Sing on 2010-02-06
```
sudo apt-get update
``` should restore it.

---

### Post by frt975 on 2010-02-06
I just ran apt-get -f upgrade and got
```
E: Internal Error, Could not perform immediate configuration (2) on libselinux1
```

---

### Post by frt975 on 2010-02-06
Dpkg -i on /var/cache/apt/archives results in many errors that look like this ```
Selecting previously deselected package cabextract.
Unpacking cabextract (from cabextract_1.2-3_i386.deb) ...
dpkg: error processing cabextract_1.2-3_i386.deb (--install):
 unable to create updated files list file for package cabextract: No such file or directory

```

---

### Post by gmargo on 2010-02-06
I believe it can be done, if you still have the **/var/lib/dpkg/status** or **/var/lib/dpkg/status-old** file, but the recovery script you tried might have blown them away.

But the first thing you must do is make a copy of the remains of your **/var/lib/dpkg** directory.  Which, you now realize, you should have done before running the original horrible "optimizer" script.

From the **/var/lib/dpkg/status** file you can easily extract a list of installed packages, and download the relevant _.deb_ files.  There is a direct correlation between the files in the **/var/lib/dpkg/info** directory and the content of the associated _.deb_ file.  It should be relatively easy to write a script to regenerate the _info_ directory.  *I think*. :eek:

So, do you have a good copy of the **status** file?

---

### Post by frt975 on 2010-02-09
I reinstalled and now before I run that script I'll backup.

---

