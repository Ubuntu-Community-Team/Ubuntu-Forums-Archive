---
title: "du command broken in 9.10?"
date: 2009-11-17
forum: General Help
---

### Post by gollum77 on 2009-11-17
When I execute *du* on a certain directory it tells me its size is 15MB

```
du -h -s -c -k /home/xyz/abc
15M     /home/xyz/abc
```

Interestingly… folder properties for *abc* reports:
```
2,432 items, totalling 100.4 MB
```
Is the du command broken in 9.10? 

PS: I remember that this used to work in 9.04.
Thanks

---

### Post by jpeddicord on 2009-11-17
> **gollum77 said:**
> When I execute *du* on a certain directory it tells me its size is 15MB

```
du -h -s -c -k /home/xyz/abc
15M     /home/xyz/abc
```

Interestingly… folder properties for *abc* reports:
```
2,432 items, totalling 100.4 MB
```
Is the du command broken in 9.10? 

PS: I remember that this used to work in 9.04.
Thanks

Try just:
```
du -sh /home/xyz/abc
```

Check the disk usage in Disk Analyzer (baobab) or Nautilus and see what is really correct. :)

---

### Post by gollum77 on 2009-11-17
> **jpeddicord said:**
> Try just:
```
du -sh /home/xyz/abc
```

Check the disk usage in Disk Analyzer (baobab) or Nautilus and see what is really correct. :)

*du -sh /home/xyz/abc* shows 15MB which is incorrect. Nautilus reports the correct size which is around 100MB. I am calling *du* in a script that was working with 9.04 and I am trying to get it to work again with 9.10.

---

### Post by gollum77 on 2009-11-17
I just found a bug report for this issue:

[https://bugs.launchpad.net/ubuntu/+source/coreutils/+bug/416981](https://bugs.launchpad.net/ubuntu/+source/coreutils/+bug/416981)

---

