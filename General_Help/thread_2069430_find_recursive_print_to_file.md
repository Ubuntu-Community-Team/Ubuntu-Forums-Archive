---
title: "find recursive print to file?"
date: 2012-10-10
forum: General Help
---

### Post by sohlinux on 2012-10-10
Hi,

How can I find all *.txt files in the current folder and print a list of them to a file text_files.txt then pipe it to send an email

find -type f -name "*.txt"  -print > text_files.txt | tail -100 /home/text_files.txt | mail -s "text_files.txt" [email]my@email.com[/email]

this only works in 2 parts, how can I make it work in one line of code? the above says Null message body; hope that's ok

---

### Post by Vaphell on 2012-10-10
you shouldn't use > and | at the same time
> dumps the output to the file, but | assumes that the output should go as input of the next command in chain. Long story short mixing > and | in this way is nonsense.

```
find ... | tail -100 | mail -s ...
```

if you wanted to use intermediary files, you'd have to properly separate commands with ; or &&

---

### Post by sohlinux on 2012-10-11
-bash: -print: command not found
Null message body; hope that's ok

tail: cannot open `text_files.txt' for reading: No such file or directory
Null message body; hope that's ok

:(

---

### Post by Lars Noodén on 2012-10-11
You have to drop the redirect and reference to the file and use just the pipes he showed.

```

find -type f -name "*.txt" -print | tail -100 | mail -s "text_files" my@email.com

```

---

### Post by sohlinux on 2012-10-11
> **Lars Noodén said:**
> You have to drop the redirect and reference to the file and use just the pipes he showed.

```

find -type f -name "*.txt" -print | tail -100 | mail -s "text_files" my@email.com

```

thanks :)

---

### Post by Lars Noodén on 2012-10-12
Just as a follow up, you can look at the examples below to see the difference between pipes and redirects.

```

# a
ls /usr/bin

# b
ls /usr/bin > /tmp/foo
less /tmp/foo

# c
sort -r < /tmp/foo
sort -r < /tmp/foo | less

# d
ls /usr/bin | sort -r | less


```

They're what give much of the power to the shell.

---

