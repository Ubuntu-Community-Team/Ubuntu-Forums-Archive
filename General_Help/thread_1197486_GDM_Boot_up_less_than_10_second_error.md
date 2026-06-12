---
title: "GDM Boot up less than 10 second error"
date: 2009-06-26
forum: General Help
---

### Post by jcr1 on 2009-06-26
Hi all,

Recently run into a problem. On start when I try to log in, I get an error message saying my session lasted less than 10 seconds and I can view the errors:

```

jonr@jonr-laptop:~$ cat .xsession-errors 
/etc/gdm/Xsession: Beginning session setup...
/etc/bash_completion: 32: [[: not found
/etc/bash_completion: 38: [[: not found
/etc/bash_completion: 50: Bad substitution
jonr@jonr-laptop:~$ 

```

Any one know what this is... it just started happening quite randomly. I can log in fine with gnome failsafe mode...

I have tried reinstalling bash-completion.

Thanks in advance.

Jon

---

### Post by JockVSJock on 2009-06-26
I've just started to get this too.  The only changes that I've made to the system is some changes to the BIOS because I'm trying to get suspended/hibernation status to work and also removed the floppy module. 

This is the text warning that I'm getting when logging into the Gnome desktop: 
```

your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see fi you can fix this problem

view details (~/.xsession-errors file)

/usr/bin/gnome-session error while loading shared libraries:  /usr/bin/libORBit-2.so.0: unexpected reloc type 0x21

```

I have a 250 GB HD and I am not able to log in via Gnome failsafe session either.  Thank God I like KDE as a desktop manager too, because I can at least get that desktop manager to work.  

I have looked at the contents of .xsession-errors and since I'm using KDE as the desktop manager I don't see any references to Gnome errors. 

Any ideas?

---

