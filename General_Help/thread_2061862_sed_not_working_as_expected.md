---
title: "sed not working as expected"
date: 2012-09-23
forum: General Help
---

### Post by geohei on 2012-09-23
Hi.

Why is this not working?

```
root@vm90:~# cat test.txt
line 1
line 2
line 3
line 4
root@vm90:~# sed "s/\n/,/g" test.txt
line 1
line 2
line 3
line 4
```

My intention was to get:

```
root@vm90:~# cat test.txt
line 1
line 2
line 3
line 4
root@vm90:~# sed "s/\n/,/g" test.txt
line 1,line 2,line 3,line 4,
```

What did I do wrong?

Thanks

---

### Post by steeldriver on 2012-09-23
Unless you use the 'N' command to glom lines together, sed doesn't match across multiple lines

---

### Post by The Cog on 2012-09-23
Yup. sed likes to treat each line separately. 

You could use tr instead, like this:
> cat test.txt | tr -d '\n'

---

### Post by steeldriver on 2012-09-23
to replace the newlines (rather than just delete them) I think that would be

```
cat test.txt | tr '\n' ','
```... or (for the cat haters)

```
tr '\n' ',' < test.txt
```A real hairy-chested sedhead would probably do

```
sed -e :a -e '$!N;s/\n/,/;ta' test.txt
```

---

### Post by sisco311 on 2012-09-23
> **The Cog said:**
> Yup. sed likes to treat each line separately. 

You could use tr instead, like this:


[demoggification]

You mean like this:
```

tr '\n' \, < test.txt
```

[/demoggification]

:)

---

