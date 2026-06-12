---
title: "custom commands, is it possible?"
date: 2011-05-24
forum: General Help
---

### Post by NERDMAN! on 2011-05-24
i want to create a command that can be typed in any old terminal window that would display a message on screen for anyone who typed it. is this possible? i just want to do this for the randomness of it.
and cuz i need to get used to messing with terminal windows.

for example i would like to have "rawr" setup as a command to display a message on screen in a popup window with an "Ok" button to close the popup.

can someone tell me how to do this? i googled it but all i came up with was creating commands to launch applications without having to type the full path/command. not what i'm looking for. thanks in advance!!!

---

### Post by nothingspecial on 2011-05-24
Sure it's possible.

You have to write a script and put it somewhere in everybody's $PATH such as /usr/bin

To do what you actually want to do, have a look at either xmessage or zenity.

```
nano rawr
```

Put this line in it

```
xmessage "Press okay to close the window"
```

Press Ctrl O to save it then enter

Press Ctrl X to close it then make it executable

```
chmod +x rawr
```

Then run it like this ```
./rawr
```

Congratulations, you just wrote your first script :popcorn:

---

### Post by seawolf167 on 2011-05-24
See nothingspecial's post for running a bash script via a command, you could alternatively (and lazily) create an alias in each user's .bashrc file

```
gedit ~.bashrc
```then add an alias

```
alias rawr='echo "your message here"'
```Save the file, close the terminal, reopen, and type

```
rawr
```

---

### Post by sanderd17 on 2011-05-24
If you want to mess in the Terminal, read this: [http://linuxcommand.org/](http://linuxcommand.org/)

It's short and good.

---

### Post by Toz on 2011-05-24
For a more modern look and feel: ```
zenity --info --title "RAWR" --text "Press OK to close this window"
```

```
man zenity
``` to list all of the options.

---

