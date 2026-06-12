---
title: "Saving files ???"
date: 2009-10-25
forum: General Help
---

### Post by Gordonisnz on 2009-10-25
Hello.

I'm using  gedit to save files in a directory outside my home directory..

(I'm trying to learn packages...)

anyway, when I use the ls command, I get 2 files with the sdame name, 1 as it should be "control" and another file with "control~"

The dpkg --build  command fails, as it cannot find the file 'control'

QUERY :-

What is ~ ??  Does it  mean I've tried to edit it but not saved it yet ? (None of my edit screens are open) - gedit


> 
 ls
control  control~  mycool  preinst~


---

### Post by vinutux on 2009-10-25
That is probably a backup file..... :) CTRL + H in nautilus (/home/[COLOR="Red"]yourdesignation[/COLOR]) to see hidden files

---

### Post by Gordonisnz on 2009-10-25
AH - thanks...

Learning all the time :)  - i'm getting to like linux more & more...


THOUGH - It doesn't solve my package problem (control file not found)...

i'll start a new thread....

---

### Post by vinutux on 2009-10-25
mm.... what package you want to compile ?

---

### Post by Gordonisnz on 2009-10-25
No file in particular...

its a test file I'm trying to learn... (started a  new thread)

[http://ubuntuforums.org/showthread.php?t=1300645](http://ubuntuforums.org/showthread.php?t=1300645)


The error isn't (invalid command in control file) or whatever, the error is, that the control file cannot be found.. 

1 step at a time :)

I'll reply on the other thread (if any)


Basically, once i learn HOW to create a valid package, i'll start packaging something useful
(PHP files I create - For a website...)

---

### Post by Gordonisnz on 2009-10-25
Currently, I create the PHP code & have to wait until someone else packages it on the website server...


I want to learn to package things myself - be more active

---

