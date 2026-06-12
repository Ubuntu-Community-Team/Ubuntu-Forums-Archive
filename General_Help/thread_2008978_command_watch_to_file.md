---
title: "command watch to file"
date: 2012-06-23
forum: General Help
---

### Post by YesGood on 2012-06-23
Hi
I intend to use the command watch for periodically run a command
I don't have problem with the output in the screen, 
but when I run thereby:
         watch -n 3 ls >> file.txt
the output is in the file.txt, but this command write me some symbols between the words

[?1049h[1;24r[m(B[4l[?7h[H[2JEvery 3,0s: ls[1;57HSat Jun 23 18:07:12 2012[3;1Harchivo [4darchivos

Why appears this symbols? 
How can I delete this symbols and get an orderly output in file?

Thanks.

---

### Post by sudodus on 2012-06-23
I think those are ANSI escape sequences to control the cursor position, colour etc according to the following link
[[COLOR="Red"]_http://en.wikipedia.org/wiki/ANSI_escape_code_[/COLOR]]("http://en.wikipedia.org/wiki/ANSI_escape_code")

---

### Post by YesGood on 2012-06-23
Thanks you for reply

But, this symbols only appear with the watch command.
if I run 
ls >> file.txt
these symbols don't appear in the file

why?

---

### Post by codemaniac on 2012-06-24
> **YesGood said:**
> Hi
I intend to use the command watch for periodically run a command
I don't have problem with the output in the screen, 
but when I run thereby:
         watch -n 3 ls >> file.txt
the output is in the file.txt, but this command write me some symbols between the words

[?1049h[1;24r[m(B[4l[?7h[H[2JEvery 3,0s: ls[1;57HSat Jun 23 18:07:12 2012[3;1Harchivo [4darchivos

Why appears this symbols? 
How can I delete this symbols and get an orderly output in file?

Thanks.

watch is an ncurses program, and is designed to be run in a console window (not redirected), which is why it's creating a bunch of unprintable characters (those are the control characters that manage and move the cursor around for redrawing the screen).

In order to have the ls snapshot every 3 sec , please consider the following .

```
#!/bin/bash

while true
do
        ls >> file.txt
        sleep 3
done
```

---

### Post by YesGood on 2012-06-24
Hi 

Thanks you!!

It work for me.

---

