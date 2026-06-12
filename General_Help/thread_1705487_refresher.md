---
title: "refresher"
date: 2011-03-12
forum: General Help
---

### Post by Semi_Nerd on 2011-03-12
3-4 weeks ago, I started using ubuntu. I've been out of touch with my computer since then. Unfortunately, I've also forgotten most of what I learned. The main thing I can't remember is how to open files and games and such from the terminal. Any help would be appreciated.

---

### Post by lykeion on 2011-03-12
What files/games are you having problem with?
Generally to open a file you would enter the name of application to open the file followed by the filename itself. Example: Open a text file with Gedit text editor:
```
gedit <name_of_textfile>
```
To launch a game you would just enter the name of the game binary file. Example: Launch Kobo Deluxe:
```
kobodl
```

A tip: Try to name your thread better. This is a quote from the Ubuntu Forums Code of Conduct:
> Make the title of your thread meaningful and concise. For example, if you are having difficulty using your BroadCom card to connect to your wireless internet, the title "Cannot connect to wireless with BroadCom card" will attract people with experience with wireless internet and BroadCom cards. Titles like "Help me please!!!" or "I have a problem" may be overlooked by people who could otherwise help you. 

---

### Post by nc_jed on 2011-03-12
> **Semi_Nerd said:**
> 3-4 weeks ago, I started using ubuntu. I've been out of touch with my computer since then. Unfortunately, I've also forgotten most of what I learned. The main thing I can't remember is how to open files and games and such from the terminal. Any help would be appreciated.

Don't get to use the background operator (&) so it doesn't hog your terminal session.

Exec Shell Script:
$ sh ./shell_script_name.sh

gedit a file:
$ gedit path/to/file/toedit.txt

gedit a 'sensitive' file:
$ sudo gedit path/to/file/toedit.txt

---

