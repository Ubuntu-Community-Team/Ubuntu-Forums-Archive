---
title: "Problem using grep command with arrays"
date: 2010-09-05
forum: General Help
---

### Post by claymore89 on 2010-09-05
Hi,

I'm using grep to grab lines from a file.

A typical line contains the words: beet bite boot pit peach (in other words, single words separated by one space)

I want to parse this line into an array, with each word being an element of the array so array[1] = beet, array[2] = bite, etc...

How do I do this? Can someone give me an example of the requisite code. I don't want to have to manually assign the elements, is their any way to code it so that all words separated by single spaces can automatically become array elements.


Thanks.

---

### Post by lykwydchykyn on 2010-09-05
Something like this:
```

myarray=(`grep someterm somefile`)

echo ${myarray[2]}


```

Would do it.  See this reference on arrays:

[http://tldp.org/LDP/abs/html/arrays.html](http://tldp.org/LDP/abs/html/arrays.html)

---

