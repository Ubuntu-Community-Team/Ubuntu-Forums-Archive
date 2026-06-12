---
title: "How to merge different text files to a single text file"
date: 2009-07-11
forum: General Help
---

### Post by mrakesh85 on 2009-07-11
I am having text files which contain names in alphabetical order. each text file contain different different names there wont be any  repetitions . Can I merge all the names in different text files to a single text file with names in alphabetical order

---

### Post by sshannin on 2009-07-11
```
cat file1 file2 file3 fileN | sort >new_file_name
```

To explain, you list all the files, then sort the entries, then write to a new file.

---

### Post by DGortze380 on 2009-07-11
> **mrakesh85 said:**
> I am having text files which contain names in alphabetical order. each text file contain different different names there wont be any  repetitions . Can I merge all the names in different text files to a single text file with names in alphabetical order

```

cat file2.txt >> file1.txt
sort file1.txt

```

---

### Post by Slim Odds on 2009-07-11
> **sshannin said:**
> ```
cat file1 file2 file3 fileN | sort >new_file_name
```To explain, you list all the files, then sort the entries, then write to a new file.

Or, if the files really have common names:```
cat file* | sort > new_file.txt
```

---

### Post by mrakesh85 on 2009-07-11
Thank you very much for ur replys, they are helpful 

Rakesh

---

