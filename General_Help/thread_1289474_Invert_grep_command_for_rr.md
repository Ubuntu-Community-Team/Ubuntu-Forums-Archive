---
title: "Invert grep command for \r\r"
date: 2009-10-12
forum: General Help
---

### Post by Forcenet on 2009-10-12
This is probably an easily answerable question and I just don't have enough Grep experience to do it.

I have a text file which needs to be reformatted in a specific way. I need to be able to grep through it and find all lines not matching two carriage returns. I can grep these lines but don't know how to invert the search. I do grep \r\r. (grep ^\r\r and grep ^\r+^\r and grep ^[\r\r] all do not work].

Thanks in advance,
Alain

---

### Post by samuelhug on 2009-10-12
```
grep -v
```
returns all lines that dont match

---

### Post by darthmob on 2009-10-12
Did you have a look at the [man page for grep]("http://www.linuxmanpages.com/man1/grep.1.php")?

---

### Post by Giblet5 on 2009-10-12
Also be aware that '\r' is not a newline character. It's just a carriage return.

DOS uses \r\n as end of line.

Unix and act-alikes use \n. Grep cannot match data from two lines, so grep -v '\n\n' will NOT work.

Maybe what you really want is "cat -s".

---

