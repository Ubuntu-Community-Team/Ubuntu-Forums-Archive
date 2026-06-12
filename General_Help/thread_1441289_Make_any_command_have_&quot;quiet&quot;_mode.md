---
title: "Make any command have &quot;quiet&quot; mode?"
date: 2010-03-28
forum: General Help
---

### Post by Bheklilr on 2010-03-28
I was wondering if anyone knew of a really quick way to keep any command from outputting in terminal.  Specifically, I want to for the "scanimage" command.  It throws a warning message for me every time I run it, but everything still works fine.  I just wanted to get rid of that warning message.

Thanks

---

### Post by gmargo on 2010-03-28
command > /dev/null 2>&1

The ">" redirects the standard out stream (stdout) to the bit bucket.
The "2>&1" redirects the standard error stream (stderr) to the same as stdout.

Or, to only toss the stderr stream:
command 2> /dev/null

Or, to ignore just one particular error message:
command 2>&1 | grep -v "particular error message"

---

### Post by Bheklilr on 2010-03-28
that would work for most functions, but the way I'm using ```
scanimage
``` is
[INDENT]```
scanimage -x 215 -y 280 > output.pdf
```[/INDENT]

Is there another way to do this?

---

### Post by gmargo on 2010-03-28
I could have written the first one as:
```

command > /dev/null 2> /dev/null

```so, in your case, to toss all error messages:
```

scanimage -x 215 -y 280 > output.pdf 2> /dev/null

```Alternatively, to toss only a particular error message (trick: using a sub-shell):
```

( scanimage -x 215 -y 280 > output.pdf ) 2>&1 | grep -v "particular error message"

```

---

### Post by Bheklilr on 2010-03-28
Thanks, that does the trick quite well.

---

