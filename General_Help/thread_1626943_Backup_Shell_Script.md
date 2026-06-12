---
title: "Backup Shell Script"
date: 2010-11-20
forum: General Help
---

### Post by antonvrg on 2010-11-20
g'day all,

I have just started messing around with Shell Scripts and wondering how i would go about having all the files in /home/me/backup/ to be added to a .7z archive and up in /home/me/backed-up/ or something like that?

any help would be great.

Thanks, Anton.

---

### Post by Crusty Old Fart on 2010-11-20
If you could be a little more specific about exactly what you're trying to do, then there's a good chance I'd be able to help you out.

---

### Post by antonvrg on 2010-11-20
> **Crusty Old Fart said:**
> If you could be a little more specific about exactly what you're trying to do, then there's a good chance I'd be able to help you out.

have a folder in my home directory that i put stuff that i want backed up on like a usb stick or ftp server. have all the files in the folder in a 7zip archive and then put in an other directory (i have a script that uploads to an ftp server every 2 days). i dont want all my files backed up just ones i put in that directory.

---

### Post by Crusty Old Fart on 2010-11-20
Should be a piece of cake.
All I need to do is install 7zip, take a look at the man page and write the script. Should only be about two or three lines of code.

I'll get on it right now.

---

### Post by Crusty Old Fart on 2010-11-20
Here you go:

Edit the blue line in the code box below to specify the path and file name of the archive file.
Edit the green line to specify the directory that contains the files you want to add to the archive.
```

#!/bin/bash 
set -e

[COLOR=Blue][B]ARCHIVE_NAME="/home/me/backed-up/archive.7z"
[COLOR=Green]SOURCE_DIR="/home/me/backup"[/COLOR][/B][/COLOR]

7z a -t7z "$ARCHIVE_NAME" "$SOURCE_DIR"
 
exit 0

```

---

### Post by antonvrg on 2010-11-21
> **Crusty Old Fart said:**
> Here you go:

Edit the blue line in the code box below to specify the path and file name of the archive file.
Edit the green line to specify the directory that contains the files you want to add to the archive.
```

#!/bin/bash 
set -e

[COLOR=Blue][B]ARCHIVE_NAME="/home/me/backed-up/archive.7z"
[COLOR=Green]SOURCE_DIR="/home/me/backup"[/COLOR][/B][/COLOR]

7z a -t7z "$ARCHIVE_NAME" "$SOURCE_DIR"
 
exit 0

```

thanks man! couldn't find the manual page, [HTML]man 7zip[/HTML] ill reinstall it

---

### Post by Crusty Old Fart on 2010-11-21
You're mighty welcome.

And...

It ain't:
```

man 7zip

```It's
```

man 7z

```

---

### Post by antonvrg on 2010-11-21
> **Crusty Old Fart said:**
> You're mighty welcome.

And...

It ain't:
```

man 7zip

```It's
```

man 7z

```


there's the problem :)

---

