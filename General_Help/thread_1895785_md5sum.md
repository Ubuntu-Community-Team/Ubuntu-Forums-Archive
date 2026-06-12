---
title: "md5sum"
date: 2011-12-15
forum: General Help
---

### Post by radu992 on 2011-12-15
How can I md5sum a string in the terminal? I don't want to know for files or archives only for a string of characters, for example my name.

---

### Post by seawolf167 on 2011-12-15
[Here ]("https://help.ubuntu.com/community/HowToMD5SUM")is the Ubuntu Community Documentation on how to MD5SUM. MD5Summing is a way to check data integrity, so preforming it on a string and not a file wouldn't help anything.

---

### Post by Slim Odds on 2011-12-15
> **radu992 said:**
> How can I md5sum a string in the terminal? I don't want to know for files or archives only for a string of characters, for example my name.

```
0> echo "radu992" | md5sum
9e85fc697bc874f211f41e319b8ee884 *-

```

---

### Post by radu992 on 2011-12-15
I know how to do that, I asked about a string of characters not files. Please can someone help me?

---

### Post by seawolf167 on 2011-12-15
> **radu992 said:**
> I know how to do that, I asked about a string of characters not files. Please can someone help me?

See Slim Odds' post above

---

### Post by sisco311 on 2011-12-15
In bash, I'd use a here string:
```
md5sum <<< "radu992"
```
In a POSIX shell, a here document:
```
md5sum << EOF
radu992
EOF
```

---

