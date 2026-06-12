---
title: "Method required to remove all spaces from a paragraph!"
date: 2009-07-20
forum: General Help
---

### Post by Rytron on 2009-07-20
Hi.
Does someone know of a command / script that would remove all spaces from a paragraph or a line? For example this:

[COLOR="DarkGreen"]The quick brown fox jumps over the lazy dog[/COLOR]

would become this:

[COLOR="Navy"]Thequickbrownfoxjumpsoverthelazydog[/COLOR]

Thanks.

---

### Post by fragos on 2009-07-20
The command line tool is "sed". "info sed" will provide you with directions on it's use.

---

### Post by kaibob on 2009-07-20
Awk and sed will do what you want:

```
echo "The quick brown fox jumps over the lazy dog." | awk '{ gsub(/ /,"") } { print }'
```

```
echo "The quick brown fox jumps over the lazy dog." | sed 's/ //g'
```

---

### Post by Rytron on 2009-07-21
> **kaibob said:**
> Awk and sed will do what you want:

```
echo "The quick brown fox jumps over the lazy dog." | awk '{ gsub(/ /,"") } { print }'
```

```
echo "The quick brown fox jumps over the lazy dog." | sed 's/ //g'
```

Awesome. Thanks guys.

---

