---
title: "&quot;ls&quot; showing deleted files"
date: 2011-12-07
forum: General Help
---

### Post by achuth on 2011-12-07
Sir, 
I have cut n pasted files from Desktop to another location. But when I type ls command at the Desktop, those files are shown but with added tilde (~) symbol at the end as :
a12iuy~
a12ppu~
boom
boom~
brij~
delfile~
file1
file1~
file1.c~
file2~

Why is this?
Even before moving those files, I was seeing filenames that ends with tilde when I used the "ls" command.
What are those files ending in "~" ?

---

### Post by haqking on 2011-12-07
They are backup files.

If you are sure you dont want them then you can remove them

---

### Post by Lars Noodén on 2011-12-07
Emacs and some other programs make a backup copy of the file you are changing.  The filename for the backup is the name of the edited file but with a tilde (~) appended to it.  Some call these 'turd files'.  

Check the content, you will see they are an earlier version of the file.  If you have not gotten rid of the original file, then these backups can be safely deleted.  They are there in case you  need to revert to the previous version.

---

### Post by mikejonesey on 2011-12-07
you must have some backup software running, many backup utils add a tildus followed by an incramental number whilst generating a backup... however ls is not defective it is showing current files, and this is not the default behaviour in any gui file manager i have ever used...

do you know what file manager you are using? and what plugins are avctive on that file manager?

---

### Post by haqking on 2011-12-07
> **mikejonesey said:**
> you must have some backup software running, many backup utils add a tildus followed by an incramental number whilst generating a backup... however ls is not defective it is showing current files, and this is not the default behaviour in any gui file manager i have ever used...

do you know what file manager you are using? and what plugins are avctive on that file manager?

you dont have to have backup software running.

individual applications often make backups of files such as text editors

and i think you meant tilde, tildus was in Xena princess warrior ;-)

---

### Post by mikejonesey on 2011-12-07
yes i forgot as lars nooden pointed out, editors also create a backup too, which is usualy deleted on close... (including vim)

---

### Post by achuth on 2011-12-07
Sir,
How can I remove those backup/temporary files?
or How can I stop the creation of backup files?

---

### Post by Mr. Shannon on 2011-12-07
To stop the backups you need to know what software created the backups.  In other words, what software did you edit the files with?

**Edit:** You can remove the files (until they are created again) with the rm command or by enabling hidden files in your file browser (so you can see the files) and then delete them like any other file.

Another solution is to use the exec option of find to delete all backups in you home folder but this could possibly remove files that you don't want removed.

---

### Post by hwttdz on 2011-12-07
Somewhat related, I didn't like seeing them all the time.  But I like keeping them around, so I have bash pretend like they're not there:
[http://ubuntuforums.org/showthread.php?t=1842874](http://ubuntuforums.org/showthread.php?t=1842874)
Keeps them out of the way, and if I realize I made a mistake I can go back.  But to each their own.

---

### Post by Lars Noodén on 2011-12-07
You could hide them by making an alias for [ls](http://manpages.ubuntu.com/manpages/precise/en/man1/ls.1posix.html) and putting it into [font=Courier New].bashrc[/font]

```

alias ls="ls --ignore-backups $@"

```

---

