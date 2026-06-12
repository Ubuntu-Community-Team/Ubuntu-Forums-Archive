---
title: "awk change variable"
date: 2010-11-26
forum: General Help
---

### Post by wanna_try on 2010-11-26
Hi.
How to change string variable in awk?
for example, I parse with awk script text file named some_name_with_extension.txt

I want to print only some_name in my script

```
....
varCompName = FILENAME
print varCompName
```

How to put not all symbols from FILENAME to variable?
thank you
This make my day

In windows I used some of next 
```
%my_var:~0,-2%
```

would extract all but the last 2 characters of the my_var variable.

---

### Post by DaithiF on 2010-11-26
your windows example is from the windows shell rather than awk, so I wasn't sure if you specifically wanted an awk solution, or whether you just wanted a bash/linux solution and thought that awk might be good.

if the latter, you can do it directly in bash:
```
$ x=some_file.txt
$ echo ${x%.*}
some_file

$ y=some_file_with_extension.txt
$ echo ${y%_with_extension.txt}
some_file
```

if you specifically want to do it awk (as part of a larger awk script), then some variation on this:
```
echo "some_file_with_extension.txt" | awk '{ sub("_with_extension.txt", "", $0); print $0 }'
```

see [http://people.cs.uu.nl/piet/docs/nawk/nawk_122.html](http://people.cs.uu.nl/piet/docs/nawk/nawk_122.html) for more awk string functions

---

### Post by wanna_try on 2010-11-26
On [http://www.linuxquestions.org/](http://www.linuxquestions.org/) there was next reply that more complicated with my task.
> **colucix said:**
> Check the awk function **substr**. For example:
```
$ awk 'BEGIN{ my_var = "something"; print substr(my_var,1,length(my_var)-2) }'
somethi
```

Thanks for links.
I introduce awk and it really attractive for my purpose.

---

