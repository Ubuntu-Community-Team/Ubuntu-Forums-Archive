---
title: "installing hexchat"
date: 2012-07-30
forum: General Help
---

### Post by antobbo on 2012-07-30
Hi can somebody give me a hand/point me to the right direction please? I am attempting to install hexchat but I don't know how to do it, the commands on the terminal etc etc. Any idea please?
thanks

---

### Post by Rodney9 on 2012-07-30
How to Build HexChat on Ubuntu

[https://gist.github.com/3194136](https://gist.github.com/3194136)

---

### Post by antobbo on 2012-07-31
thanks. All done I built it and used it fine, but now I have a question. After using it yesterday I switched my laptop off. Today I switched it on again, and how do I launch the application again? I mean it is already built but where do I get the executable from?
I tried ```
./src/fe-gtk/hexchat
``` but no joy. Same with just ```
hexchat
``` or do I have to be in a specific directory to execute those commands?
thanks

---

### Post by dodo3773 on 2012-07-31
If you did a make install it should have been installed somewhere in your shells $PATH. If you type "whereis hexchat" does it return anything?

---

### Post by antobbo on 2012-08-19
yes it returns this:

```
antobbo@antobbo-xps17-ubuntu:~/Desktop$ whereis hexchat
hexchat:
antobbo@antobbo-xps17-ubuntu:~/Desktop$ 

```

but hexcchat I know sits under Desktop/hexchat
I don't seem to be able to start it again...

---

### Post by dodo3773 on 2012-08-20
You know it's on the desktop? How do you know that? Is there a shortcut or a binary there or something?

---

### Post by antobbo on 2012-08-20
I managed to open it from the folder, but I can't from the terminal

---

### Post by dodo3773 on 2012-08-20
> **antobbo said:**
> I managed to open it from the folder, but I can't from the terminal

Okay, so navigate to where the file is in the terminal and see what kind of file it is. Is it a binary or a .desktop shortcut or something?

---

