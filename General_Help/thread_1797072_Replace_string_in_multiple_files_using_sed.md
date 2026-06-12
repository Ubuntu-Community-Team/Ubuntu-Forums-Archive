---
title: "Replace string in multiple files using sed"
date: 2011-07-04
forum: General Help
---

### Post by tomeus on 2011-07-04
Hi guys, I am trying to replace a string (url) in 100s of files located in different directories.

I found the sed command but cannoy get it to work. First I locate the files that have the string in them:

```
grep -ilr 'url' *
```this works correctly and displayed the location of the files that have the string:

```
1/index.php
2/index.php
```Now I need to replace the string so I combined it with sed:

```
grep -ilr ‘url’ * | xargs -i@ sed -i ‘s/url/url-new/g’ @
```it returns no error but also it doesn't changes the string

Any help would be appreciated

---

### Post by gmargo on 2011-07-04
Try this instead.  Note the standard single quotes.  Note -d option so that pathnames with spaces in them will still work.  No need to use '@' in this case.
```

grep -ilr 'url' * | xargs -d '\n' sed -i 's/url/url-new/g'

```Or, if you prefer using the NULL between pathnames:
```

grep -ilr --null 'url' * | xargs --null sed -i 's/url/url-new/g'

```

---

### Post by sisco311 on 2011-07-04
Using grep & sed is redundant. In sed you can do something like: 
```
sed '/PATTERN/s/FOO/BAR/g' file
```
(If the line contains PATTERN, do the substitution). But if PATTERN is the same as FOO, then obviously it can be omitted.

Also, sed is a stream editor, for editing files, I would use [ed]("http://wiki.bash-hackers.org/howto/edit-ed").

In bash, you can try something like:
```

while IFS= read -d '' -r file
do
  ed -s -- "${file}" <<< $',s/url/new-url/g\nw'
done < <(find path/to/dir -type f -print0)
```

You can test it with:
```

while IFS= read -d '' -r file
do
  echo "${file}:"
  ed -s -- "${file}" <<< $'H\n,s/url/new-url/g\n**,p**'
done < <(find path/to/dir -type f -print0)
```

On, and it's always a good idea to keep some backups around. ;)

EDIT: Welcome to the forums!

---

### Post by tomeus on 2011-07-05
Thank you guys, both of your methods worked!

I am very new to Ubuntu and Linux in general so I appreciate your help and guidance.

I need to look why the @ option was not needed

Thank you again!

---

