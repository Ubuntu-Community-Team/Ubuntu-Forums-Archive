---
title: "$PATH Variable"
date: 2009-11-29
forum: General Help
---

### Post by J0hnnyBr@v0 on 2009-11-29
I want to add to my $PATH variable.  I have looked through other posts that say to use the /etc/profile for global.  I am very curious as to where my current $PATH variables are set, because I just can't find it in the usual files.

I was hoping to find something like this in one of the files :
/opt/kde3/bin:/opt/kde3/games:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

Where I could simply add on, but I can't.

Can someone please assist me with this?

Thanks in Advance

---

### Post by Leppie on 2009-11-29
I'd suggest the following to add directories to your path:
- create a file .myenv in your home directory
- open .myenv with a text editor and add the line: export PATH=$PATH:/mydir1:...:/myddirN
- save .myenv and exit the editor
- open ~/.profile *or ~/.bashrc) with a text editor
- at the end of the file add the line: source ~/.myenv
- save ~/.profile and exit the editor

run the command:
```
$telinit 2  ##process startup scripts
```

---

### Post by capscrew on 2009-11-29
> **J0hnnyBr@v0 said:**
> I want to add to my $PATH variable.  I have looked through other posts that say to use the /etc/profile for global.  I am very curious as to where my current $PATH variables are set, because I just can't find it in the usual files.

I was hoping to find something like this in one of the files :
/opt/kde3/bin:/opt/kde3/games:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

Where I could simply add on, but I can't.

Can someone please assist me with this?

Thanks in Advance

The correct place to add to your path (not the global path) is the .bashrc file.  This file is for your to personalize the bash shell.

I added this at the bottom of my .bashrc```


# Add personal bin dirrectory to path
# The global path is before the personal bin directory
# and is separated by a :
  
if [ -d ~/bin ] ; then
PATH="${PATH}":~/bin
fi

```

---

