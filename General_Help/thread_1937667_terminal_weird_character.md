---
title: "terminal weird character"
date: 2012-03-08
forum: General Help
---

### Post by vivi168 on 2012-03-08
hi,
since yesterday my terminal has been outputting a weird character. 

for example, sometimes when i create a file and then cat it, at the end appears a "%". (the "%" doesn't appear in any text editor)

i also made a simple c program that print hello, and it also prints a "%" at then end.

(it's not only related to X, i tested in tty1)

picture : 

[IMG]http://i.imgur.com/DFWrU.jpg[/IMG]

thanks in advance for your answers.

---

### Post by TeoBigusGeekus on 2012-03-08
A mistype in your .bashrc maybe?

---

### Post by vivi168 on 2012-03-08
i use zsh. and thanks to your allusion to bash, i think i figured out what the problem is.

it seems it's a zsh substitution. when i use bash and cat/execute the same file/program, there is no new line. maybe the "%" is a new line character substitute.

[IMG]http://i.imgur.com/QlU5r.jpg[/IMG]

---

