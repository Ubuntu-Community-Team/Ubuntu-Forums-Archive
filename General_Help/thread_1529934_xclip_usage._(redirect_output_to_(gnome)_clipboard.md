---
title: "xclip usage. (redirect output to (gnome) clipboard on command line?)"
date: 2010-07-12
forum: General Help
---

### Post by aweber on 2010-07-12
This is a continuation of the post archived at [http://ubuntuforums.org/showthread.php?t=413786](http://ubuntuforums.org/showthread.php?t=413786).

The following example works great when done in Terminal

```
$ fglrxinfo | xclip -sel clip
```

However, this does not work from: a Keyboard Shortcut, Alt-F2, or a Panel Custom Application Launcher.  Might this have to do with setting the X display?  It's the only part I'm not familiar with, and I'm not sure of the syntax (if this is the issue).

```
xclip -sel clip -d ?????
```

---

### Post by gzarkadas on 2010-07-13
I don't know why this happens. However a workaround, is to put your command inside a script file (such as this example:

```

#!/bin/bash
cat <some-file> | xclip -selection "clipboard"

```) and make it executable. 

Then you can succesfully paste the copied text by simply issuing your script as the command.

---

### Post by aweber on 2010-07-15
This worked beautifully. Thank you!

---

### Post by playful_geometer on 2010-08-18
I could not make this solution work either from "Run application" or Compiz , although when I run the script from the terminal the text goes into the clipboard.  The script file was "~/pasties", the commands I tried were "bash ~/pasties"  "bash ~/pasties 0"  "~/pasties 0"  "~/pasties", the file was as follows: 

```
#!/bin/bash
TEXTARR[0]="http://www.flickr.com/photos/playful_geometer/"
TEXTARR[1]="http://sites.google.com/site/starringattractions/"
echo ${TEXTARR[$1]} | xclip -selection "clipboard"
```

Any tips ?  Before I pull my hair out, I give up... for now ....

---

### Post by gzarkadas on 2010-08-18
Replace the ~ in your command with the full path to your folder (/home/<your-account>/pasties).  To pass arguments enclose them in quotation marks. Alt+F2 example:
```
/home/myaccount/pasties '0'
```. You must have made the file executable for this to work.

---

### Post by DaithiF on 2010-08-18
> **aweber said:**
> 
The following example works great when done in Terminal

```
$ fglrxinfo | xclip -sel clip
```However, this does not work from: a Keyboard Shortcut, Alt-F2, or a Panel Custom Application Launcher.  Might this have to do with setting the X display?  It's the only part I'm not familiar with, and I'm not sure of the syntax (if this is the issue).

```
xclip -sel clip -d ?????
```

this command pipes output from one command to another.  when run in a terminal it is the shell that takes care of the mechanics of redirecting the output from one program to the stdin of the other.  When entered into Alt-F2, there is no shell to do this, and so commands can't be chained together in this way.

unless of course you invoke a shell to run the command for you.  So for example, this would work in Alt-F2:
```
bash -c "fglrxinfo | xclip -sel clip"

```

---

