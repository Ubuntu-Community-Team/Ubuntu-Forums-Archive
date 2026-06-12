---
title: "Removing Something from my Respiratory"
date: 2011-08-15
forum: General Help
---

### Post by Hosmion on 2011-08-15
Hello everyone.  In my efforts to try and find a working screencaster, a fellow Ubuntu mate helped me out by giving me some commands to get "Kazam Screencaster."  I used the commands but it didn't work, and now when I:

```
sudo apt-get update
```

It gives me the error:

```
W: Failed to fetch http://ppa.launchpad.net/and471/kazam-daily-stable/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/and471/kazam-daily-stable/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

How do I remove the kazam-daily-stable from my respiratory?

Thanks,
Leonard

P.S.  If you could help me with my screen recorder problem, that'd be great also.  Link: [http://ubuntuforums.org/showthread.php?t=1824958]("http://ubuntuforums.org/showthread.php?t=1824958")

---

### Post by knutschr on 2011-08-15
```
gksu gedit /etc/apt/sources.list
```
Remove the lines.Save.

repository :-/

---

### Post by grahammechanical on 2011-08-15
Or,

Open Ubuntu Software Centre, click Edit and click on Software Sources and then open the Other software tab and select the relevant ppa and click remove.

Or, 

Open Update Manager, click on Settings, select the Other Software tab, select the relevant ppa and click remove.

Regards.

---

### Post by Hosmion on 2011-08-15
Thanks guys, it worked.

---

