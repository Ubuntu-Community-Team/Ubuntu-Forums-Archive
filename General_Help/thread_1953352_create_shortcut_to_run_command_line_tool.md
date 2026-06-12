---
title: "create shortcut to run command line tool"
date: 2012-04-06
forum: General Help
---

### Post by DataSpy on 2012-04-06
How can I create a launcher shortcut to run a commandline tool.  It's annoying to have to cd every time I want to use a commandline tool!!

here's what I tried in the launcher so far but it doesn't change the directory or bring up the tool

gnome-terminal cd /home/dataspy/shares/storage/progs/

any help would be great appreciated!!

---

### Post by ianhaycox on 2012-04-06
```
gnome-terminal --working-directory '/home/dataspy/shares/storage/progs/'
```

---

### Post by DavisS87 on 2012-04-06
Thanks Ian

This helped me too



__________________[]("http://www.rxonepharmacy.com/brand_******.php")
[Online Pharmacy](http://www.rxonepharmacy.com)

---

### Post by DataSpy on 2012-04-06
Thanks, just what I was looking for!!!

is there any way to call a .pl script as well or would I just have to type it after I've clicked the shortcut?

like
gnome-terminal --working-directory '/home/dataspy/shares/storage/progs/'+./script.pl

---

### Post by ianhaycox on 2012-04-06
Have a look at

```
$ man gnome-terminal
```

and I expect the -e or -x option is what you want.

---

