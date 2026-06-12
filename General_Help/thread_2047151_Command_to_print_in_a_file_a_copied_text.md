---
title: "Command to print in a file a copied text"
date: 2012-08-24
forum: General Help
---

### Post by degenerate32 on 2012-08-24
Is there any command that prints a copied text into a specific file? Alternatively, in which file is a copied text saved by default? Thanks for your time !

---

### Post by Habitual on 2012-08-24
cat file >new_file

---

### Post by dozdozez on 2012-08-24
Or maybe...

echo text > New_file

---

### Post by degenerate32 on 2012-08-24
This would be useful If I'd like to print into a file a specific text that I have already written in the command line. My intention is to print what is copied to the "clipboard". e.g.: [ctr+c] "text..bla,bla,bla" from anywhere [file, internet page] and then go to the terminal and put [wanted command] that will print the copied text. Thanks again for your patience!

---

### Post by steeldriver on 2012-08-24
you can try xsel - it's not installed by default afaik so you will need to apt-get it or find it in the software center / package manager

[http://askubuntu.com/questions/11925/a-command-line-clipboard-copy-and-paste-utility](http://askubuntu.com/questions/11925/a-command-line-clipboard-copy-and-paste-utility)

---

### Post by Vaphell on 2012-08-24
not that i understand exactly what you need but i think you need to know there are 2 ways of copying
1. ctrl+c/ctrl+v in gui world, ctrl+shift+c/ctrl+shift+v in terminal (ctrl+c, ctrl+v do other things already)
2. highlight desired text, middle-click in target position to paste

as for playing with clipboard contents - there is **xsel** command which allows you to operate on 3 buffers (primary, secondary, clipboard)
highlighting/middleclicking uses primary buffer
```
echo "some string" | xsel -**p**i   # puts the desired string in the buffer
xsel -**p**o   # prints out the current content
```

ctrl(+shift)+c/ctrl(+shift)+v on the other hand use clipboard
```
echo "some string" | xsel -**b**i
xsel -**b**o
```

secondary buffer functions can be accessed in a similar way by using **s**

---

### Post by dozdozez on 2012-08-24
Why don't use a text editor?

anyway, you can install a program called xclip and then:

```
xclip -o > file
```

for more options man xclip, you know....

---

### Post by degenerate32 on 2012-08-24
Thank you so much Vaphell & steeldriver! I got the xsel package installed and then "xsel -po" did exactly what I was looking for. I'm so grateful guys

---

