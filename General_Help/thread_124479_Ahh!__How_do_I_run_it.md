---
title: "Ahh!  How do I run it?"
date: 2006-02-01
forum: General Help
---

### Post by tonyisntcreative on 2006-02-01
I just download an rpm for the linux version of winamp and I think I did everything right to get it installed...but I have no idea how to open it up!  ```
tony@ubuntu:~$ sudo alien Winamp-0.a1-1.i386.rpm
winamp_0.a1-2_i386.deb generated
tony@ubuntu:~$ sudo dpkg -i winamp_0.a1-2_i386.deb
(Reading database ... 65097 files and directories currently installed.)
Preparing to replace winamp 0.a1-2 (using winamp_0.a1-2_i386.deb) ...
Unpacking replacement winamp ...
Setting up winamp (0.a1-2) ...

```Any help would be appreciated.

---

### Post by MartinG on 2006-02-01
I would guess type winamp at a prompt -- either in a console or using Alt+F2 (in KDE, anyway).

---

### Post by tonyisntcreative on 2006-02-01
It tells me that it's an unknown command.

---

### Post by drummer on 2006-02-01
Try typing win or just wi and press tab to get a list of possible commands. Could be something like winamp-player or something.

---

### Post by tonyisntcreative on 2006-02-01
It accepts "Winamp" as a command, yet it does nothing other than give me a new command line.

---

### Post by Lord Illidan on 2006-02-01
Same here.. Doesn't work at all..

Why don't you use XMMS, Amarok, or any of the frankly better native programs out there?

---

### Post by MartinG on 2006-02-01
Find Winamp in Synaptic, right click on it and select Properties, then go to the installed files tab.  Look through this list for whatever files are installed in /usr/bin (or, possibly, in /usr/local/bin, /usr/share/bin or another .../bin directory); one of these must be the executable, so try using that name.

If it claims to be an unknown command, try again but type the full path (e.g. /usr/bin/winamp) rather than just the filename.

---

### Post by Lord Illidan on 2006-02-01
[quote=MartinG]Find Winamp in Synaptic, right click on it and select Properties, then go to the installed files tab.  Look through this list for whatever files are installed in /usr/bin (or, possibly, in /usr/local/bin, /usr/share/bin or another .../bin directory); one of these must be the executable, so try using that name.

If it claims to be an unknown command, try again but type the full path (e.g. /usr/bin/winamp) rather than just the filename.[/quote]

The executable is ```
Winamp
```. It just doesn't seem to work, though.

---

### Post by tonyisntcreative on 2006-02-01
I was just SO used to winamp....that and since a lot of my cd's are ripped as wma, I wanted to be able to play those.  I installed BMP and I like that a little better than XMMS, and I just installed the wma plugin...so I guess that solve my problem for now.

---

### Post by MartinG on 2006-02-02
[QUOTE=Lord Illidan]The executable is ```
Winamp
```. It just doesn't seem to work, though.[/QUOTE]Does it require an argument (to choose a skin, or something)?  Being a Windows port, it might not have the usual Linux attributes, but does "Winamp --help" produce anything? Is there a man entry (man winamp)? Are there any docs (probably /usr/share/doc/winamp)?

---

