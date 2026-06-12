---
title: "[SOLVED] how to set alias permanently?"
date: 2006-06-29
forum: General Help
---

### Post by Warlord88 on 2006-06-29
I have Ubuntu 6.06 installed and I use the default Gnome terminal. I set aliases using the following command (for example):
alias home="cd /home/saurabh"  
But the alias is cleared when I close the terminal. How do I set the alias permanently for all users so that is works every time I open the terminal?

---

### Post by ikarus9999 on 2006-06-29
You can put your aliases either into the /etc/bash.bashrc (global settings) or into the .bash_aliases in your home directory.

---

### Post by Warlord88 on 2006-06-29
Ok. I put the alias into .bashrc in my home directory and it worked. But there is no file named .bash_aliases in my home directory.

---

### Post by cajunlibra on 2006-10-27
Do the alias commands just get typed in anywhere in the file?

---

### Post by bsussman on 2006-10-27
> **cajunlibra said:**
> Do the alias commands just get typed in anywhere in the file?

simple aliases should be ok anywhere but it is a good habit to add them at the end, commented so that you do not need to remember what you did when you look at it again :)

---

### Post by geneticmaterial on 2006-10-28
you would need to create the "~/.bash_aliases" file and uncomment the three following lines in the "~/.bashrc" file. 

# if [ -f ~/.bash_aliases ]; then
#     . ~/.bash_aliases
# fi

and just input your aliases into the "~/.bash_aliases" file and save. a tip i use is to make a alias likes so > edit_aliases='vim ~/.bash_aliases'

this way anytime i want to create one i just type in that command

---

