---
title: "init(8) causes lots of disk IO"
date: 2012-09-20
forum: General Help
---

### Post by mife on 2012-09-20
Hi,

I have an ubuntu 12.04 installed on SSD and I've recently discovered that my init process (upstart) produces high amount of disk writes. I measure it using write_bytes parameter from /proc/1/io. This gives 1854619648 bytes (1.8GB) after 2 days of uptime and 12152082432 bytes (12GB!!!) after 4 days of uptime.

I tried lsof:
```
lsof | grep -E '^init'
init         1       root  cwd   unknown                             /proc/1/cwd (readlink: Permission denied)
init         1       root  rtd   unknown                             /proc/1/root (readlink: Permission denied)
init         1       root  txt   unknown                             /proc/1/exe (readlink: Permission denied)
init         1       root NOFD                                       /proc/1/fd (opendir: Permission denied)

```and it gives me no clue.

So my question is what are these writes?

---

