---
title: "Batch file rename (with spaces in filename)"
date: 2009-07-09
forum: General Help
---

### Post by laffinet on 2009-07-09
Hi,

I'm looking for a script or one liner that lets me rename a bunch of files in a folder. The tricky bit is that the filenames contain spaces/blanks which seem to mess up any solutions that I found so far.

Original filename:

```
bla bla - blabla blabla_26_05_09.avi
```

After rename:
```
bla bla - blabla blabla.avi
```

I don't want the blanks replaced by underscores.

One suggestion I found was this:
```
for i in *; do j=`echo $i | cut -d . -f 1`; j=$j".avi"; mv $i $j; done

```

however that has problems with the blanks and I get an error message along the lines of 
```
mv: target `blabla.avi' is not a directory
```

Any ideas ? Thanks.

---

### Post by sisco311 on 2009-07-09
Try one of the GUI batch renaming apps: purrr, gprename, pyrenamer, thunar (file manager) or krename.

---

### Post by laffinet on 2009-07-09
Thanks, I will try those but I was hoping to find a script or command line solution.

---

### Post by sisco311 on 2009-07-09
Well, something like this should work:
```
find /path/to/dir -maxdepth 1 -type f -iname "*.avi" | \
while read file; do
  **echo** mv --backup=t "$file" "${file//_[0-9][0-9]_[0-9][0-9]_[0-9][0-9]/}"
done
```
(remove the **echo** to actually rename the files)

or

```
rename **-n** "s/_[0-9][0-9]_[0-9][0-9]_[0-9][0-9]//g" ./*.avi
```

---

### Post by laffinet on 2009-07-11
Thanks, worked like a charm.

---

