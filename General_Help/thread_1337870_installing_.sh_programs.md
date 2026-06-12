---
title: "installing .sh programs"
date: 2009-11-25
forum: General Help
---

### Post by time_shift on 2009-11-25
i have just downloaded the new version of boinc to find that i don't know how to install a .sh file. i tried to do what they said online (sh file.sh) but it didn't work. i was wondering why on the easy version ubuntu which is the easy version of linux which is the easy version of unix that i still feel like the education requirements for os's still go
Mac OS- babies
Windows OS elementary school
Linux college
Unix university
the funny thing is that i just went to school for a year to learn how to be a computer support specialist (though it was 99% windows).

---

### Post by 3rdalbum on 2009-11-25
A ".sh" file is a shell script. You don't install it, you run it.

If Boinc doesn't distribute its programs in an easy-to-install format, that is not Ubuntu's fault. Ubuntu distributes Boinc in the repositories already - it's three clicks away.

I'm sure as a support specialist you can appreciate that, in order to diagnose a problem, the person giving support must be provided with better descriptions than "it didn't work". :-D

One of two things come to mind:

1. It didn't work because your terminal wasn't navigated to the directory that contains the script
2. The script needs root access to install Boinc in a system-wide location.

Type this into the terminal, but don't press Enter yet:

```
sudo sh 
```

Put a space after the 'h'. Drag the script into the terminal window. Click the terminal to bring it back to the front, and now press Enter.

The 'sudo' part of the command says "Run this as root". Remember, your ordinary user account can only write to its home directory; you need to be root to create or modify files outside your home directory. Dragging the file to the terminal will fill in the path for you.

---

