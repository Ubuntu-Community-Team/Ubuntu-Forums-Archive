---
title: "How to change the PATH variable"
date: 2012-02-07
forum: General Help
---

### Post by kranthi457 on 2012-02-07
HI All ,
 
I want to change the PATH variable globally. So that i can run exe files i create(under /home/kranthi/bin) . I am able to change the local path variable using the export command but the changes dont take effect if i open a new shell.
 
Also there are 3 files where people say we can change global setting namely 
bash.bashrc
profile
environment
 
all located under /etc directory. I am not where to change an how to change please advice.
 
Thanks
Kranthi

---

### Post by HiImTye on 2012-02-07
you can add it to your .bashrc in your home folder, simply add a new line and then add
```
PATH="whatever you want your path to be"
```ditto for any other variables you want to change

edit: you might want to include your current PATH in your new one. to find out what it is, in a terminal, use:
```
echo $PATH
```

---

### Post by kranthi457 on 2012-02-07
HI 
 
I am new to linux i am really not sure how to append thi .bashrc file ,could you please explain me how to do so ???
 
Thanks

---

### Post by HiImTye on 2012-02-07
go to any line (for your sanity, you might want to choose an empty one if you plan on making other changes later, but you don't have to)
hit <enter>
this will make a new line
go to the line in the middle so that it is all by itself
add to this new line:
```
PATH="the path that you want"
```for instance, if I were to add it to the top of my .bashrc, using the path that is already set for Ubuntu by default (echo $PATH) then the top of my file would look like this:
```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

PATH="/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

# If not running interactively, don't do anything
[ -z "$PS1" ] && return
```and then it continues on

---

### Post by kranthi457 on 2012-02-07
Thank you so much i am able to fix the issue .:)

---

