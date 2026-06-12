---
title: "Opening terminal and execute commands"
date: 2009-11-25
forum: General Help
---

### Post by Raff1 on 2009-11-25
Hello! How can I open a terminal and execute a command there? I am thinking along the lines of:
```
gnome-terminal echo 'hello world'
```but this only opens a new terminal window. What I wanted was to display "Hello World" in the newly opened terminal.

Another thing: How to execute several lines of commands as a script? I am thinking something i can run like a launcher or something. If will be happy if I can run it with ./  :-)

---

### Post by Mr. Devil on 2009-11-25
```
gnome-terminal --command="echo 'Hey, I am alive!'"
```More than 1 command - shell script ( .sh ).

---

### Post by drs305 on 2009-11-25
```
gnome-terminal -x echo "hello world"
```

Read about switches by typing "man gnome-terminal":
```

gnome-terminal -x man gnome-terminal

```

;-)

---

### Post by doas777 on 2009-11-25
if your command will be run from a launcher, you can just put in the command, and tell it that it is of type "Application in Terminal" from the dropdown at the top. no idea if that is your usecase though.

---

### Post by Raff1 on 2009-11-25
> **Mr. Devil said:**
> ```
gnome-terminal --command="echo 'Hey, I am alive!'"
```More than 1 command - shell script ( .sh ).
bash: !'": event not found

> **drs305 said:**
> ```
gnome-terminal -x echo "hello world"
```Read about switches by typing "man gnome-terminal":
```

gnome-terminal -x man gnome-terminal

```;-)
This might work..? However, the terminal closes as soon as its done, so I really can't tell. Switces it is then! Thanks :-)

---

### Post by drs305 on 2009-11-25
> **Raff1 said:**
> bash: !'": event not found


This might work..? However, the terminal closes as soon as its done, so I really can't tell. Switces it is then! Thanks :-)

It doesn't close for me, but try adding a " &" symbol at the end.

---

### Post by Raff1 on 2009-11-25
> **drs305 said:**
> It doesn't close for me, but try adding a " &" symbol at the end.
```

:~$ gnome-terminal -e echo "hello world" &
[1] 5175
:~$ fg
bash: fg: job has terminated
[1]+  Done                    gnome-terminal -e echo "hello world"

```

Huh! it still disappears :S
I read the manual, and tested the -t for setting the topic as well, but the topic just flashes for a split second before the topic goes back to the usual me@pcname: ~
```
gnome-terminal -t "Topic"
```

Thanks for the help ppl! :D

---

### Post by Mr. Devil on 2009-11-25
> **Raff1 said:**
> bash: !'": event not found

Remove the **!** sign from the echo command ;)

---

### Post by drs305 on 2009-11-25
For gnome-terminal, click on Edit, Profile Preferences: Tiitle and Preferences: When a command exits: Hold the terminal open.

---

### Post by Raff1 on 2009-11-25
> **drs305 said:**
> For gnome-terminal, click on Edit, Profile Preferences: Tiitle and Preferences: When a command exits: Hold the terminal open.
Ah thanks! And Devil: It worked all right now!

However, I don't seem to be able to use these newly opened terminals after running the commands. So no use in holding the terminal open as I can see it anyways :-)
What I originally tried to do was this:

```
gnome-terminal -x irrsi
```
and that work neatly now! Thanks! But as I /exit irssi the terminal is still not usable. I don't need that so badly (problem solved!), but it would have been nice to be able to use it for something sensible afterwards :p

---

### Post by kaibob on 2009-11-25
The following is another way to do what you want. It doesn't require that you change  the terminal-window setting.

```
gnome-terminal -x bash -c "echo 'hello world' ; bash"
```

---

### Post by Raff1 on 2009-11-25
> **kaibob said:**
> The following is another way to do what you want. It doesn't require that you change  the terminal-window setting.

```
gnome-terminal -x bash -c "echo 'hello world' ; bash"
```

Nice! That is just what I wanted! Thanks \o/

---

