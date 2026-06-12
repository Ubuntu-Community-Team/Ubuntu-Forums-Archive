---
title: "Bash script"
date: 2010-05-16
forum: General Help
---

### Post by mikewhatever on 2010-05-16
open a text editor. ;)

---

### Post by ibuclaw on 2010-05-16
Open a text editor, have the top line read:
```
#!/bin/bash
```
And then program the rest of the script below it.

Once done, save and mark as executable:
```
chmod +x file.sh
```
Then test/run
```
./file.sh
```


Once you've tested the script and it works perfect to how you designed it, you can optionally choose to install it so that it appears in your shell's PATH.

```

mkdir ~/bin
install file.sh ~/bin

```
or to install somewhere accessible for all users.
```

sudo install file.sh /usr/local/bin

```

Regards
Iain

---

### Post by kerry_s on 2010-05-16
> **sirplayerrock said:**
> what is the best way to write a easy bash script?

have a need
fill a need

---

