---
title: "Adding a string of text from bash to a config file"
date: 2010-07-14
forum: General Help
---

### Post by iMetaphysikz on 2010-07-14
Hi I'm trying to get BASH to write a line into a config file (/etc/fstab).

I currently have this code:
```
sed '2 a\ Add this line after 2nd line' /etc/fstab
```but this doesn't write to the file it just prints it in to terminal. I've heard that cat can be combined with sed to write to this file but lost on how to do this?

any help would be greatly appreciated.

---

### Post by dcstar on 2010-07-14
> **iMetaphysikz said:**
> Hi I'm trying to get BASH to write a line into a config file (/etc/fstab).

I currently have this code:
```
sed '2 a\ Add this line after 2nd line' /etc/fstab
```but this doesn't write to the file it just prints it in to terminal. I've heard that cat can be combined with sed to write to this file but lost on how to do this?

any help would be greatly appreciated.

This appends to the end of the file called "filename":
```
> filename
```

---

### Post by sisco311 on 2010-07-14
```
sed -i.backup '2 a\Add this line after 2nd line' path/to/file
```

See:
```
man sed | less +/"-i\[SUFFIX\]"
```

---

### Post by WorMzy on 2010-07-14
> **dcstar said:**
> This appends to the end of the file called "filename":
```
> filename
```

Er. > is replace. >> is append.

Example:
```
echo "hello" >> example.txt
```
Adds "hello" to the end of example.txt

EDIT: Oh, you meant for use with sed. Never mind then. :)

---

### Post by iMetaphysikz on 2010-07-14
> **sisco311 said:**
> ```
sed -i.backup '2 a\Add this line after 2nd line' path/to/file
```See:
```
man sed | less +/"-i\[SUFFIX\]"
```


Thanks this solution worked for me.

Also thanks everybody else for the input.

---

### Post by sisco311 on 2010-07-14
> **iMetaphysikz said:**
> Thanks this solution worked for me.

Also thanks everybody else for the input.

You're welcome!


Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

Thanks.

---

