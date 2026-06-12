---
title: "Copy o/p of terminal to gedit"
date: 2011-06-24
forum: General Help
---

### Post by jaypatel on 2011-06-24
[FONT=monospace]I wish to copy o/p of lsusb command to gedit.But I am getting following error>
root@jay-laptop:/home/jay/proj# lsusb -v | gedit
No protocol specified

(gedit:4310): Gtk-WARNING **: cannot open display: :0.0
root@jay-laptop:/home/jay/proj# lsusb -v | gedit hi
No protocol specified


[/FONT]

---

### Post by nothingspecial on 2011-06-24
```
lsusb -v > hi; gedit hi
```

would do that.

---

### Post by cbowman57 on 2011-06-24
I don't know if what you want to do is even possible, it might be, but why not just **lsusb -v >lsusb.txt** then open lsusb.txt with gedit?

Apparently it is possible. ;)

---

### Post by idoitprone on 2011-06-24
> **jaypatel said:**
> [FONT=monospace]I wish to copy o/p of lsusb command to gedit.But I am getting following error>
root@jay-laptop:/home/jay/proj# lsusb -v | gedit
No protocol specified

(gedit:4310): Gtk-WARNING **: cannot open display: :0.0
root@jay-laptop:/home/jay/proj# lsusb -v | gedit hi
No protocol specified


[/FONT]


guis dont behave the same way as command line programs. guis do not accept input from standard in so the program the pipe "|" will not work


i believe this is what you want

```
lsusb -v > hi

```
you want the redirect symbol ">" then it will save to a file named hi

---

### Post by nothingspecial on 2011-06-24
You are running X?

---

### Post by cbowman57 on 2011-06-24
> **nothingspecial said:**
> ```
lsusb -v > hi; gedit hi
```

would do that.

Nice, I had to try it. :)

---

### Post by idoitprone on 2011-06-24
> **nothingspecial said:**
> ```
lsusb -v > hi; gedit hi
```would do that.


i think it better if we used &&. i just do not want gedit to open an empty file

lsusb -v > hi && gedit hi

---

### Post by nothingspecial on 2011-06-24
&& tests the command before it worked.

which we know did

---

### Post by CaptainMark on 2011-06-24
and if i didnt work we would still get an open gedit screen with details of the error output

---

### Post by nothingspecial on 2011-06-24
> **nothingspecial said:**
> && tests the command before it worked.

which we know did

I don't think I put that quite right.

I mean, in cases when you know the first command will work, a  ; is fine for the next one.

&& is for when you are unsure.

---

### Post by idoitprone on 2011-06-24
> **nothingspecial said:**
> I don't think I put that quite right.

I mean, in cases when you know the first command will work, a  ; is fine for the next one.

&& is for when you are unsure.

exactly, if the op somehow mess up the command on the first time around. gedit will not open and we know it not gedit fault. the op wrote the wrong syntax for the first command.

the problem with using a semi-colon, we cannot tell if the output is actually nothing or he mess up the command. I want to get rid of all these minor annoying cases

---

