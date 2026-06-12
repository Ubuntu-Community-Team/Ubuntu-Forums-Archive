---
title: "cannot empty trash"
date: 2009-09-30
forum: General Help
---

### Post by yanvolking on 2009-09-30
Hello Community,

I made a backup of some data I had on a CD rom.  Then I decided to send it to trash.  It successfully went from the file system to the trash can.  But when I try to empty the trash can nothing happens.  The contents remains in the trash can.  If I try to highlight the file manually and right click to "delete it permanently" I get the following message:[IMG]file:///tmp/moz-screenshot-1.jpg[/IMG] "Error removing file : Permission denied"  It is interesting to note that all the archives have a padlock symbol attached.

Does anyone know how I can get rid of these files?

Thanks



[IMG]file:///tmp/moz-screenshot.jpg[/IMG]

---

### Post by credobyte on 2009-09-30
```
sudo rm -r ~/.local/share/Trash/*

```

---

### Post by yanvolking on 2009-09-30
Thanks, Credobyte.

I executed your command line in the terminal.  I had 3 identical archives in the trashcan.  The command execution removed one of the archives.  2 remained.  but when I execute the command line again I get the following:

yan@yan-laptop:~$ sudo rm -r ~/.local/share/Trash/*
rm: cannot remove `/home/yan/.local/share/Trash/*': No such file or directory
yan@yan-laptop:~$ 

Any idea why the above commande only removes one of three identical archives?  What's to be done?

Thanks inadvance

Yan

---

### Post by dE_logics on 2009-09-30
Goto the place where you mounted the partition on which you copied the file.

Then in view...select show hidden files.

There should be a folder name like...trash-1000

Open that...then open commandline and cd to the this trash-1000 folder - 

```

cd <trash-1000 folder's path>

```

then - 
```
sudo rm -R *
```

Now ENSURE that you're in the trash-1000 folder when you implement this command...otherwise you're doomed.

---

### Post by yanvolking on 2009-09-30
OK, I've found the place where i copied the files to.  It was on a USB stick.  When I do "view" then "show hidden files", there suddenly appears a file called ".trash-1000".  So I opened a terminal and typed :

yan@yan-laptop:~$ cd <trash-1000 folder's path>

and all that happens is that there appears :

> 

Nothing more.  I must admit I am scared of being doomed, as you warn me.  I suppose I have to substitute something like "16.2GBmedia/.trash-1000" or something similar for "foldre's path". is that right?
(what would the path to a file in a USB pen drive look like?)

I think we're half way there.
Thanks

---

### Post by yanvolking on 2009-09-30
Hi community,

Thanks for your help.  What I was not sure about I toyed with.  To establish the exact file path of the ".trash-1000" directory I right clicked it and pressed "properties".  Then :

yan@yan-laptop:~$ cd /media/disk/.trash-1000
[email]yan@yan-laptop:/media/disk/.trash[/email]-1000$ 
[email]yan@yan-laptop:/media/disk/.trash[/email]-1000$ sudo rm -R *
[sudo] password for yan: 



[email]yan@yan-laptop:/media/disk/.trash[/email]-1000$ 

Now "/media/disk/.trash-1000" is empty and so is my tarsh can.

Problem Solved and I'm much wiser...........

Thanks

---

