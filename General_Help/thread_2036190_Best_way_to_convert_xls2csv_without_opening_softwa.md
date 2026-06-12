---
title: "Best way to convert xls2csv without opening software"
date: 2012-08-01
forum: General Help
---

### Post by cheerPuncH on 2012-08-01
Hi,

What is the best way to convert xls2csv without opening software such as excel and open office? I've tried unix's catdoc sub funtion xls2csv, but it throws and OLE error. I've also tried using a python module called  pyExcelerator that has a xls2csv converter, but won't (for some reason work on remote, only local).

[http://ubuntuforums.org/showthread.php?t=2035893](http://ubuntuforums.org/showthread.php?t=2035893)

I haven't tried a CPAN module, but it seems I'm heading in that direction.
Edit! Now I have tried CPAN. I followed the instructions on this site [http://robertborkowski.com/techblog/convert-xls-to-csv-in-command-line.html](http://robertborkowski.com/techblog/convert-xls-to-csv-in-command-line.html), but I get this error
```
Can&#8217;t use an undefined value as an ARRAY reference at /usr/local/bin/xls2csv line 139.
``` 

I looked at the code and the variable they are referring to $Sheet is defined as a global. I'm not sure what is wrong.

I thought this would be really easy, but it has turned into a very frustrating process.

Thanks in Advance!

---

