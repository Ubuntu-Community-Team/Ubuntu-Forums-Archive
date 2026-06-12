---
title: "how to use grep command to get what i want?"
date: 2010-03-31
forum: General Help
---

### Post by luofeiyu on 2010-03-31
there  is a file /home/pt/test.txt,the content is :
1 require 'rubygems'
2 require 'hpricot'
3 require 'open-uri'

4 doc = Hpricot(open('http://www.google.com/search?q=ruby'))
5 links = doc/"//a[@class=l]"
6 links.map.each {|link| puts link.attributes['href']}
what i want is :
require 'rubygems'
require 'hpricot'
require 'open-uri'

doc = Hpricot(open('http://www.google.com/search?q=ruby'))
links = doc/"//a[@class=l]"
links.map.each {|link| puts link.attributes['href']}
how to write a grep cmmand or other command to get what i want ?

---

### Post by Ahadiel on 2010-03-31
```
cat /home/pt/test.txt | grep "require"
```

Unless of course I misinterpreted what you were asking.

---

### Post by john newbuntu on 2010-03-31
It appears like you just need the text without numbers if I am not mistaken:
cut -f2- -d' ' /home/pt/test.txt

---

### Post by Ahadiel on 2010-03-31
> **john newbuntu said:**
> It appears like you just need the text without numbers if I am not mistaken:
cut -f2- -d' ' /home/pt/test.txt

Ah, guess I didn't read his entire post.

---

### Post by luofeiyu on 2010-04-01
cut -f2- -d' ' /home/pt/test.txt
it's ok 
think you

---

