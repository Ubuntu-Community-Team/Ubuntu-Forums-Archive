---
title: "File System out of space!!!"
date: 2012-02-08
forum: General Help
---

### Post by astrobob.tk on 2012-02-08
Hello there,

I just got a message saying that the "File System" is on low space (~700+MB). Included are screenshots of gparted & baobab.

Although I have set / to 25GB (practically 23), still I have used all of it?! I did indeed install loads of software but does it take all the 25GB?

Do you see any "issues" in the partition table? What should I do to accommodate for the File System?

Note: I use the "Programs" partition as a 2nd Win partition on which I installed a couple of software & where my music is located. It's the best place to grab space from.

[IMG]http://img823.imageshack.us/img823/579/devsdagparted011.png[/IMG]

[IMG]http://img269.imageshack.us/img269/6408/diskusageanalyzer012.png[/IMG]

---

### Post by searchfgold6789 on 2012-02-08
You can use Ubuntu-Tweak along with Bleachbit to free up a bit of space if you need to. Works well.

---

### Post by astrobob.tk on 2012-02-08
> **searchfgold6789 said:**
> You can use Ubuntu-Tweak along with Bleachbit to free up a bit of space if you need to. Works well.

I am using bleachbit but nothing impressive yet!

I just removed some packages am not using & increased the root to 97MB.

---

### Post by oldos2er on 2012-02-08
Info here on freeing up disk space: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by astrobob.tk on 2012-02-08
> **oldos2er said:**
> Info here on freeing up disk space: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

Thanks :D

Just a few minutes ago I removed a few unused packages & deleted my evolution accounts (am using Thunderbird instead) & removed a big folder from .wine (~6.6GB). Now, / is 6.0GB or as the command ```
dh -TH
``` shows:

```
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda7     ext4     23G   16G  6.1G  73% /

```

Will try to free up more & expand the /, maybe?

---

