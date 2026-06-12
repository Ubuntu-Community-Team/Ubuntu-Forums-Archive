---
title: "Print multiple .doc-files"
date: 2010-06-12
forum: General Help
---

### Post by smain on 2010-06-12
Hi all

I often have a need for printing multiple files. Therefore I found a Nautilus script that would allow me to do this. However often many of the files a Microsoft Office doc-files. Since I do not really want to convert every single file (as that would defeat the purpose of bundle printing) I tried to figure out how to print these, as the commands "lpr" og "cupsdoprint" cannot process these. I have found a printing command using the CLI part of OpenOffice, but I cannot get it to do multiple selected files.

The command is:
```
soffice -p "/path/of/file.doc" 
```How can I use this in a Nautilus Script so I can print multiple files?

Smain

---

### Post by ateholiz on 2010-09-02
Try a script with this in it:

```

#!/bin/bash
#
quoted=$(echo -e "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" | awk 'BEGIN {FS = "\n" } { printf "\"%s\" ", $1 }' | sed -e s#\"\"##)
eval "ooffice -p $quoted"
```The "quoted..." line should handle multiple files (with spaces!) 
[SIZE=1]I got the multiple file part from a script I found on the net, but I can't seem to find the script's author.[/SIZE]:oops:

---

