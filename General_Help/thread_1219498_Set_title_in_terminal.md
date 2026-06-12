---
title: "Set title in terminal"
date: 2009-07-21
forum: General Help
---

### Post by pvfloripa on 2009-07-21
Hi!

After I open a terminal in Ubuntu 8.10, I can go to the option 

"Terminal -> Set Title"

to change the terminal's title.

Does anybody know how I can perform this operation via command line?

Many thanks!!!

---

### Post by Dejai on 2009-07-21
Ah your talking about User@Host correct? Well to do that you would have to change your host for the part afterwards may I suggest the hostname command for a temporary change or the ubuntu wiki for more information. The first section is in fact your username. If your unhappy with that... In ubuntu, open System>Admin>Users and groups. Select your names and press properties. Then you can change your login name and password from there.

If you want to go through all the terminal stuff its basically just editing a bunch of config files in /etc/ But I don't see why you would want to change your user and hostname just to change the terminal title. 

In other words, if you want to change the title its application specific and you would have to know the location of the gnome terminal and configure something there. Otherwise you are wanting to change your username and hostname. I am a bit :confused:

---

### Post by wojox on 2009-07-21
Here:

```
gnome-terminal --title=wojox rocks
```

```
man gnome-terminal
```

---

### Post by LightningCrash on 2009-07-21
A guy I work with has the slick way of doing this. I'll look when I get to work tomorrow.

---

### Post by bab1 on 2009-07-21
I believe what you are looking for is in the .bashrc file.  it is the variable $PROMPT_COMMAND.  Here is the relevant part of the .bashrc file:```
# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
            PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac

```

---

### Post by Moyamo on 2010-06-12
> **wojox said:**
> Here:

```
gnome-terminal --title=wojox rocks
``````
man gnome-terminal
```

when I do this it changes the title to wojax for a few seconds and then it changes back to USER@HOSTNAME:CURRENT_DIRECTORY$

How do I stop this automatic change:confused:

---

