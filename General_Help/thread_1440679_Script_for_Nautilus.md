---
title: "Script for Nautilus"
date: 2010-03-27
forum: General Help
---

### Post by oaxacamatt1 on 2010-03-27
Hi All,
I was wondering if it is possible to write a script for nautilus (or even it is 'best' in nautilus) that allows me to highlight a ton of files and then make a folder for them in the same directory and also let me name it or date the file?

For example, I am working with SAS and it spews out a ton of .htm to /home/me/sas that I would like to keep and check over later.  

If so how would you go about it?

Alternatively, if anyone is feeling generous...
Cheers,
M

---

### Post by kaibob on 2010-03-27
> **oaxacamatt1 said:**
> Hi All,
I was wondering if it is possible to write a script for nautilus (or even it is 'best' in nautilus) that allows me to highlight a ton of files and then make a folder for them in the same directory and also let me name it or date the file?

It's not entirely clear to me what you want the Nautilus script to do--especially when you say you want to "date the file."

Anyways, the following Nautilus script prompts you for the name of a directory, creates that directory within the directory that contains the highlighted files, and then copies the highlighted files to the new directory. The script makes use of a zenity dialog, which is not installed by default but is in the repos's.  You may want to add some provision in case a file to be copied into the new directory already exists. The cp command has an archive option that might be usable depending on your needs. 

```
#!/bin/bash

cd "${NAUTILUS_SCRIPT_SELECTED_FILE_PATHS%/*}"

dir=$(zenity --entry --width=300 --title "Directory Name" --text "Enter Directory")
[ "$dir" ] || exit 1

mkdir -p "$dir"

cp "$@" "$dir"
```

---

### Post by oaxacamatt1 on 2010-03-28
Very Cool dude.  I'll give it a try as soon I have time.
U da man,
M

---

