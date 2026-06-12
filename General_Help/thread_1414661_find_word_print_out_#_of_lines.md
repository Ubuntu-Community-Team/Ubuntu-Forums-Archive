---
title: "find word print out # of lines"
date: 2010-02-17
forum: General Help
---

### Post by dstudentx on 2010-02-17
this is driving me crazy.
How can i in the terminal, display only the first 5 lines of say dmesg

---

### Post by dstudentx on 2010-02-17
if I want to read in a text file and only output a word i wanted such as "love".  how would i do that?

---

### Post by dstudentx on 2010-02-23
How can you redirect the output of the dmesg command into a file called dmesg.txt
I cant figure it out and its driving me a little crazy

---

### Post by dstudentx on 2010-02-23
How can you display the last 5 lines of a text file

---

### Post by dstudentx on 2010-02-23
I need to search for a word say "ubuntu" and just print out the number of lines "ubuntu was found

---

### Post by kaibob on 2010-02-23
The following will do what you want. I assume the lines are in a text file.

```
grep -c string file
```

---

### Post by patchwork on 2010-02-23
If you are looking for the number of lines in a file that contain "ubuntu" you can use

```
grep -i -c "ubuntu" /path/to/file
```

or, for a list of files with the counts of "ubuntu" in each file,

```
grep -i -c "ubuntu" /path/to/directory -r
```

The -i makes the search case-insensitive
The -c calls for the count output.

However, if you are searching for the number of times "ubuntu" exists in a directory, I don't know how to display that without counting the above output...

---

### Post by dmizer on 2010-02-23
From the [Code of Conduct]("http://ubuntuforums.org/index.php?page=policy"):

> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums should not be thought of as a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.

---

