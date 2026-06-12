---
title: "Can I make Terminal default to /Desktop instead of ~?"
date: 2012-05-10
forum: General Help
---

### Post by nrundy on 2012-05-10
When I open Terminal it always defaults to ~ location. Can I make it default to ~/Desktop instead? 

anybody know how to do this?

---

### Post by oldos2er on 2012-05-10
Open your .bashrc file in your favorite text editor, and add ```
cd /home/user/Desktop
``` at the bottom of the file. You'll need to close any open terminals and restart one for the change to take effect.

---

### Post by flemur13013 on 2012-05-10
$ gnome-terminal --working-directory=/whatever

Assign an alias or link to it so you'll retain the regular gnome-terminal.

---

### Post by nrundy on 2012-05-10
> **oldos2er said:**
> Open your .bashrc file in your favorite text editor, and add ```
cd /home/user/Desktop
``` at the bottom of the file. You'll need to close any open terminals and restart one for the change to take effect.

a search found 4 .bashrc files. which one am I supposed to edit?

bash.bashrc (1.9 kb)
bash.bashrc (870 bytes)
dot.bashrc (3.0 kb)
dot.bashrc (1.8 kb)

---

### Post by PaulW2U on 2012-05-10
> **nrundy said:**
> a search found 4 .bashrc files. which one am I supposed to edit?


The one in your home directory which is called **.bashrc**.

---

### Post by davetv on 2012-05-10
it should be ".bashrc" in home directory. It has been like that for years. Pls advise if Ubuntu does this differently.

If it is different now ... my Ubuntu experience is over! It has been getting strange at lower levels for a while.

(seen above post - feel happier now)

---

### Post by nrundy on 2012-05-10
I am using 10.04. and I found the .bashrc in my home folder.

Thanks everyone!

---

### Post by codemaniac on 2012-05-10
try the path  ~/.bashrc 
```
ls -l ~/.bashrc 
```

<edit>Apologies for my redundant post</edit>

---

### Post by nrundy on 2012-05-10
> **codemaniac said:**
> try the path  ~/.bashrc 
```
ls -l ~/.bashrc 
```<edit>Apologies for my redundant post</edit>

no problem. this was good idea. I'm still new with terminal.

---

### Post by wojox on 2012-05-10
You can also do it without opening the file:
```
echo "cd $HOME/Desktop" >> ~/.bashrc
```

Source for good measure:
```
source .bashrc
```

---

