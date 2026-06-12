---
title: "handling spaces in files (cp/cat)"
date: 2009-11-07
forum: General Help
---

### Post by Macamba on 2009-11-07
Hello,

This must be 'Linux 101', but it's bugging me. I have a directory filled with a film, broken up in parts. But instead of using rar to do it, the film is broken up in .001, .002 and so on. Normally I can cat that, but the film has the additional problem that the file names contain spaces. So how do I handle it?

Imagine the directory is filled with:
```
me@home: ~/some/directory/sub directory$ ls
me@home: ~/some/directory/sub directory/this is the film.avi.001
me@home: ~/some/directory/sub directory/this is the film.avi.002
...
me@home: ~/some/directory/sub directory/this is the film.avi.vol203+26.PAR2
```

I tried it with the following script:
```
#!/bin/bash
for i in {1..9}
do
  cp \this\ is\ the\ film.avi.00$i bos12a.avi.00$i
done
```

But I get the following error
```

cp: cannot stat `this is the film.avi.001': No such file or directory'
cp: cannot stat `this is the film.avi.002': No such file or directory'

```

How do I solve this?

Macamba

---

### Post by dcstar on 2009-11-07
> **Macamba said:**
> Hello,

This must be 'Linux 101', but it's bugging me. I have a directory filled with a film, broken up in parts. But instead of using rar to do it, the film is broken up in .001, .002 and so on. Normally I can cat that, but the film has the additional problem that the file names contain spaces. So how do I handle it?
.......
How do I solve this?

Macamba

Put quotes around the names.

---

### Post by diesch on 2009-11-07
```
#!/bin/bash
for i in {1..9}
do
  cp "this is the film.avi.00$i" "bos12a.avi.00$i"
done
```
should do the job.

In general quote your shell variables unless you know you don't want to.

---

### Post by Macamba on 2009-11-08
Hi diesch and dcstar,

I tried:
```
#!/bin/bash
for i in {1..9}
do
  cp "this is the film.avi.00$i" bos12a.avi.00$i
done
```

This is what I got:
```
cp: cannot stat `this is the film.avi.001': No such file or directory
cp: cannot stat `this is the film.avi.002': No such file or directory
cp: cannot stat `this is the film.avi.003': No such file or directory
cp: cannot stat `this is the film.avi.004': No such file or directory
cp: cannot stat `this is the film.avi.005': No such file or directory
cp: cannot stat `this is the film.avi.006': No such file or directory
cp: cannot stat `this is the film.avi.007': No such file or directory
cp: cannot stat `this is the film.avi.008': No such file or directory
cp: cannot stat `this is the film.avi.009': No such file or directory

```

FWIW, I execute this script in the same directory as the files are.

Macamba

---

