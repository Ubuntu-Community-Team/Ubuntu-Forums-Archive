---
title: "Use sed/awk to fix a mis-formatted csv file?"
date: 2010-05-26
forum: General Help
---

### Post by lethalfang on 2010-05-26
Hi,

I have a bunch of huge .csv files that have some mis-formatted lines. 
It is supposed to contain 3 numbers in each line. Each number has 3 decimal places.
The problem is, when the program generated that .csv file, some number are too "large," such that the 3 numbers become squished together like this:
xxx.xxxyyy.yyyzzz.zzz, when it's supposed to be xxx.xxx yyy.yyy zzz.zzz

You can imagine that the .csv file can easily be fixed by inserting a space 3 characters after every decimal point. 

Anyone knows how to do that?

Thanks. Much appreciated.

---

### Post by lisati on 2010-05-26
It almost sounds like a bug in the program that produced the file - a csv file should have a comma between the values. How were the files produced?

---

### Post by lethalfang on 2010-05-26
> **lisati said:**
> It almost sounds like a bug in the program that produced the file - a csv file should have a comma between the values. How were the files produced?

Yes, there is clearly a bug in the program that produced the file. It's a molecular dynamics program that I didn't write myself. The program puts a space between the numbers, but with fixed column width. When the number of digits exceeds the column width, the numbers loses the space between them. 

I think it's easier to fix the .csv file than to fix the original program.

---

### Post by frostschutz on 2010-05-26
```

$ echo xxx.xxxyyy.yyyzzz.zzz | sed -r -e 's/([^ ]{7})/\1 /g' -e 's/  +/ /g'
xxx.xxx yyy.yyy zzz.zzz 
$ echo xxx.xxx yyy.yyy zzz.zzz | sed -r -e 's/([^ ]{7})/\1 /g' -e 's/  +/ /g'
xxx.xxx yyy.yyy zzz.zzz

```Mind the spaces in that code...

Reading your description, of course if the numbers only have three decimal places but a different length before the decimal, it won't work this way. :)

Give a real example?

---

### Post by lethalfang on 2010-05-26
> **frostschutz said:**
> ```

$ echo xxx.xxxyyy.yyyzzz.zzz | sed -r -e 's/([^ ]{7})/\1 /g' -e 's/  +/ /g'
xxx.xxx yyy.yyy zzz.zzz 
$ echo xxx.xxx yyy.yyy zzz.zzz | sed -r -e 's/([^ ]{7})/\1 /g' -e 's/  +/ /g'
xxx.xxx yyy.yyy zzz.zzz

```Mind the spaces in that code...

Reading your description, of course if the numbers only have three decimal places but a different length before the decimal, it won't work this way. :)

Give a real example?

Thanks.

The numbers may have different number of digits in front of the decimal points, but all have 3 digits after the decimal point. Numbers can be negative. 

An example would be:

111.11122222.222-3.333, in which case I want it to be
111.111 22222.222 -3.333

So one way to do it, but I don't quite know how, is to insert a space whenever there is a decimal place.
... further complicated by the "special" nature of "."

---

### Post by StuartN on 2010-05-26
> **lethalfang said:**
> So one way to do it, but I don't quite know how, is to insert a space whenever there is a decimal place.

If multiple spaces do not matter, then add a space after every ".123" pattern, and if spaces do matter then pipe that back through sed to replace double spaces with single spaces.

```
echo 012.345678.901234.567 | sed "s/\(\.[0-9]\{3\}\)/\1 /g"
012.345 678.901 234.567 

```

---

### Post by lethalfang on 2010-05-26
> **StuartN said:**
> If multiple spaces do not matter, then add a space after every ".123" pattern, and if spaces do matter then pipe that back through sed to replace double spaces with single spaces.

```
echo 012.345678.901234.567 | sed "s/\(\.[0-9]\{3\}\)/\1 /g"
012.345 678.901 234.567 

```

Yep, this is exactly what I was looking for.
Thanks!

---

