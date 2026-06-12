---
title: "How do you find your executable program files in Ubuntu?"
date: 2009-08-01
forum: General Help
---

### Post by DGeeez on 2009-08-01
I found out recently that the reason I've not been seeing any file extensions consistent with executable files is that there are no such extensions. So, there I would go, trying to find a program launcher for Nautilus (so that I could add it to my toolbar for instant gratification, in a choice directory), but I just can't expect to identify programs by file extension - how can I cull my system for this? Does Linux have a directory which lists only programs, and if there isn't one which contains exclusively executables, then how do you tell an executeable from a library file?

Thanks.

---

### Post by michy99 on 2009-08-01
To find an executable, use the which command.```
which nautilus
```will return```
/usr/bin/nautilus
```

---

### Post by jocampo on 2009-08-01
> **DGeeez said:**
> I found out recently that the reason I've not been seeing any file extensions consistent with executable files is that there are no such extensions. So, there I would go, trying to find a program launcher for Nautilus (so that I could add it to my toolbar for instant gratification, in a choice directory), but I just can't expect to identify programs by file extension - how can I cull my system for this? Does Linux have a directory which lists only programs, and if there isn't one which contains exclusively executables, then how do you tell an executeable from a library file?

Thanks.

Wow! ;-) a lot of questions in just one thread...well, let me help you...

The most basic way to find out is via file system. Open a console and run

```
ls -la
```
You will see some letters, like RWX and so on, divided on three main sections from left to right: folder-user-group-others. If there is an X, chances are high that the file is a program, which means that can be executed. 

The location of the file is a good indicator too. Linux executables files resides on /bin , like ls and cp commands.

---

### Post by michy99 on 2009-08-01
Also, to find out what type a certain file is, use the file command.```
mike@ubuntumike:~$ file /usr/bin/nautilus
/usr/bin/nautilus: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped
```

---

### Post by Raffles10 on 2009-08-01
Executables are contained in /usr/bin.

If you're trying to add a shortcut to your gnome panel, right click + add to panel is the simplest method.

If you want to add a shortcut to the menu, right click 'Applications' and select 'Edit Menu' & 'New Item'.

---

### Post by michy99 on 2009-08-01
Actually, there are many /bin directories containing executables.```
/bin
/sbin
/usr/bin
/usr/sbin
/usr/local/bin
/usr/local/sbin
```sometimes even a /bin in the user's home directory for manually installed programs.

That is why the which command comes in handy.

---

### Post by HermanAB on 2009-08-01
Hmmm, that is one of the closely guarded Unix secrets that make old timers laugh in their beards.

Try whereis, which and locate.

Tee, hee, hee...

---

### Post by jocampo on 2009-08-01
> **michy99 said:**
> Also, to find out what type a certain file is, use the file command.```
mike@ubuntumike:~$ file /usr/bin/nautilus
/usr/bin/nautilus: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped
```

Hey Michy, did not know that command, thanks ;-) I learned something new today

---

### Post by DGeeez on 2009-08-02
Thanks, everyone!

---

