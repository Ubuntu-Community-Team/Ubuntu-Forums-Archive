---
title: "Firefox 3.6 &amp; 3.5"
date: 2010-02-20
forum: General Help
---

### Post by Silvertones on 2010-02-20
I installed 3.6 from Ubuntuzilla. The icon launches 3.6 .How do I launch 3.5?

---

### Post by viralmeme on 2010-02-20
> **Silvertones said:**
> I installed 3.6 from Ubuntuzilla. The icon launches 3.6 .How do I launch 3.5?
Create a new launcher icon and point it to /usr/lib/firefox-3.5.3/firefox

---

### Post by cong06 on 2010-02-20
On my computer I only have one firefox version installed, but just to give you an idea:

```

user@computer:~$ ls -al /usr/bin/fire*
lrwxrwxrwx 1 root root 11 2010-02-19 12:06 /usr/bin/firefox -> firefox-3.0
lrwxrwxrwx 1 root root 32 2010-02-19 12:06 /usr/bin/firefox-3.0 -> ../lib/firefox-3.0.18/firefox.sh

```

What the icon calls is /usr/bin/firefox. When you install a version of firefox, this file changes to point to the new version.

I'm fairly certain that the actual executable for firefox-3.5 is:
```

/usr/bin/firefox-3.5

```
Try that and see if it works.

If it doesn't, try running:
```

ls -al /usr/bin/firefox*

```

Could help us/you also.

---

### Post by cong06 on 2010-02-20
> **ymitchell said:**
> Create a new launcher icon and point it to /usr/lib/firefox-3.5.3/firefox

The problem is once there's an upgrade, it won't be 3.5.3 it'll be 3.5.X
It's better to point to versions in /usr/bin since they're updated automatically.

---

### Post by Silvertones on 2010-02-20
> **cong06 said:**
> The problem is once there's an upgrade, it won't be 3.5.3 it'll be 3.5.X
It's better to point to versions in /usr/bin since they're updated automatically.

Worked fine thank you.
The reason I wanted to revert back is to test the two. I'm getting some stalling when pages load. This was happening in windows as well. I want to check if 3.5.8 is stalling also.
If anyone has ideas...........

---

### Post by nanotube on 2010-02-20
> **Silvertones said:**
> Worked fine thank you.
The reason I wanted to revert back is to test the two. I'm getting some stalling when pages load. This was happening in windows as well. I want to check if 3.5.8 is stalling also.
If anyone has ideas...........

well, for the future: the ubuntuzilla repo diverts the official-ubuntu-firefox link to /usr/bin/firefox.ubuntu so you can use that one to start 3.5.  that said, highly not recommended to share the same profile between two versions.

as far as stalling etc - try a fresh profile. most of the "firefox is slow" or "firefox is crashing" problems come from a borked profile.

---

### Post by Silvertones on 2010-02-21
Brand new profile now. Seems much better. My old profile has been copy/pasted back and forth from machine to machine, Windows to Ubuntu etc. So it probably was a little corrupt. In the new profile I just restored my bookmarks. I then installed all of my ext fresh.

---

