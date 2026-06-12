---
title: "Who does use updatedb?"
date: 2009-09-29
forum: General Help
---

### Post by ilna on 2009-09-29
There is a daily script 

```
/etc/cron.daily/mlocate
```

Which services/applications are interested in using updatedb results?

Which disadvantages have these steps:

- remove this script,
- replace 'defaults' with 'noatime' in /etc/fstab for HDD partitions?

---

### Post by wojox on 2009-09-29
The:

```
locate
```

utility. For locating files in the filesystem.

Ex.

```
locate firefox
```

---

### Post by ilna on 2009-09-29
I know about 'locate' ;) I'm interested in information about Ubuntu-specific services/applications which do use 'locate'.

---

### Post by wojox on 2009-09-29
Sorry I'm very command line driven. :)

I would assume if you went to Places > Search for Files it probably invokes locate.

---

### Post by ilna on 2009-09-29
I have not 'Places > Search' as far as use Kubutu :) And I'm also oriented to CLI at many every day tasks. All these doesn't help me to answer questions in first thread post.

---

### Post by sisco311 on 2009-09-29
> **ilna said:**
> I know about 'locate' ;) I'm interested in information about Ubuntu-specific services/applications which do use 'locate'.

```
apt-cache rdepends mlocate
```


The default mount option in Ubuntu is relatime.

the defaults option is added implicitly:
```
/dev/sda1 /mnt auto relatime 0 0
```
is the same as:
```
/dev/sda1 /mnt auto relatime,defaults 0 0
```

```
       relatime
              Update inode access times relative to  modify  or  change  time.
              Access time is only updated if the previous access time was ear&#8208;
              lier than the current modify or change time. ([B]Similar  to  noat&#8208;
              ime,  but  doesn't break mutt or other applications that need to
              know if a file has been read since the last time  it  was  modi&#8208;
              fied.[/B])
```

---

### Post by wojox on 2009-09-29
Well when you need to search for something using a gui in kde what do you use? That gui probably invokes locate.

---

### Post by ilna on 2009-09-29
sisco311,

1. how to determine 'apt-cache rdepends mlocate' (taking in mind it belongs to 'apt' package, and last one doesn't depend on mlocate if to look at 'aptitude -v show' output.

2. I have not modified fstab, but there are 'defaults' (except for '/', which has 'errors=remount-ro') options (have started from Kubuntu Karmic A4). Must I add (or replace 'defaults' with) 'realtime' option?

wojox,

Commonly I know what and where is located. At those cases when I don't, I use Krusader (mostly searching with context - instead of 'grep').

---

