---
title: "How to escape expression evaluation when wring a text to a file using a script?"
date: 2012-05-29
forum: General Help
---

### Post by legolas_w on 2012-05-29
Hi,

I need some help with adding text to a file. My text contains shell variables like $server_name I want the exact server name to be inserted into the file and not it's equivalent text. I mean I dont want the variable to be evaluated and the evaluation result be written into the file.

Foe example:

```

server_name="my_server_name_here"
cat <<EOF >> .server_script
set secondary_path=$server_name/secondary/directory

```

I want the following to be written in the .server_script 

```

set secondary_path=$server_name/secondary/directory

```

but instead I get the following one.
```

set secondary_path=my_server_name_here/secondary/directory

```


Any idea how to fix it?

Thanks.

---

### Post by sisco311 on 2012-05-29
If you quote any character in word (EOF), then the here document lines arn't expanded: 

```

cat << \EOF >> file
text=$var
EOF

```

or you can escape the $ characters in the text:

```
cat << EOF >> file
text=\$var
EOF

```
See: ```
man bash | less +/' +Here Documents'
```

---

### Post by legolas_w on 2012-05-30
Thanks, using \ solved the issue.

---

