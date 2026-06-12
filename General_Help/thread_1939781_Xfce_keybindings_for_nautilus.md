---
title: "Xfce keybindings for nautilus"
date: 2012-03-12
forum: General Help
---

### Post by sirriffsalot on 2012-03-12
Hello!

I'm using Xfce and would like to make a key bind whereby the command is "sudo xfce4-taskmanager", but for some reason configuring that in the "Shortcuts" panel of the keyboard settings nothing happens? "xfce4-taskmanager" turns up, but if root commands are involved here nothing happens, any ideas? "gksu nautilus" works on the other hand... :-S

Thanks for taking time out to read this!:)

--> Leo

---

### Post by P.ap G on 2012-03-12
Wouldn't the command line be a better option ?

---

### Post by sirriffsalot on 2012-03-12
I've come that far mate:D Anyway, I have to type in what command is to be given, and so I do: "sudo xfce4-taskmanager" and all the rest that you said. But when I press the binds nothing happens...:)

---

### Post by pbrane on 2012-03-12
I was able to add 
```

gksudo xfce4-taskmanager

```
as a shortcut. I used CTRL + T as a test and it worked fine. When I press CTRL + T I get a password dialog box. After entering my password I get the taskmanager with a red warning bar that says '*Warning, you are using the root account, you may harm your system*.'.

so if you invoke xfcce4-taskmanager as root you should see that warning bar also.

---

### Post by sirriffsalot on 2012-03-12
I figured it out... For some curious reason "sudo xfce4-taskmanager" does not work, but "**gksu**"xfce4-taskmanager" does work... How can this be??

---

### Post by pbrane on 2012-03-12
sudo will run in a terminal asking for your password. gksudo runs in a window (dialog box). You will never see the terminal the way you invoked the command.

---

### Post by sirriffsalot on 2012-03-12
Not if you're using it regularly enough for it to be simpler to have a keybind for it:)

---

### Post by sirriffsalot on 2012-03-12
Jinx;D Yea, thanks, noticed that. Being very careful with what I kill et cetera!

---

