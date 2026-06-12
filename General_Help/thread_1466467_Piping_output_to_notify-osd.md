---
title: "Piping output to notify-osd?"
date: 2010-04-30
forum: General Help
---

### Post by gk_manutd on 2010-04-30
Hey guys... 

I was wondering how would you go about piping the output of the shell to notify-osd? 


Thanks!!! :)

---

### Post by Serpher on 2010-04-30
I don't know what notify-osd is, but you can redirect output using '>' for a new file or '>>' to append it to the end of a file (or even make a new one like a single '>')

For example, the command 'echo "this is some text" > somefilename' makes a file that contains 'this is some text'

If we then 'echo "and some more text" >> somefilename' will make the file now contain:

```
this is some text
and some more text
```

---

### Post by gk_manutd on 2010-04-30
notify-osd is Ubuntu's notification system (That rectangular semi-transparent bubble that you get on the right-hand side top-corner of your screen at times).

What I want to do is accomplish the same thing you just explained- except I want it to be displayed on-screen as opposed to echoed on a shell or stored in a file.

---

### Post by gk_manutd on 2010-04-30
To be clear... I do not want to echo TEXT out on the screen- there are python scripts that do that.

I want to run a cron job every hour and display its output on-screen. The cron job could be anything- maybe output of **weather-util**.

---

### Post by kaibob on 2010-04-30
> **gk_manutd said:**
> I was wondering how would you go about piping the output of the shell to notify-osd? 

I know next to nothing about notify-osd but you can pipe stuff to notify-send--which I believe is the command-line equivalent of notify-osd--as demonstrated in the following command. This creates the bubble in the right-hand side top-corner of the screen.

```
echo "this is a test" | xargs -0 notify-send
```

BTW, notify-send was not installed by default in karmic. I'm not sure about lucid, but it a tiny install and is in the repositories.

---

### Post by gk_manutd on 2010-04-30
Thanks kaibob!

That did it.  :popcorn:


Thanks a lot. Appreciate it.

---

