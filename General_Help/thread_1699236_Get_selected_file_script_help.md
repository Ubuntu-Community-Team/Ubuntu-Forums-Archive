---
title: "Get selected file script help"
date: 2011-03-03
forum: General Help
---

### Post by false_chicken on 2011-03-03
I am trying to create an option in the right click menu to append the currently selected file/folder to a text file that a script will read later and delete the files in the list. Is there a way I can do that? I know how to write a script to read the text file and delete the list but I don't know how/if you can get the currently selected file with a script. Is that possible?

---

### Post by sisco311 on 2011-03-03
You didn't specify it, but, I guess that you are trying to write a Nautilus script in bash.

From [http://g-scripts.sourceforge.net/faq.php](http://g-scripts.sourceforge.net/faq.php)

[i]There are a couple of other useful things to know. When a script is invoked, Nautilus sets a few environment variables that can be used by the script:
NAUTILUS_SCRIPT_SELECTED_FILE_PATHS:
newline-delimited paths for selected files (only if local)
NAUTILUS_SCRIPT_SELECTED_URIS:
newline-delimited URIs for selected files
NAUTILUS_SCRIPT_CURRENT_URI:
current location
NAUTILUS_SCRIPT_WINDOW_GEOMETRY
position and size of current window

The selected files can also be referred to with the more traditional "$@" and "$*" bash variables.[/i]

So you could do something like:
```
echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" >> path/to/list
```

The problem with this approach is that filenames can contain any character (including a newline) except a slash or a null character.

So if you want to write a robust script which will work with any possible filename, you have to separate the names with a null character.

Something like:
```
#!/usr/bin/env bash

for file in "$@"; do    #or simply: `for file; do'
  printf "%s\0" "$file"
done >> path/to/list

```

Then, to delete the files:
```

while IFS= read -rd '' file; do
  echo rm -rf -- "$file"
done < path/to/list

```

---

