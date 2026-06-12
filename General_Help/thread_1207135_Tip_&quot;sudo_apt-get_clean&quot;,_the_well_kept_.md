---
title: "Tip: &quot;sudo apt-get clean&quot;, the well kept secret"
date: 2009-07-07
forum: General Help
---

### Post by kwilliam on 2009-07-07
Did you know that /var/cache/apt/archives grows indefinitely?

```
man apt-get

    clean
        clean clears out the local repository of retrieved package files. It
        removes everything but the lock file from /var/cache/apt/archives/
        and /var/cache/apt/archives/partial/. When APT is used as a
        dselect(8) method, clean is run automatically. [B][SIZE="4"]Those who do not use[/SIZE]
        [SIZE="4"]dselect will likely want to run apt-get clean from time to time to[/SIZE]
        [SIZE="4"]free up disk space.[/SIZE][/B]
```

**Why was I never told about this?** It seems like the kind of thing that would be mentioned in the "10 Top Linux Tricks" type article that appears on Digg once a week. (Or use too... I don't read Digg anymore.) I've used Linux for years and had never heard of this. I was about to repartition because I was low on disk space, when I thought, "Eh, I'll pull out Filelight and see what in / is taking up space."

To my HOLY CRAP surprise, [SIZE="4"]2.8 GB[/SIZE] out of the 9.2GB being used were taken up by old packages!! I won't need to repartition at all; after running "apt-get clean" I went from being 91% full to 63% full.

---

### Post by wojox on 2009-07-07
Here is another secret source

[http://www.debian.org/doc/manuals/apt-howto/index.en.html#contents](http://www.debian.org/doc/manuals/apt-howto/index.en.html#contents)

---

### Post by kerry_s on 2009-07-07
> **kwilliam said:**
> Did you know that /var/cache/apt/archives grows indefinitely?

```
man apt-get

    clean
        clean clears out the local repository of retrieved package files. It
        removes everything but the lock file from /var/cache/apt/archives/
        and /var/cache/apt/archives/partial/. When APT is used as a
        dselect(8) method, clean is run automatically. [B][SIZE="4"]Those who do not use[/SIZE]
        [SIZE="4"]dselect will likely want to run apt-get clean from time to time to[/SIZE]
        [SIZE="4"]free up disk space.[/SIZE][/B]
```

**Why was I never told about this?** It seems like the kind of thing that would be mentioned in the "10 Top Linux Tricks" type article that appears on Digg once a week. (Or use too... I don't read Digg anymore.) I've used Linux for years and had never heard of this. I was about to repartition because I was low on disk space, when I thought, "Eh, I'll pull out Filelight and see what in / is taking up space."

To my HOLY CRAP surprise, [SIZE="4"]2.8 GB[/SIZE] out of the 9.2GB being used were taken up by old packages!! I won't need to repartition at all; after running "apt-get clean" I went from being 91% full to 63% full.


try deleting /usr/share/doc & /usr/share/man if you don't use them, that will probably cut that 63% in half.

---

