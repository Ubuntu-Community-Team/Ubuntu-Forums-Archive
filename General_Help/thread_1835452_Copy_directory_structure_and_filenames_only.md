---
title: "Copy directory structure and filenames only"
date: 2011-08-29
forum: General Help
---

### Post by byb3 on 2011-08-29
Hi,

How do I recursively copy a directory structure, but without copying the files, just the filenames?

for example, a.jpg will still be copied, but in the new directory it would be 0 bytes.

If there is a bash script that does the same job I'd really appreciate it if someone could post an example?

Thanks,

---

### Post by sisco311 on 2011-08-29
Try something like:
```

#!/bin/bash

# path to the source and dest directories 
source="$HOME/source"
dest="$HOME/dest"

# exit if dest can't be created 
mkdir -p "$dest" || exit 1

# exit if source doesn't exist or can't be accessed
# otherwise cd ito it
cd "$source" || exit 1

# remove dotglob if you don't want to operate on hidden (.file) files
shopt -s nullglob globstar dotglob
for file in **/*
do
    if [ -d "$file" ]
    then
        mkdir -p "$dest/$file"
    else
        > "$dest/$file"
    fi
done

```

---

### Post by seawolf167 on 2011-08-29
You can copy the directory tree via rsync (but not the filenames without their data as far as I know).

```
rsync -av -f"+ */" -f"- *" source/ destination/
```

---

### Post by byb3 on 2011-08-29
> **sisco311 said:**
> Try something like:
```

#!/bin/bash

# path to the source and dest directories 
source="$HOME/source"
dest="$HOME/dest"

# exit if dest can't be created 
mkdir -p "$dest" || exit 1

# exit if source doesn't exist or can't be accessed
# otherwise cd ito it
cd "$source" || exit 1

# remove dotglob if you don't want to operate on hidden (.file) files
shopt -s nullglob globstar dotglob
for file in **/*
do
    if [ -d "$file" ]
    then
        mkdir -p "$dest/$file"
    else
        > "$dest/$file"
    fi
done

```

[Thankyou sisco311]("http://ubuntuforums.org/member.php?u=244665"), this works beautifully!

---

