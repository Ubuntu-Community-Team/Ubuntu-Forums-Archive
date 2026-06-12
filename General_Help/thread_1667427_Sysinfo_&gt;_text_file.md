---
title: "Sysinfo &gt; text file"
date: 2011-01-14
forum: General Help
---

### Post by gypsumwolf on 2011-01-14
Is there a good command to send all the details of Sysinfo to a text file?

---

### Post by TeoBigusGeekus on 2011-01-15
Something like
```
sysinfo|tee ~/Desktop/file.txt
```

---

### Post by gypsumwolf on 2011-01-15
> **TeoBigusGeekus said:**
> Something like
```
sysinfo|tee ~/Desktop/file.txt
```

I tried that with tree (not tee^) and i got a file that was empty.

sysinfo|tree ~/Desktop/file.txt
/home/wolf/Desktop/file.txt [error opening dir]

0 directories, 0 files

---

### Post by efflandt on 2011-01-16
Is there something wrong with File > Save from the sysinfo menus?

---

### Post by TeoBigusGeekus on 2011-01-16
> **gypsumwolf said:**
> I tried that with tree (not tee^) and i got a file that was empty.

sysinfo|tree ~/Desktop/file.txt
/home/wolf/Desktop/file.txt [error opening dir]

0 directories, 0 files

It's tee, not tree.

```
man tee

NAME
       tee - read from standard input and write to standard output and files
```

---

### Post by gypsumwolf on 2011-01-18
I tried. Here is the results.

```
$:~$ sysinfo|tee ~/Desktop/file.txt
GConf.NoSuchKeyException: Key '/apps/sysinfo/initial_animation' not found in GConf
  at GConf.Client.Get (System.String key) [0x00000] in <filename unknown>:0 
  at Sysinfo.Sysinfo.UpdateFromGConf () [0x00000] in <filename unknown>:0 
GConf.NoSuchKeyException: Key '/apps/sysinfo/window_width' not found in GConf
  at GConf.Client.Get (System.String key) [0x00000] in <filename unknown>:0 
  at Sysinfo.Sysinfo..ctor (System.String[] args) [0x00000] in <filename unknown>:0 
GConf.NoSuchKeyException: Key '/apps/sysinfo/section_start' not found in GConf
  at GConf.Client.Get (System.String key) [0x00000] in <filename unknown>:0 
  at Sysinfo.Sysinfo..ctor (System.String[] args) [0x00000] in <filename unknown>:0 
$:~$ cd Desktop/
$:~/Desktop$ ls
file.txt
$:~/Desktop$ more file.txt 
GConf.NoSuchKeyException: Key '/apps/sysinfo/initial_animation' not found in GCo
nf
  at GConf.Client.Get (System.String key) [0x00000] in <filename unknown>:0 
  at Sysinfo.Sysinfo.UpdateFromGConf () [0x00000] in <filename unknown>:0 
GConf.NoSuchKeyException: Key '/apps/sysinfo/window_width' not found in GConf
  at GConf.Client.Get (System.String key) [0x00000] in <filename unknown>:0 
  at Sysinfo.Sysinfo..ctor (System.String[] args) [0x00000] in <filename unknown
>:0 
GConf.NoSuchKeyException: Key '/apps/sysinfo/section_start' not found in GConf
  at GConf.Client.Get (System.String key) [0x00000] in <filename unknown>:0 
  at Sysinfo.Sysinfo..ctor (System.String[] args) [0x00000] in <filename unknown
>:0 
$:~/Desktop$ 
```

---

