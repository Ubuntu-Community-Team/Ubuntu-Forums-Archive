---
title: "Help with my Nautilus scripting?"
date: 2010-02-14
forum: General Help
---

### Post by Xero Xenith on 2010-02-14
Hey, I'm trying to make a Nautilus script that plays an unfinished .rar file containing a video file.

This command does everything I need - it's essentially perfect.

```
unrar p -inul myarchive.rar | mplayer -cache 2048 -
```

I'm just a bit lost on how to convert it to a Nautilus script. So far I've got this far:

```
#!/bin/sh
unrar p -inul $NAUTILUS_SCRIPT_SELECTED_URIS | mplayer -cache 2048 -
```

...however this doesn't do anything when I add it as a Nautilus script and run a .rar file through it.

I'm on Ubuntu 9.10 64-bit. Any help would be much appreciated :)

---

### Post by kaibob on 2010-02-14
I don't have unrar or mplayer installed to test your command, but $NAUTILUS_SCRIPT_SELECTED_URIS won't work. Instead, you should use $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS, which returns the name of the selected file including its path, or $1, which returns the name of the selected file without its path. 

For example, if the selected file is located in my home directory and is named file.txt, then

$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS returns /home/kaibob/file.txt

$NAUTILUS_SCRIPT_SELECTED_URIS returns file:///home/kaibob/file.txt

$1 returns file.txt

---

### Post by Xero Xenith on 2010-02-14
> **kaibob said:**
> I don't have unrar or mplayer installed to test your command, but $NAUTILUS_SCRIPT_SELECTED_URIS won't work. Instead, you should use $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS, which returns the name of the selected file including its path, or $1, which returns the name of the selected file without its path. 

For example, if the selected file is located in my home directory and is named file.txt, then

$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS returns /home/kaibob/file.txt

$NAUTILUS_SCRIPT_SELECTED_URIS returns file:///home/kaibob/file.txt

$1 returns file.txt

Thanks for your reply!

Unfortunately I can't get any of that to work. I've made the script simply:
```
#!/bin/sh
$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS > ~/test-01.txt
```

... and test-01.txt is created, but it's blank. If I make it like this:

```
#!/bin/sh
ls . > ~/test-01.txt
```

...then it functions as expected (returning a file list). I just can't get those naming functions you described to work properly - I tried all three, and they all return a blank file.

Thanks again :)

EDIT: this seems to work!
```
#!/bin/sh
unrar p -inul "$@" | mplayer -cache 2048 -
```

---

### Post by kaibob on 2010-02-14
> **Xero Xenith said:**
> Thanks for your reply!

Unfortunately I can't get any of that to work. I've made the script simply:
```
#!/bin/sh
$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS > ~/test-01.txt
```

... and test-01.txt is created, but it's blank. If I make it like this:

```
#!/bin/sh
ls . > ~/test-01.txt
```

...then it functions as expected (returning a file list). I just can't get those naming functions you described to work properly - I tried all three, and they all return a blank file.

Thanks again :)

EDIT: this seems to work!
```
#!/bin/sh
unrar p -inul "$@" | mplayer -cache 2048 -
```

You have to use the echo command--the following will work:

```
#!/bin/sh
echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" > ~/test-01.txt
```

"$1" should return the same thing as "$@" if you only select one file in Nautilus. I don't know why that didn't work for you. Anyways, glad you got things working.

---

