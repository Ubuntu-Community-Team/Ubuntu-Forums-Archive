---
title: "start skype and gedit programs from same script."
date: 2010-12-30
forum: General Help
---

### Post by gmgj on 2010-12-30
I  am trying to make a wifey friendly way to click on something in the desktop and have it start 2 programs.  One program is Skype, the other is gedit which opens a file with notes we have made about using Skype

1)
[Desktop Entry]
/home/ubugj/Desktop/gjtest

2)
file gjtest  with permissions to execute
!/bin/sh

#this is skype-wrapper
if [ ! -e ~/.Skype/shared.xml ]; then
  mkdir -p ~/.Skype
  cp /usr/share/skype/shared.xml ~/.Skype/shared.xml
fi

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so  /usr/bin/skype "$@"

#this is to open skype.txt, a file of notes
/usr/bin/gedit "/home/ubugj/Desktop/Skype.txt"

3)if skype first, starts skype, when quit skype, start gedit with Skype.txt and vice versa

My swag is that its an issue with starting programs with user interfaces.
?

---

### Post by XeonBloomfield on 2010-12-30
Did you try "screen"?

It creates separated "screen" with console and run on it Skype.

For example:
```
screen -A -m -d -S screen_name command
```

So for Skype it is:
```
screen -A -m -d -S skype skype
```

You can go to "screen" like that by:
```
screen -r skype
```

And you can detach it by pressing CTRL+A+D.

It will not stop your script, it will just start screen on another process without pausing your script.

---

### Post by tredegar on 2010-12-30
Another way.

If you want to start 2 (or more) programs at once, try this:

```
#!/bin/bash
# script to open both skype and a textfile
skype &
gedit /path/to/file &
```

Then **chmod +x /path/to/script**
Then call the script from a menu entry, desktop icon, whatever.

The "&" puts that program in "the background" and allows the script to continue, so both skype, and the gedit file open at the "same" time.

---

### Post by gmgj on 2010-12-30
Thanks for the answers.

I tried the version with the keywords screen
#!/bin/sh
screen -A -m -d -S skype skype-wrapper
screen -A -m -d -S gedit /usr/bin/gedit "/home/ubugj/Desktop/Skype.txt"
exit

Happy as a bird with a french fry!

---

