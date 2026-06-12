---
title: "df and du Show Different Disk Usage.."
date: 2009-12-03
forum: General Help
---

### Post by Deacon Frost on 2009-12-03
I've been in the IRC for a few, and jrib's been pretty helpful in at least figuring out what the problem was, and I figured I'd make it a little more simple by instead posting a thread (so it can also be used for future references.)

Alright, I recently switched to Ubuntu, and used an external hd to copy all of my files and switch them over. Well, then I went to delete the files, and well, it moved the folder to the trash bin, and I thought that was that. However, when I looked at the properties to make sure I got everything, the space was unchanged, and it seemed the files were still in the external.

I ran a disk usage analyzer, and it said that it was not the same. Then I went on the IRC, jrib had me run du and df in the terminal, and they both reported differently. du said there was 175G on the external, which is what the analyzer said. And df said there was 268G on the external, which is what the properties said.

[http://www.walkernews.net/2007/07/13/df-and-du-command-show-different-used-disk-space/](http://www.walkernews.net/2007/07/13/df-and-du-command-show-different-used-disk-space/)

jrib linked me there, and I read over it, but am kind of at a loss. I've restarted since I deleted the files from the external, and have no clue what I'm looking for =/.

Any help is appreciated :). Thanks.

---

### Post by SPr on 2009-12-03
df measures the size of the filesystem including the journal, tables etc (as you can probably tell I don't know much about filesystems).

du measures the size of just the files.
```

whatis du
du (1)               - estimate file space usage
whatis df
df (1)               - report file system disk space usage

```

That's my understanding, anyway.

---

### Post by endBc on 2009-12-03
```
endbc@ubuntu:~$ sudo du -ah / --max-depth 0
[sudo] password for endbc: 
3.0G    /
``````
endbc@ubuntu:~$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              72G  3.2G   66G   5% /
```

Don't know where it lost 0.2G but I doubt it's the most important part here since both commands return +/- the same value ( 0.2G / 80G doesn't seem to be worth worrying ).

---

