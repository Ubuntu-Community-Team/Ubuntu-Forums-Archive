---
title: "acpi-support Problems"
date: 2011-02-05
forum: General Help
---

### Post by lvleph on 2011-02-05
I have been trying to get LIRC and Amarok 2 to work together, but I am having some issues. I need to use acpi-support, but when running any of the scripts in /etc/acpi I get an error, e.g.
```
/etc/acpi/playbtn.sh 
open: No such file or directory
```
I checked what the script was doing and I noticed it calls another file: /usr/share/acpi-support/key-constants
So I checked to see if this file actually was there and it was. So this didn't help me at all. The other thing I noticed was that the script runs
```
acpi_fakekey $KEY_PLAYPAUSE
```
I checked the key-constants file for the proper key-code which turned out to be 164. Anyway, I ran 
```
acpi_fakekey 164
```
and this is when I got the **open: No such file or directory** error. Now I am stuck.

EDIT: Running Linux Mint 9
```
uname -r
2.6.32-28-generic

```

---

