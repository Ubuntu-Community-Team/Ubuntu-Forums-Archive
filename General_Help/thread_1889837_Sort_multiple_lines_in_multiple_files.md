---
title: "Sort multiple lines in multiple files"
date: 2011-12-02
forum: General Help
---

### Post by HeXor0815 on 2011-12-02
Hello everyone!

I have multiple files, each containing multiple lines. Now I want to sort these lines in each file.

Usually I am using EMACS to edit *.txt files, where you can easily use M-x sort-lines to sort the lines. But now I would like to do use this on many (!!!) files and don't want to open each file manually.

Does someone have a clue how this could work? Do I really need to read and sort each line, or is there some kind of command which can be used on a file from a bash script like the EMACS intern function?

Thanks in advance!

---

### Post by tjoff on 2011-12-02
Yes, it is called "sort" :)

```
sort unsorted_file.txt -o sorted_file.txt
```

You can then make a script that loops over all the files you want to sort.

---

### Post by Lars Noodén on 2011-12-02
> **tjoff said:**
> Yes, it is called "sort" :)

```
sort unsorted_file.txt -o sorted_file.txt
```

You can then make a script that loops over all the files you want to sort.

I checked and you don't need to have a different name for the sorted file.  So you could do it like this:

```

sort *file.txt* -o *file.txt*

```

---

### Post by HeXor0815 on 2011-12-02
Wow its really that simple? Ok I will test it, thank you!

---

