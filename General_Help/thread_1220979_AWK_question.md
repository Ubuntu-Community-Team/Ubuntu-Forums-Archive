---
title: "AWK question"
date: 2009-07-23
forum: General Help
---

### Post by yaazz on 2009-07-23
I am trying to write an awk program that will look for two blank lines, and then grab all lines until there is another blank one. 

This can happen more then once 

This is where the input is coming from
w3m 'http://www.totousa.com/ProductDetail/tabid/75/Default.aspx?ProductId=39823d12-d23c-42a9-bae4-0a3195c653a2&SearchId=271c67aa-4f37-4581-86db-bf9ca853cee4'

I am not very familliar with AWK, and if someone could help me out with this that would be great!

---

### Post by DaithiF on 2009-09-25
bit late to this one, but using sed rather than awk, something like:
```
sed -n '1h;1!H;x;/^\n\n.*\n$/{s/\n\n\(.*\)\n$/\1/;p;x};/^\n/x' somefile
```

---

