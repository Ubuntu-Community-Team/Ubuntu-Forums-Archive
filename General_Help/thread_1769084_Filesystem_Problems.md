---
title: "Filesystem Problems"
date: 2011-05-27
forum: General Help
---

### Post by Yellobes on 2011-05-27
Alright, so I'm having this crazy catch 22. 

```
me@mycompy:~$ rm -r '/media/iPod/.Trash-1000/expunged/#' 
rm: cannot remove `/media/iPod/.Trash-1000/expunged/#/\001.': No such file or directory
rm: cannot remove `/media/iPod/.Trash-1000/expunged/#': Directory not empty

```

Checking it with ls...

```
me@mycompy:~$ ls -la '/media/iPod/.Trash-1000/expunged/#'
ls: cannot access /media/iPod/.Trash-1000/expunged/#/.: No such file or directory
total 8
drwx------. 2 me me 4096 2010-10-30 02:45 .
drwx------. 3 me me 4096 2010-11-05 00:19 ..
-?????????? ? ?    ?       ?                ? ?.

```

That guy with the question marks won't show up as anything significant, but my filesystem is 1.3 gb fuller than it should be.

How do I get rid of this thing, aside from reformatting the device? What is this?

---

### Post by kamaji792 on 2011-05-27
Does doing:
```
ls -lab '/media/iPod/.Trash-1000/expunged/#'
```
Produce anything more interesting?

The -b option displays special characters in octal escapes.

Or how about:
```
rm -rf '/media/iPod/.Trash-1000/expunged/#'
```

The -f option "ignores nonexistent files, never prompt"

atb S

---

### Post by wildmanne39 on 2011-05-27
> **Yellobes said:**
> Alright, so I'm having this crazy catch 22. 

```
me@mycompy:~$ rm -r '/media/iPod/.Trash-1000/expunged/#' 
rm: cannot remove `/media/iPod/.Trash-1000/expunged/#/\001.': No such file or directory
rm: cannot remove `/media/iPod/.Trash-1000/expunged/#': Directory not empty

```

Checking it with ls...

```
me@mycompy:~$ ls -la '/media/iPod/.Trash-1000/expunged/#'
ls: cannot access /media/iPod/.Trash-1000/expunged/#/.: No such file or directory
total 8
drwx------. 2 me me 4096 2010-10-30 02:45 .
drwx------. 3 me me 4096 2010-11-05 00:19 ..
-?????????? ? ?    ?       ?                ? ?.

```

That guy with the question marks won't show up as anything significant, but my filesystem is 1.3 gb fuller than it should be.

How do I get rid of this thing, aside from reformatting the device? What is this?Hi, try this command
```
sudo apt-get --purge remove package name
```

---

### Post by katykat on 2011-05-27
Use a decent file manager such as mc or gnome-commander.
Make sure to tell it to show hiden files. 

If you can highlight the filename you may be able to delete it. 

Or else from a bootcd check and fix the file system.

---

