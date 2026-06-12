---
title: "how to be a root in ubuntu?"
date: 2010-08-17
forum: General Help
---

### Post by enhu on 2010-08-17
need to edit text file in a folder. how to use sudo?

---

### Post by Naitsirhc Hsem on 2010-08-17
cd to the directory, eg
```
cd Documents
```
and ```
sudo gedit file.txt
```
gedit is the text editor
file.txt is the example file you want to edit

---

### Post by GlazedDonut on 2010-08-17
Enter```
sudo gedit <textfile>
``` in a terminal, substituting <textfile> with the actual textfile.

---

### Post by dcollier on 2010-08-17
ok if you are trying to edit a text file using root priv. here is an example of a file name file in your current directory.

sudo vim file

I use vim to edit file, you can use any editing program of your choice.

---

### Post by TheWeakSleep on 2010-08-17
From the terminal, cd into the folder where your document is, for example,

```
cd ~/Desktop/Documents/This/Is/Where/It/Is
```then type
```
gksudo gedit nameofdocument.txt
```where nameofdocument.txt is replaced by the name of your document

EDIT: AHH beat me to it :p

---

### Post by enhu on 2010-08-17
thanks. so i need no password to be a root?
how can i configure for it to need a password?

---

### Post by enhu on 2010-08-17
i tried getting into the grub and i can't seem to see the menu.lst :D

where can i find it?

---

### Post by oldos2er on 2010-08-17
Which version of Ubuntu are you using? If it's 9.10 or later, and you didn't upgrade from an older version, you're using grub2 which doesn't use /boot/grub/menu.lst. See [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

Ubuntu locks the root user be default, and instead uses sudo. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by JKyleOKC on 2010-08-17
> **enhu said:**
> thanks. so i need no password to be a root?
how can i configure for it to need a password?
It will ask you for your own login password, but won't echo anything to the screen as you type it.

Be very careful about using "sudo" with graphical editors such as gedit or mousepad. Best use "gksudo" or "gksu" instead. The reason is that using "sudo" does slightly different things with permissions, and can leave you with confusing symptoms and undesired results. The two "gk" variants deal properly with the graphical interface behind the scenes. All three take your login password.

---

