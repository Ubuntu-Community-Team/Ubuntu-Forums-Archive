---
title: "xubuntu terminal"
date: 2011-10-20
forum: General Help
---

### Post by China Diapers on 2011-10-20
Hi, 

Can anybody recommend an alternative terminal emulator to the default one on xubuntu?

The default one, bizarrely, does not have a select all command to select all the output for copying to clipboard.

Any ideas?

Thanks

---

### Post by hwttdz on 2011-10-20
One easy way to get the output is to append "> logfile 2>&1" to the end of your command, and then all the output is in logfile.

Even easier, you can just pipe the output to "xclip -i" to cut and use "xclip -o" if you want to paste at the terminal.  The 2>&1 will still be necessary to catch standard error as well as standard out.

Other than that, I guess you could use gnome-terminal?  It seems many terminal emulators don't have that functionality (honestly I've never even thought to look for it).

---

### Post by scania_gti on 2011-10-20
Just type "terminal" in software centre ;)
And look users rating.

---

### Post by China Diapers on 2011-10-20
> **scania_gti said:**
> Just type "terminal" in software centre ;)
And look users rating.

Yes of course, many of the terminals don't seem to have a select all command.

---

### Post by China Diapers on 2011-10-20
> **hwttdz said:**
> One easy way to get the output is to append "> logfile 2>&1" to the end of your command, and then all the output is in logfile.

Even easier, you can just pipe the output to "xclip -i" to cut and use "xclip -o" if you want to paste at the terminal.  The 2>&1 will still be necessary to catch standard error as well as standard out.

Other than that, I guess you could use gnome-terminal?  It seems many terminal emulators don't have that functionality (honestly I've never even thought to look for it).

Mate thanks a million, this is a far better solution, works like a charm.

---

### Post by China Diapers on 2011-10-20
> **hwttdz said:**
> One easy way to get the output is to append "> logfile 2>&1" to the end of your command, and then all the output is in logfile.

This I mean, awesome

---

### Post by Jose Catre-Vandis on 2011-10-20
> **China Diapers said:**
> Hi, 

Can anybody recommend an alternative terminal emulator to the default one on xubuntu?

The default one, bizarrely, does not have a select all command to select all the output for copying to clipboard.

Any ideas?

Thanks

I beg to differ. In 11.10 using xfce4-terminal, simply go to the edit menu and choose Select All (or SHIFT+CTRL+A) and the Copy (SHIFT+CTRL+C)

---

### Post by China Diapers on 2011-10-20
> **Jose Catre-Vandis said:**
> I beg to differ. In 11.10 using xfce4-terminal, simply go to the edit menu and choose Select All (or SHIFT+CTRL+A) and the Copy (SHIFT+CTRL+C)

Not in my terminal, the copy and paste work but not select all. I know this does work in the Gnome terminal though.

Anyway that stuff is for losers, writing to log files in the way forward.

---

### Post by China Diapers on 2011-10-20
That was close, posted my Betfair password for the whole world to see.

Screenshot, without Betfair login and password this time.

---

### Post by China Diapers on 2011-10-20
Is it possible to append the current date to the name of the text file I am directing the terminal output to? As in it takes the system date and adds it to the end of the file name.

I have Googled this but not found anything that looks like it works.

---

### Post by AlphaLexman on 2011-10-20
```
command > logfile-$(date +'%Y-%m-%d')
```

---

### Post by China Diapers on 2011-10-21
> **AlphaLexman said:**
> ```
command > logfile-$(date +'%Y-%m-%d')
```

Thanks

---

### Post by Rodney9 on 2011-10-21
> **Jose Catre-Vandis said:**
> I beg to differ. In 11.10 using xfce4-terminal, simply go to the edit menu and choose Select All (or SHIFT+CTRL+A) and the Copy (SHIFT+CTRL+C)
 
I agree, have a look

---

### Post by China Diapers on 2011-10-21
> **Rodney9 said:**
> I agree, have a look

Guys please, I am not a computer illiterate, I know how to use the select all function, if it exists. Please see my screenshot.

I am really not here to argue about whether your terminal can select all or not

---

### Post by scania_gti on 2011-10-21
Maybe try terminal command print to file?
Like:```
lscpi > listpcidevices.txt
```
Found in this tread:
[HTML]http://ubuntuforums.org/showthread.php?t=989100[/HTML]

---

