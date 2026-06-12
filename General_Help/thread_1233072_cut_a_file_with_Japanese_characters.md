---
title: "cut a file with Japanese characters"
date: 2009-08-06
forum: General Help
---

### Post by mbroek2004 on 2009-08-06
Hi,

Is there a way to cut a text file that consists of several columns; some columns containing English text and some columns containing Japanese characters.

I tried to use 'cut' using the following parameters to cut out columns 12 through 14.

**cut -f 12-14 {filename1} > {filename2}**

The program respons back with the following error though:

*cut: {filename1}: Illegal byte sequence*

I suspect it has something to do with the Japanese characters that cut can not deal with. I found out that {filename1} has a 'Unicode UTF-16 Little Endian' character encoding scheme.


Anyway, is there a way to cut up a file into columns even though some columns contain Japanese characters?

Thanks, M

---

