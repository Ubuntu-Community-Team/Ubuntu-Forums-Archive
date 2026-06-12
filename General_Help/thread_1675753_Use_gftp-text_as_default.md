---
title: "Use gftp-text as default"
date: 2011-01-26
forum: General Help
---

### Post by uint32 on 2011-01-26
Hi everyone,

This maybe a simple noob question but it's niggling at me and I can't find an answer.  For a change I thought I would pop on the forums and ask a question rather than just lurking about!


I'm currently using gftp-text from the terminal to access my ftp but I'm wondering if I can change the command so I can type just "ftp" or "gftp" to use it rather than "gftp-text"?  


It's really not that hard to type either way and it's no biggie but I'm annoyed I can't figure it out how to do this for myself!  Any pointers or hints would be appreciated.

Thanks.

---

### Post by ajgreeny on 2011-01-26
You can add an alias to the .**bashrc** file in your home.

Hit Ctrl+H if you can not see hidden files and folders then search for that file, which is a plain text file.  Open it in gedit amd look for the lines:-
```
# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'
```
You can un-comment the last three lines to enable them if you want, and then add another line below
```
alias ftp='gftp-text'
```save the file and that's it.  Now when you type ftp as a command the terminal will read it as gftp-text instead.

I use a lot of aliases in my system just to make life quicker and easier for me, and as you will see in the .bashrc file, you can add them to a file called **.bash_aliases** if you prefer to keep things more orderly.

---

### Post by uint32 on 2011-01-26
Legend!

Thanks for that ... it's appreciated.

---

