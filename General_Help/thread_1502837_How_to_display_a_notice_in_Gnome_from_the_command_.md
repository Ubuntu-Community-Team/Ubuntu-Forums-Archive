---
title: "How to display a notice in Gnome from the command line?"
date: 2010-06-06
forum: General Help
---

### Post by nikstard on 2010-06-06
What is the command to use to display a notice on the Gnome desktop? I would like to do something like the following:

```

    $ compile-huge-project && show-notice "Compilation ok" || show-notice "Compilation failed"

```

---

### Post by nikstard on 2010-06-06
Ahh, Google is my friend: [http://blogs.divisibleprime.com/ronin/articles/2008/03/10/command-line-gnome-notification]("http://blogs.divisibleprime.com/ronin/articles/2008/03/10/command-line-gnome-notification")

---

### Post by benson444 on 2010-06-06
Another option is zenity:

```
zenity --info --title="Compile result" --text="Compilation OK"
```

---

### Post by gerowen on 2010-06-06
I'm doing something similar with a python script.  I stuck the following zenity line into a test script and told it to print the output to make sure it captured the input properly, but it's weird, I keep getting the number 0 appended to whatever I enter.  Here's what I get:

The Python script for testing is this:
```

import os
value=os.system("zenity --entry --text 'Enter full path to your .LIT file' --title 'Enter filename'")
print value

```

And here's example output:
```

marcus@marcus-laptop:~/Desktop$ python zenitytest.py
yourmom
0

```

Anybody know why it's appending a 0?

---

### Post by benson444 on 2010-06-06
The zenity dialog returns 0 or 1 depending on whether OK or Cancel is clicked, so that is what is assigned to 'value'. What is typed into the text entry gets sent to stdout. If you remove the 'print value' line the text will still be printed.

I had a look around at capturing stdout in python and this works:

```
#!/usr/bin/env python

from subprocess import Popen, PIPE

proc=Popen("zenity --entry --text='Enter full path' \
--title='Enter filename'", shell=True, stdout=PIPE, stderr=PIPE)

value=proc.communicate()[0]

if value:
    print value[:-1]
```

I'm no expert but it seems to work. I'd advise researching it a bit to make sure I'm not missing something important.

---

