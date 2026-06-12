---
title: "problem with cpufreqd"
date: 2011-08-10
forum: General Help
---

### Post by gufide on 2011-08-10
Hello there, I got some problem with cpufreqd, I think it doesn't work because *sudo lsmod | grep cpufreq *give me: ```
No cpufreqd socket found
``` Is this say me that cpufreqd doesn't work? Is there a solution to this?

---

### Post by gufide on 2011-08-11
bump

---

### Post by majoballs on 2011-11-27
Add
```
enable_remote=1
```

in section 
```
[Gerneral]
``` of /etc/cpufreqd.conf

[source]("http://gehype.blogspot.com/2009/02/tipcpufreqd-get-error-no-cpufreqd.html")

---

