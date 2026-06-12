---
title: "why is the script unstable?"
date: 2009-10-14
forum: General Help
---

### Post by skaldyr on 2009-10-14
Im using this simple shell script.


```
#!/bin/sh
echo at+csq > /dev/ttyUSB2 | head -n 4 /dev/ttyUSB2 
```

Which reads out the signal strength form a 3g modem.

when a just type the expression in the command line it works fine.

But in the shell script it only reads out the correct result sometimes.

Can someone explain the difference?

---

### Post by scorp123 on 2009-10-14
Modem not ready maybe? My Novatel Ovation MC950D for example takes a few seconds to properly initialize. And most of the time the virtual CD-ROM part (containing the Windoze drivers) will come up first, so I first need to "eject" that CD-ROM part before the modem part initializes ...

Maybe it's something like this?

---

### Post by skaldyr on 2009-10-14
I dont think thats why its not reliable.

because i can run the command in terminal by itself like this

```
jon@jon-laptop:~$  echo at+csq > /dev/ttyUSB2 | head -n 4 /dev/ttyUSB2 
```
 and that works everytime. 
But when i try the shell script which is the exact same thing, even if i have used the above expression rigth before and gotten the right result, the shell script will not give the right result.
I dont understand why.

---

### Post by justleen on 2009-10-14
try using /bin/bash (since what you run cmdline is in bash, and that works), or use a full path to /bin/echo?

---

### Post by Giblet5 on 2009-10-14
> **justleen said:**
> try using /bin/bash (since what you run cmdline is in bash, and that works), or use a full path to /bin/echo?

+1

Each shell has its own builtin echo function. They are not all the same.

From the CLI, you're using bash. Make sure you always use bash or, as justleen said, specify /bin/echo explicitly.

---

### Post by skaldyr on 2009-10-14
With /bin/bash theres no change.

And with /bin/echo it just writes the name of the shell script.

---

### Post by justleen on 2009-10-14
ehm.. just double check, but I meant to change #!/bin/sh to #!/bin/bash. And echo should works exacly the same..
```
#!/bin/bash
/bin/echo at+csq > /dev/ttyUSB2 | /usr/bin/head -n 4 /dev/ttyUSB2
```

---

### Post by skaldyr on 2009-10-14
I forgot the first / in /bin/echo.


Thank you. Great help

---

