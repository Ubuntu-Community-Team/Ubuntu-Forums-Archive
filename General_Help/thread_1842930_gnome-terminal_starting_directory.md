---
title: "gnome-terminal starting directory"
date: 2011-09-12
forum: General Help
---

### Post by hwttdz on 2011-09-12
update: mount --bind works better than symlinks in home directory path.  Some programs (ubuntuone) do not play well with symlinks.

Ok, so I've an admittedly weird setup.  In order to mirror my cluster account so I don't need quite as much "where am I running" testing in my scripts, I don't have my home directory living in /home/username

instead it lives in something more like

/home/users/u/username

but that path is actually a symbolic link back to /home/username.  It's almost like having a home both places.  Anyways, very few things get confused, mainly because either works, but gnome-terminal (my most used program) is one of those few.  When I open it up I'm in /home/username, but because of the way tilde substitution works it actually displays that.  I'd rather it open to /home/users/u/username (which is actually the same place so I get) "username @ hostname ~ > " as my prompt instead of "username @ hostname /home/username >".  Thoughts?  How does gnome-terminal decide where to open a new terminal?

---

### Post by nitstorm on 2011-09-12
Try this please,

1. Open the terminal, go to Edit->Profiles.

2. Create a new profile and edit it, in the Title & Commands tab, choose - Run a custom command instead of my shell.

3. There type, 
```
gnome-terminal --working-directory=/home/username/ 
```

Else,

Modify the keyboard shortcut for your terminal (Ctrl+T) to execute ```
gnome-terminal --working-directory=/home/username
```

---

### Post by hwttdz on 2011-09-12
Do not put a "gnome-terminal" command in your "custom command instead of shell".  It's no good at all.  Infinite loop of gnome-terminals.  

Also, if I were to do something like that I would loose the handy feature of staying in the same directory when opening up a new tab.

Here's a "bad" solution: [http://superuser.com/questions/182960/gnome-terminal-how-to-preserve-symlinks-of-working-directory-when-opening-new-ta](http://superuser.com/questions/182960/gnome-terminal-how-to-preserve-symlinks-of-working-directory-when-opening-new-ta)

---

### Post by nitstorm on 2011-09-12
There is another alternative suggested here - [http://stackoverflow.com/questions/844677/gnome-terminal-how-to-start-in-a-different-directory/844711#844711]("http://stackoverflow.com/questions/844677/gnome-terminal-how-to-start-in-a-different-directory/844711#844711")

It suggests, you add ```
cd /home/username
``` to your *.bashrc* file..

---

### Post by raja.genupula on 2011-09-12
[http://www.linuxquestions.org/questions/linux-software-2/change-default-bash-directory-in-gnome-terminal-288622/](http://www.linuxquestions.org/questions/linux-software-2/change-default-bash-directory-in-gnome-terminal-288622/)


hope this gonna solve

---

### Post by hwttdz on 2011-09-12
I have added the following to my .bashrc, which gets me 
1) terminals open where they should
2) it uses the right symlink path

```

PWD="`pwd|perl -pe 's/\/home\/username/\/home\/users\/u\/username/g'`"
cd $PWD

```

Win.

Of course some users want it to know if the terminal was opened from 
/home/username 
and if so not do this replacement, but do it if it was opened from
/home/users/u/username.  
I don't know how to do this.

---

