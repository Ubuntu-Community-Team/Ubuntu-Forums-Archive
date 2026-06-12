---
title: "shell scripting command doubt"
date: 2011-01-01
forum: General Help
---

### Post by jsriz on 2011-01-01
How do i find out if a particular item is a file or a folder through the terminal ls -la gives 'd' before the permissions for every folder and '-' before every file
Like i want to write a script that backup data if it is a folder and deletes if it is a file

---

### Post by sisco311 on 2011-01-01
Try something like:
```

file="path/to/file"
if [ -d "${file}" ]; then
  echo "${file}" is a directory.
elif [ -f "${file}" ]; then
  echo "${file}" is a regular file.
else
  echo neither a directory nor a regular file.
fi
```

See:```
man bash | less +/"^CONDITIONAL EXPRESSIONS"
```

---

### Post by AlphaLexman on 2011-01-01
Another option using the 'ls' command...
```
ls --file-type
```
will append an indicator after each entry.

---

