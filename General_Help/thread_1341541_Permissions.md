---
title: "Permissions"
date: 2009-11-29
forum: General Help
---

### Post by frank cox on 2009-11-29
I went into users and groups and added myself to administrators but still get permission error messages. For instance when I tried to install the smoking guns game.
First I extracted it to a file in home but the manual said it should be in /usr/local/ games/quake3 .
I used terminal to create the file because it would not allow me to in the gui but I don't know how to extract to it and don't understand why i can't do it all with the gui.

The pingus game I loaded from a deb and it loaded to that directory with no glitches.

TIA

---

### Post by Xog on 2009-11-29
> **frank cox said:**
> I went into users and groups and added myself to administrators but still get permission error messages. For instance when I tried to install the smoking guns game.
First I extracted it to a file in home but the manual said it should be in /usr/local/ games/quake3 .
I used terminal to create the file because it would not allow me to in the gui but I don't know how to extract to it and don't understand why i can't do it all with the gui.

The pingus game I loaded from a deb and it loaded to that directory with no glitches.

TIA

are u using sudo for creation?

---

### Post by frank cox on 2009-11-29
> **Xog said:**
> are u using sudo for creation?

That was fast!

I kept looking and found a reference to the gksudo nautilus command and it allowed me to extract the files.

I am not sure  what you mean. I was trying to do it all with the graphical interface. 
I used sudo to create the file but I don't know how to extract files in terminal.

Is that possible? 

Thanks

---

### Post by Xog on 2009-11-29
> **frank cox said:**
> That was fast!

I kept looking and found a reference to the gksudo nautilus command and it allowed me to extract the files.

I am not sure  what you mean. I was trying to do it all with the graphical interface. 
I used sudo to create the file but I don't know how to extract files in terminal.

Is that possible? 

Thanks

mv: The mv command will move a file to a different location or will rename a file. Examples are as follows: "mv file foo" will rename the file "file" to "foo". "mv foo ~/Desktop" will move the file "foo" to your Desktop directory but will not rename it. You must specify a new file name to rename a file.

    * To save on typing, you can substitute '~' in place of the home directory.
    *

      Note that if you are using mv with sudo you can use the ~ shortcut, because the terminal expands the ~ to your home directory. However, when you open a root shell with sudo -i or sudo -s, ~ will refer to the root account's home directory, not your own.

I believe this is what it would be:
```
 sudo mv /locationOfSubdirectories/locationOfDirectoryYou'reMoving (space) /usr/local/games/quake3
```

---

### Post by frank cox on 2009-12-01
Thanks but I think gksudo nautalis is easier to remember.

---

