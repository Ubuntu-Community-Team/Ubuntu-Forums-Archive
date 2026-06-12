---
title: "bash"
date: 2009-09-22
forum: General Help
---

### Post by FiskFisk33 on 2009-09-22
I remember there was a place i could put bash files to make them execute just by typing their name in the terminal, however i forgot where.

i bet its easy to find the answer but i dont know what to search.

---

### Post by kaibob on 2009-09-22
Create a directory named bin in your home directory.

---

### Post by Darkwing-Duck on 2009-09-22
If you want to know more about customizing bash follow this little tutorial. Maybe what your looking for.

[http://gwos.org/udsf/doku.php/core:bash:customize](http://gwos.org/udsf/doku.php/core:bash:customize)

---

### Post by ibuclaw on 2009-09-22
> **kaibob said:**
> Create a directory named bin in your home directory.

... and make them executable.

---

### Post by FiskFisk33 on 2009-09-23
ah thank you awesome!
 hm, while I'm at it.
i need to start two programs from /etc/rc.local but as it is now it only starts the first one.
i realize that that is because it wont continue on with the rest until the first program has ended (am i correct?)
how do i get around this?
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
cd /etc/bf2srv/bf2_1/cc
sudo mono bf2ccd.exe -autostart default
# it seems to stop here
cd /etc/bf2srv/bf2_2/cc
sudo mono bf2ccd.exe -autostart default

exit 0
```

---

### Post by ibuclaw on 2009-09-23
> **FiskFisk33 said:**
> ah thank you awesome!
 hm, while I'm at it.
i need to start two programs from /etc/rc.local but as it is now it only starts the first one.
i realize that that is because it wont continue on with the rest until the first program has ended (am i correct?)
how do i get around this?


Two things: **&** and **disown**

```

[code]#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/usr/bin/mono /etc/bf2srv/bf2_1/cc/bf2ccd.exe -autostart default &
/usr/bin/mono /etc/bf2srv/bf2_2/cc/bf2ccd.exe -autostart default &

disown
exit 0
```
disown is important, as it means that the programs stay running after the script has finished.

edit: I noticed that you had some redundant code as well, and removed that.
Correct it back if it is **imperiment** for you to cd into the directory beforehand.

edit2: Full pathnames to executables is preferred in low level scripts.

Regards
Iain

---

### Post by FiskFisk33 on 2009-09-23
Works like a charm!
thank you you're a lifesaver

---

