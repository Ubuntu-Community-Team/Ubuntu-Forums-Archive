---
title: "How scan if there's a subfolder in a folder ?"
date: 2010-06-27
forum: General Help
---

### Post by alien-377h on 2010-06-27
I have a small bash script that compress all folders in a specific folder

The script also:
- add a password to the compressed files
- delete the original folder after compression

Suppose that this script is called "rar.sh".


At some particular moment, there will not have any folder in the specific folder since they have all been compressed.

I want something (a script?) that will check (every minute approximately) if there's new folder in the specific folder.

If there's new folder, then execute script rar.sh

or if there's not new folder, then re-scan in the next minute.


Does anyone know how to make this?

---

### Post by stderr on 2010-06-27
Many ways; here's the simplest one I can think of (pretty inefficient - you can probably improve on this):

```

[COLOR="Blue"]#!/bin/bash[/COLOR]

[COLOR="Blue"]# Run ad infinitum[/COLOR]
while [ 1 ] ; do
[COLOR="Blue"]  # Iterate through every file/dir in your path (alter for the right path)[/COLOR]
  for f in path/to/dir/* ; do
[COLOR="Blue"]    # Test to see if this is a directory[/COLOR]
    if [ -d "$f" ] ; then
[COLOR="Blue"]      # Is a directory - execute your script (alter this to meet you needs)[/COLOR]
      rar.sh "$f"
    fi
  done
[COLOR="Blue"]  # Wait 1 minute[/COLOR]
  sleep 60
done

```

---

### Post by alien-377h on 2010-06-27
Thanks for this stderr

it's really useful :)

---

