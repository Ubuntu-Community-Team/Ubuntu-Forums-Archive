---
title: "Ctrl-C doesn't work in gnome-terminal"
date: 2012-03-18
forum: General Help
---

### Post by aneganov on 2012-03-18
Hi,

I've got a computer with Linux Ubuntu 10.10 and Control-C doesn't work in gnome-terminal. How comes?

---

### Post by codemaniac on 2012-03-18
If you want to copy text in terminal , select the text and shift+Ctrl+c .
That would copy the text to clipboard .
shift+Ctrl+v would paste it .

---

### Post by aneganov on 2012-03-18
> **codemaniac said:**
> If you want to copy text in terminal , select the text and shift+Ctrl+c .
That would copy the text to clipboard .
shift+Ctrl+v would paste it .

This is about FLOW CONTROL, not playing with clipboard :)

---

### Post by winh8r on 2012-03-18
I do not know why it doesn't work, but you can try using

control + z 

which will also stop the running command and bring you to a new prompt.

---

### Post by aneganov on 2012-03-18
> **winh8r said:**
> I do not know why it doesn't work, but you can try using

control + z 

which will also stop the running command and bring you to a new prompt.

Control-z works fine btw.
But I need to stop process, not pushing it into background.

---

### Post by raja.genupula on 2012-03-18
try this 
 ctrl+alt+F1 and type as 
```
sudo apt-get install --reinstall gnome-terminal
```
then press ctrl+alt+f7 to get back to GUI  . and try again with Ctrl+C .

---

### Post by WasMeHere on 2012-03-18
> **aneganov said:**
> This is about FLOW CONTROL, not playing with clipboard :)

@winh8r: ***ctrl + z*** stops the execution and you can put the process to the background with ***bg*** or return to the foreground with ***fg***, so that is not the same thing.

I think it is important that ***ctrl + c*** works.

@aneganov:

1. Have you tried if it works in a text terminal,
for example started with ***ctrl + alt + F3*** ?
(You get back to the GUI desktop environment with ***ctrl + alt + F7***.)

2. Do you have a global shortcut tied to ***ctrl + c***, that intercepts the action of gnome-terminal?

3. Have you tried if it works in another terminal window program, for example ***xterm*** or ***tilda***?

4. Have you tried if it works in another shell (I guess you have ***bash***, so try for example ***csh***).

---

### Post by codemaniac on 2012-03-19
> **aneganov said:**
> This is about FLOW CONTROL, not playing with clipboard :)

Oh sorry for the misunderstanding , the lack of information on your post guided me the wrong way .
Anyways you can try the options as raja and Olle Wiklund have suggested .

---

