---
title: "Launch parameter for gnome terminal to run a command at launch?"
date: 2009-07-16
forum: General Help
---

### Post by w1ntermute on 2009-07-16
Hello,

If I were to open a gnome terminal with the command gnome-terminal, is there a launch parameter to run a command as soon as it opens?

For example something like

```
gnome-terminal -r irssi
```If I wanted it to run irssi on startup


All help appreciated, thankyou :)

---

### Post by roccivic on 2009-07-16
```
gnome-terminal -x irssi
```

---

### Post by w1ntermute on 2009-07-16
Thanks for this :)

If I wanted, however, for the terminal to echo the output from a command specified in the launch (cowsay for example, or just "todo" to output a simple todo list), would there be an alternative to the -x to run a specified command? Trying these outputs with it usually just closes the window as soon as the print is done or simply breaks (at least in the case of cowsay)

---

### Post by roccivic on 2009-07-16
Do you specifically want to read the output from gnome-terminal?
How about a GUI script?

```
#! /bin/bash
echo "foo" > /tmp/bar
zenity --info --text="`cat /tmp/bar`"
rm -f /tmp/bar

```

Obviously you change 'echo "foo"' to whatever you want executed.
You will need to give the script executable permissions, if you save it as, say foobar.sh on your desktop:
```
chmod +x ~/Desktop/foobar.sh
```

For more cool GUI options try:
```
man zenity
```

If you don't have zenity installed (you should):
```
sudo apt-get install zenity
```

---

### Post by roccivic on 2009-07-17
If you do want to see the output int he terminal, just thought this might work for you:

```
#! /bin/bash
echo "Now executing \"echo\""
echo -e "\nFinished executing, press ENTER to close this window."
read
```

Change the line (echo "Now executing \"echo\"") to whatever code you want executed.
If you save the above script as "foobar.sh" on your Desktop, you can call it like this:
```
gnome-terminal -x ~/Desktop/foobar.sh
```

---

