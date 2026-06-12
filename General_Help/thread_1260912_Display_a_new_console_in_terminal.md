---
title: "Display a new console in terminal"
date: 2009-09-08
forum: General Help
---

### Post by ricky845 on 2009-09-08
I'm working with terminal in UBUNTU with some client server applications and i have to open too many consoles. So my questio is , how can i get a new console of terminal without loosing the route and the variable systems? is there any command to get it?

sorry about my english!:guitar:

thxs

---

### Post by nothingspecial on 2009-09-08
dvtm lets you split the screen into as many as you want.

screen will let you run multiple sessions in the same terminal, detach and reatach them and much much more.

```
sudo apt-get install dvtm screen
```

```
dvtm
```

Press Ctrl+G, C 3 times then press Gtrl+G,G to give you a nice grid layout.

Navigate the different windows using Ctrl+G, K and Ctrl+G, J

launch ```
screen
``` in one window then in 2 others 
```

[CODE]man screen
```
man dvtm[/CODE]

Now you`ve got four windows with the instructions to your 2 new programs in two of them and 2 more for other things.

Cool hey.

---

### Post by ricky845 on 2009-09-08
Sorry, but i don't undertand this:

Press Ctrl+G, C 3 times then press Gtrl+G,G to give you a nice grid layout.

Navigate the different windows using Ctrl+G, K and Ctrl+G, J

i have installed but i don't know how i can change between the windows..

---

### Post by nothingspecial on 2009-09-08
You launch dvtm

```
dvtm
```

Pressing Ctrl and G at the same time is the dvtm escape.
This means the shell now knows the next key you type will be an instruction to dvtm. 

After pressing Ctrl+G there are a number of instructions you can send to dvtm

C will open a new window
J will switch you one way
K will switch you the other

Type man dvtm in one of the windows to see the full instructions.

---

### Post by ricky845 on 2009-09-08
Thanks!!

---

