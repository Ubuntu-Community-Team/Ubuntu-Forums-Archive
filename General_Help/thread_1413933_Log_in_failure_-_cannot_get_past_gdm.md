---
title: "Log in failure - cannot get past gdm"
date: 2010-02-23
forum: General Help
---

### Post by pfcrock on 2010-02-23
**Cannot get past gdm - cannot log on** 
Basically when I get to the gdm/logon screen I type in my password running it in a normal *GNOME* session and it thinks for a bit then goes to the 9.10 ubuntu loading screen like it usually does on start-up but then it just loops back to the gdm - the same happens if I try boot in a *xsafe* session
If I try booting it with a *Failsafe GNOME* session then the screen just goes black and I can only move the mouse.

I am pretty sure this is because my hard drive is full, I have tried several things after pressing Ctrl+Alt+F1 and logging on but nothing seems to yield results - even when I type in startx it comes up with lots of text and then just continues in the command session.

Basically, my question is:
**[SIZE=2][COLOR=red]How can I free up space on my hard drive without being able to log-in? (ie. in command prompt thing)[/COLOR][/SIZE]**
**[SIZE=2][COLOR=#ff0000]Or how can I be able to log-on?[/COLOR][/SIZE]**

**[SIZE=1][COLOR=black]Cheers :razz:[/COLOR][/SIZE]**

---

### Post by r_s on 2010-02-23
you can always free some space from the command prompt by removing some unwanted files and even clearing the package archive using *sudo apt-get clean*.

---

### Post by JiuJitsu500 on 2010-02-23
Or boot froma live CD or USB and get 'er done :)

---

### Post by rnerwein on 2010-02-23
hi
if you can log in in a consol terminal execute following commands.
1. df -k  ( to see if your hd is really full)
2. have a look at your ~/.xsession-errors ( to see if there are some error messages which can cause the describe situation.
3. if the disk is full --> cd :~/.local/share/Trash/
4. du -k .  ( to see if the Trash folder is empty - if yes remove the files in the ./files folder)
5. run du -k in ~/ to see if you got huge files in your home directory ( i guess you are a movie or music fan)
6. if nothing works: post the output of your df -k command
ciao

---

