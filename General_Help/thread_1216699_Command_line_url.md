---
title: "Command line url"
date: 2009-07-18
forum: General Help
---

### Post by jfreak53 on 2009-07-18
Other than writing it in Python, is there a command line program that I can run from an sh script that will open a url and parse the return.  Since I can't find anything that exists already I want to make a small script to run that will, using zenity, prompt for url then parse it with the tinyurl api which returns a one line of text with the new url.  Is there something for this from the command line?  I don't want to take the time to make a screenlet either.

Thanks in advance.

---

### Post by Finalfantasykid on 2009-07-18
you might be able to use something from the program w3m(terminal based web browser).

---

### Post by wojox on 2009-07-18
wget may work in terminal:

```
man wget
```

---

### Post by t4thfavor on 2009-07-18
Use wget, sed/awk, and tinyurl to get what you want.

Is it possible to get more information about what your looking to do?

---

### Post by jfreak53 on 2009-07-18
AHA, screw making a pything screenlet, too much work.  I ended up using w3m to output to stdout and xclip to copy the new link to clipboard for fast pasting.  I couldn't find out how to make wget go to stdout instead of a file.  Here is what I was trying to do:

```
#!/bin/bash

url1=`zenity --title "Enter URL" --entry --text "Enter the URL you want to TINY:"`

w3m -dump_source http://tinyurl.com/api-create.php?url=$url1 | xclip -selection clip-board
```

Sweet, now to put a link in the applet bar.  Thanks for all the help.

---

### Post by t4thfavor on 2009-07-18
Now thats a service to society.

---

