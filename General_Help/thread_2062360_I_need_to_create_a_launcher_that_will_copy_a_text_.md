---
title: "I need to create a launcher that will copy a text to the clipboar"
date: 2012-09-24
forum: General Help
---

### Post by adhamj90 on 2012-09-24
hello, 
i've been looking around on how to copy a text to the clipboard from the terminal.
i found many solutions using the xclip and xsell.

for example if i use any of the following it will always copy "string" to the clipboard.

echo string| xclip -i -selection clipboard
echo string | xsel -i -b
echo "string" | xsel -b

the problem is when i want to add it to a launcher to the panel..
im using ubuntu 10.10, i create a new launcher and i put one of the line above as the command. but it just doesn't work!

can someone please tell me what am i doing wrong.

i tried doing the same thing before. 
i created a launcher to put the volume to the max ( 150% )
all i did was create a launcher and put this line as the command:

pacmd set-sink-volume 0 100000

and it works just fine. 


i hope i was clear enough. 
I really appreciate your help. thanks in advance.

---

### Post by LewisTM on 2012-09-24
You can't use shell operators like the pipe | in a launcher without some extra care.
This command should work:
```
bash -c "echo string | xsel -i -b"
```
Cheers!

---

### Post by adhamj90 on 2012-09-25
thanks a lot for the answer..
it works just fine now ! :)

---

### Post by adhamj90 on 2012-09-25
only problem about the solutions. almost all of them, is that when you past the string from the clipboard it will paste it with a space (or a new line) in front of it. i couldn't find any code that would copy the string without the space.

---

### Post by Vaphell on 2012-09-25
echo by default adds newline at the end, use echo -n or printf

---

### Post by adhamj90 on 2012-09-25
i've  already used 

echo -n string | xclip -i -selection clipboard .

and it worked fine without the space.

problem solved :D

---

### Post by HiImTye on 2012-09-25
are you trying to copy a specific string to the clipboard or just whatever text you have selected? if it's the latter, you can always just middle click to paste whatever selection you have, rather than copying it to the clipboard and pasting it

---

