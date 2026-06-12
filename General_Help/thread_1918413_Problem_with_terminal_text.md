---
title: "Problem with terminal text"
date: 2012-01-31
forum: General Help
---

### Post by Kobbs on 2012-01-31
I am having a problem with my terminal text after I run a C++ program. This is the program...


[IMG]http://s16.postimage.org/5j3gk7fol/C_gedit.png[/IMG]


And what I get in the terminal looks like this

[IMG]http://postimage.org/image/8mwo11nzz/[/IMG][IMG]http://postimage.org/image/8mwo11nzz/[/IMG]
[IMG]http://s11.postimage.org/u9boi2mkj/Screenshot_Terminal.png[/IMG]


Any ideas on why this is happening?


[IMG]http://ubuntuforums.org/home/nechayev/Desktop/Sceenshot-Terminal.png[/IMG]

---

### Post by sudodus on 2012-01-31
You have sent a character (or sequence of characters) to the standard output, the sets your terminal to interpret characters like that. Either reset it or close it and start another fresh terminal.

Often I can use the following alias to reset my terminal:

```
alias reset='/bin/echo -e "\0033[0m"'
```I have that line in my [FONT=Courier New][SIZE=3]~/.bashrc[/SIZE][/FONT] file, and I type ***reset*** to run it, which is simple even when the output is garbled.

---

