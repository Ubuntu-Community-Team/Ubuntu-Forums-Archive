---
title: "Extract column separated by ,"
date: 2010-06-01
forum: General Help
---

### Post by dragos2 on 2010-06-01
I have a csv file in this format:
```

1,characterswithnospace
2,same
...
4545,characters

```I want to extract only the strings after the comma, please suggest a way.

---

### Post by BoneKracker on 2010-06-01
If I have understood your description of the file correctly:
```
sed -r 's/^[0-9]+, *//' myfile
```
Or, if you would like to capture that in a file:
```
sed -r 's/^[0-9]+, *//' oldfile > newfile
```
Or, if you would like to make the changes in the original file and save a backup with .bak extension:
```
sed -i.bak -r 's/^[0-9]+, *//' testfile
```
You can ommit the backup like so, but it's not recommended:
```
sed -i'' -r 's/^[0-9]+, *//' testfile
```

---

### Post by StuartN on 2010-06-01
```
cut -d "," -f 2 file.csv
```

-d sets the field delimiter, -f is followed by a field list.

---

### Post by BoneKracker on 2010-06-01
> **StuartN said:**
> ```
cut -d "," -f 2 file.csv
```

-d sets the field delimiter, -f is followed by a field list.
```

1,characterswithnospace
2,same
...
4545, characters
```

Cut would be preferable to sed (which is larger), except cut won't strip the leading spaces that apparently exist at the beginning of _some_ of the data, as shown in the 4545 line in his sample data (assuming the sample data set is accurate, and that the spaces should be stripped).

---

### Post by dragos2 on 2010-06-01
Thank you all. It was a typo, there is no space between the comma and string.

And here are the results:
```

$ time sed -r 's/^[0-9]+, *//' oldfile > newfile

real    0m1.350s
user    0m0.840s
sys    0m0.520s

$ time cut -d "," -f 2 file.csv > newfile

real    0m0.229s
user    0m0.040s
sys    0m0.190s

```

Thanks BoneKracker and StuartN :)

---

