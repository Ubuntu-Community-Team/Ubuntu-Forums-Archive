---
title: "&quot;at&quot; doesn't do a thing!"
date: 2011-03-08
forum: General Help
---

### Post by Pithikos on 2011-03-08
I tryied many different things, echoing to a file, espeak and nothing works. "at" is running but it doesn't execute anything of what I tell it :confused:

---

### Post by Kareeser on 2011-03-08
How are you running it?

Try this:

```
at now + 1 minute
```

and when at opens standard input...

```

export DISPLAY=:0
zenity --info --text="Hello world."

```

Remember to use ctrl-D to finish, not ctrl-C. Optionally, you can put your commands in a separate file and call it with the "f" switch, thusly:
```

at now + 10 minutes -f doThisInTenMinutes.sh

```

Also note that at runs everything with /bin/sh, not bash. sh isn't as user friendly as bash, and (I believe) won't know where your home directory is, so everything must be absolutely linked.

---

