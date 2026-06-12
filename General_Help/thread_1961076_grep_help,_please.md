---
title: "grep help, please"
date: 2012-04-18
forum: General Help
---

### Post by Diametric on 2012-04-18
Hello,

I have a samba log file I'm trying to pull data from (/var/log/samba/log.combined).  Specifically, I am trying to pull all lines from the file where a specific IP is mentioned

```
less log.combined | grep 10.1.4.* > file1
```However, this particular log file actually has two lines per data instance.  Example:

```
[2012/04/12 03:03:46, 3] nmbd/nmbd_incomingrequests.c:process_name_query_request(454)
process_name_query_request: Name query from 10.1.4.54 on subnet 10.1.0.115 for name WPAD<00>
```

So, my grep returns data from the third line, but I also need the first line to know when said IP attempted access.  How do I pull this off?

Thanks!

---

### Post by Lars Noodén on 2012-04-18
Try this:

```

grep 10.1.4 log.combined > file1

```

Can you show a few sample lines from the log file?

---

### Post by Diametric on 2012-04-18
It's there, I just didn't wrap code filter around the instance.

---

### Post by Lars Noodén on 2012-04-18
There should be a way to use awk to grab a line with a pattern along with the preceding line.

---

### Post by Diametric on 2012-04-18
Thanks for your replies - I just don't know enough about awk to pull that off in a reasonable amount of time.  Hell...I'm proud I was able to get that grep command to work!

---

### Post by Vaphell on 2012-04-18
grep -B2 ...
-Bn include n lines before matching line 
-An include n lines after matching line

example
```
$ echo $'1\n2\n3\n4\n5'
1
2
3
4
5
$ echo $'1\n2\n3\n4\n5' | grep -A2 '3'
3
4
5
$ echo $'1\n2\n3\n4\n5' | grep -B2 '3'
1
2
3
$ echo $'1\n2\n3\n4\n5' | grep -B1 -A1 '3'
2
3
4
```

---

### Post by Diametric on 2012-04-18
> **Vaphell said:**
> grep -B2 ...
-Bn include n lines before matching line 
-An include n lines after matching line

Perfect!  Thank you so much, I have exactly what I was looking for.

Cheers.

---

### Post by Lars Noodén on 2012-04-18
> **Vaphell said:**
> grep -B2 ...
-Bn include n lines before matching line 
-An include n lines after matching line


That's awesome!

---

