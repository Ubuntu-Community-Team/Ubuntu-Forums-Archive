---
title: "Running a program in a console?"
date: 2010-04-20
forum: General Help
---

### Post by kartal on 2010-04-20
Hi

I am using a gui app that can run other apps in case of a trigger event. It works well however I would like to see the console out put of the called app. In this case  the gui app calls "unison" when there is a change. The app calls Unison and Unison runs well but it all happens in the background and I do not know what is going on. So I would like unison to run in a console when the app cals it.

any ideas?

thanks

---

### Post by m_duck on 2010-04-20
To run 'top' in 'gnome-terminal' for example:
```
gnome-terminal -x top
```

Or in xterm:
```
xterm -e top
```

---

### Post by klemes on 2010-04-20
You can always run a gui program by typing it's full name in a console.That way you can keep track of what is going in the background including most of the times the programs that this particular app calls.

---

### Post by thegreenblob on 2010-04-20
You could have your app run that command in a terminal like this,

```
xterm -e unison
OR
gnome-terminal -e unison
OR
terminator -e unison
```

And that will run it in a terminal. Depending on which terminal app you use, I've found that most support -e to run a command.

Hope this helps.

edit: doh, I was too slow. lol

---

### Post by kartal on 2010-04-20
Hi

thank you for all the great answers. I tried all and it seems like "xterm" is the one that works for me

I have one final question. I tried looking into xterm`s help and cannot figure out.

Is there a way to keep the console window open? Unison runs in console but as soon as its done the xterm shell closes as well.

thanks

---

### Post by m_duck on 2010-04-20
Assuming your shell is bash, the following works:
```
xterm -e "top && bash"
```[Ref: LQ Link]("http://www.linuxquestions.org/questions/linux-newbie-8/open-a-terminal-and-run-a-program-after-gnome-boot-515690/")

---

### Post by itcotbtoemik on 2010-04-20
man xterm -

       -hold   Turn  on  the  hold  resource, i.e., xterm will not immediately
               destroy its window when the shell command completes.   It  will
               wait  until you use the window manager to destroy/kill the win-
               dow, or if you use the menu entries that send a  signal,  e.g.,
               HUP or KILL.

---

### Post by kartal on 2010-04-20
Hi

It looks like xterm -hold is exactly what I was looking for.


thanks again

---

