---
title: "mysql package question"
date: 2009-07-20
forum: General Help
---

### Post by chuckh1958 on 2009-07-20
Why does ubuntu use a non-gpl'ed version of mysql?

mysql --help | head -n 1

mysql  Ver 14.14 Distrib 5.1.31, for debian-linux-gnu (i486) using  **[COLOR="Red"]EditLine[/COLOR]** wrapper

The EditLine version (as opposed to the readline version) indicates non-gpl. It's causing me problems as I can't seem to get the keybindings right. For example the delete key does not behave correctly and I can't find any docs on how to change it.

---

### Post by wojox on 2009-07-20
What are you trying to delete?
If it is from the command line you have to use the backspace button.

---

### Post by chuckh1958 on 2009-07-20
> **wojox said:**
> What are you trying to delete?
If it is from the command line you have to use the backspace button.


I'm trying to delete characters using the delete key.

On gpl'ed versions of the mlsql cli I don't have to use the backspace key. I can use delete if I want too. Not so with the non-gpl'ed version in the ubuntu repository. I'm just trying to figure out (a) why ubuntu would feel the need to use a non-gpl version, and (b) how to make it work like it does on every other machine that I use. It's really annoying.

---

### Post by chuckh1958 on 2009-07-20
I was able to achieve the desired behaviour with the delete key by creating a  and .editrc file in my $HOME direcotry with the following line in it.

bind "\e[3~" ed-delete-next-char

HTH anyone else running into the same problem.

I'm still at a total loss though as to why Unbuntu would feel the need to distribute a non-gpl'ed (read commercial) version of the mysql client.

---

