---
title: "Wine App Auto Start"
date: 2011-03-01
forum: General Help
---

### Post by fleamour on 2011-03-01
What command can I use to get a research app to auto start under wine?

I have tried:

```
wine /directory/app.exe
```

It does not work

---

### Post by davidmohammed on 2011-03-01
if you mean auto-start on logon then enter the following commandline entry in your startup list

sh -c "/usr/bin/wine /home/user/app.exe &" 

hopefully this will work for you.

---

### Post by fleamour on 2011-03-01
> **davidmohammed said:**
> sh -c "/usr/bin/wine /home/user/app.exe &"

Not working for me with or without quote marks.  There is a space after wine before file path, yeah?

---

### Post by davidmohammed on 2011-03-01
yes - space between wine and after .exe

Does your application start if you type the above in a terminal session?

If not -  what errors do you see in the output?

---

### Post by fleamour on 2011-03-01
user@computer:~$ sh -c /usr/bin/wine /home/user/.wine/drive_c/Program Files/Watchtower/Watchtower Library 2010/WT Library 2010/E/WTLibrary.exe 


Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit

---

### Post by davidmohammed on 2011-03-01
try

```
sh -c "/usr/bin/wine /home/user/.wine/drive_c/Program\ Files/Watchtower/Watchtower\ Library\ 2010/WT\ Library\ 2010/E/WTLibrary.exe &"
```

i.e. you have to "escape" the spaces in the file name - you'll also need the quotes.

---

### Post by fleamour on 2011-03-01
OK, thanks.  Will try again tomorrow.  On laptop at mo' as Unicomp keyboard (think Russian military issue) is way too noisy for nocturnal use.

---

