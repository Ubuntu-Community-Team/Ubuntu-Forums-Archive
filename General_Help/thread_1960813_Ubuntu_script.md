---
title: "Ubuntu script"
date: 2012-04-18
forum: General Help
---

### Post by Drenriza on 2012-04-18
Hi guys.

I have a xml file that is constructed as follows.
```
<stbs>
        <stb>
                <id>1</id>
                <unit-number>0999</unit-number>
                <room-number>999</room-number>
                <nc-unit>nc106</nc-unit>
                <channel-number>3</channel-number>
                <duration>1800</duration>
                <max-volume>25</max-volume>
        </stb>
        <stb>
                <id>2</id>
                <unit-number>0888</unit-number>
                <room-number>888</room-number>
                <nc-unit>nc107</nc-unit>
                <channel-number>3</channel-number>
                <duration>1800</duration>
                <max-volume>25</max-volume>
        </stb>
</stbs>
```

My question is. What is an easy way to get the information from where id equals 1 or 2?
With Bash, AWK or Sed?

Thanks on advance.
Kind regards.

---

### Post by HiImTye on 2012-04-18
bash is a shell, while awk and sed are tools to use within a shell. bash is the default shell for most Ubuntu distros

awk and sed can be used in the same ways, it is mainly how you prefer to use them that differs

[awk]("http://www.gnu.org/software/gawk/manual/gawk.html")
[sed]("http://www.gnu.org/software/sed/manual/")

you can also use tools such as grep to achieve the same results, it is all how you want to write

---

### Post by iponeverything on 2012-04-18
grep -A6 \<id\>[1,2] xml.file

---

### Post by Drenriza on 2012-04-18
> **iponeverything said:**
> grep -A6 \<id\>[1,2] xml.file

Thanks :p! Is their also a way to grab the data between the two >date< fields. So the output is

1
0999
999
nc106
3
1800
25

Thanks on advance

---

### Post by iponeverything on 2012-04-18
```
grep -A6 \<id\>[1,2] xml.file | awk -F\> '{print $2}'|awk -F\< '{print $1}'
```

There are better ways to do it..

---

### Post by Vaphell on 2012-04-18
<id>[12] is too broad, it will match any 1.* and 2.*

```
grep -A6 '<id>[12]</id>' xml.file | sed -r 's/.*>(.*)<.*/\1/'
```

---

### Post by HiImTye on 2012-04-18
```
grep -A6 '<id>[0-9]\{1,3\}</id>' file.xml | sed -r 's/.*([a-zA-Z-].*)>(.*)<.*/\1: \2/' > out.file
```should format it like
```
id: 1
unit-number: 0999
...
```for any ID from 0-999

---

### Post by iponeverything on 2012-04-19
> **Vaphell said:**
> <id>[12] is too broad, it will match any 1.* and 2.*

```
grep -A6 '<id>[12]</id>' xml.file | sed -r 's/.*>(.*)<.*/\1/'
```

thanks, I didn't notice that. I should have narrowed it..

```
grep -A6 \<id\>[1,2]\< xml.file 
```

---

### Post by Vaphell on 2012-04-19
you also don't separate characters enumerated in [] with commas ;-)

```
$ echo $'<id>1</id>\n<id>,</id>\n<id>2</id>' | grep '>[1,2]<'
<id**>1<**/id>
<id**>,<**/id>
<id**>2<**/id>
``` [1-2] if that was supposed to be a range :)

---

### Post by iponeverything on 2012-04-19
back, back in day I learned that [n-n] was a range and [n,n,n] meant n or n or n..

thanks again - in test case I used didn't have <id>,<id> so I didn't catch it..

---

