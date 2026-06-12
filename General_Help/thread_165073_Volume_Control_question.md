---
title: "Volume Control question"
date: 2006-04-23
forum: General Help
---

### Post by Greeface on 2006-04-23
I know that the command "amixer sset Master 1+ unmute" turns up the volume, but how do you make it bring up that little OSD of the volume level like if you were to turn it up using the keyboard shortcuts that you set in the Gnome Keybinding Properties menu?  Sorry if thats a little hard to understand

---

### Post by bluevoodoo1 on 2006-04-23
gnome-volume-control maybe? (If that's what you're looking for...)

---

### Post by Greeface on 2006-04-24
yeah i think so, but i need the command that that uses to make that little box.  Ill attach a screenshot so you know what i am talking about

thanks for the reply

---

### Post by nathandh on 2006-08-06
If someone knows how to do this it would be greatly appriciated. I also get the OSD indication when I use my keyboard to lower or increase the volume but it doesn't actually adjusts the volume it just shows the OSD thingy.

---

### Post by pointone on 2007-08-01
Sorry to revive the thread... but here goes!

Try:

```
sudo /etc/acpi/volupbtn.sh
sudo /etc/acpi/voldownbtn.sh
```

---

### Post by alphane on 2007-12-04
Any ideas on how I would run these commands as non-root?

Want to add these controls to my openbox setup and map them to some keys, without having to sudo.

---

### Post by pointone on 2007-12-04
Two ideas come to mind...

The first is easier, but may be a potential security risk or break other ACPI functions.

```
sudo chmod u+s /usr/bin/acpi_fakekey
```

This will set the suid bit on the acpi_fakekey binary, which will cause it to run as root no matter who uses it. 

The second: create your own launch script. Unfortunately, you'll have to do it in C, because you cannot set the suid bit on plain text files; they must be compiled.

```
sudo apt-get install build-essential
```

Create the following file, volup.c:

```
#include <stdlib.h>

int main() {
    system("/etc/acpi/volupbtn.sh");
    }
```

Run the following commands:

```
sudo gcc volup.c
sudo mv a.out /etc/acpi/volup
sudo chown root:root /etc/acpi/volup
sudo chmod u+s /etc/acpi/volup
```

... and repeat for voldown / voldownbtn.sh.

---

